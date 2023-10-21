# Zipkin
distributed tracing system 분산 추적 시스템

## 서비스 이름
어떤 서비스가 트레이싱 정보를 보냈는지 구분
일반적으로 해당 앱의 이름으로 설정한다.

## 스팬 이름
서비스 내의 다양한 작업이나 요청 유형을 구분

# Zipkin과 함께한 추억

으엑거어ㅓ아아ㅏ

이것도 다 경험이지.. 그렇지….

← 왜이럼? : zipkin 굳이 안써도 datadog apm으로 zipkin이 하는 일 할 수 있음. 이 사실을 apply 하기 전에 알게됨 ㅎㅎ

아마 머지되지 못하겠지만 브랜치로 일단 남겨두고 datadog로 설정할 때 비슷하게 설정할 수 있도록 하겠음

`feat/TWM-836/zipkin-적용`

# 추억용 스샷 (Local)

![](https://i.imgur.com/g55trBV.png)
![](https://i.imgur.com/JT5fbXi.png)
![](https://i.imgur.com/PCfWYe7.png)
![](https://i.imgur.com/JhamuM8.png)

이거 보면 이제 처음에 백엔드로 들어와서 fa-server로 이어졌다는 것을 알 수 있다..

일단 기본적으로 연결되는 것만 보고 나중에 더 봐야지 하고 생각함 ← 지금보니 그나마 다행이누

# ZipKin

distributed tracing system 분산 추적 시스템

MSA에서 트랜잭션 별로 어떤 서비스를 오갔는지 찍어준다

지연시간이 얼마나 되었었는지 보기 좋았다.

몇가지 간단한 개념이 있다.

- b3-propagation : 헤더에 들어가는 것. 이것으로 같은 trace인지 몇번째 span인지를 구분한다.
    - 헤더에 `X-B3-{name}` 의 이름으로 서비스간의 통신에서 값을 전달한다.
    - name에는 `TraceId`, `ParentSpanId`, `SpanId`, `Sampled`(?이건 아직 모름)가 있다.
- service name : 말그대로 해당 시점에 있는 서비스의 이름이다.
- trace id : 최초 클라이언트가 보낸 HTTP 요청의 흐름
- span : 서비스 내의 다양한 작업이나 요청 유형을 구분한다. 나 같은 경우 엔드포인트 기준으로 나눠두었다.
    - span id, span name 이 있다.

최초로 들어온 요청(다른 서비스로부터 온 요청이 아님)인 경우 trace id와 span id를 새로 생성하는 것이다.

## TWM-Backend 설정

### 기본 설정

```
// Zipkin
implementation 'io.zipkin.reporter2:zipkin-sender-urlconnection'
implementation 'io.micrometer:micrometer-tracing-bridge-brave'
implementation 'io.zipkin.reporter2:zipkin-reporter-brave'
```

```yaml
spring:
  application:
    name: twm-backend

...

# Actuator 설정
management:
...
  tracing:
    sampling:
      probability: 1.0 # 추적 샘플링 비율, 범위 [0,1]
    propagation: # 추적 정보 형식 정의
      consume: B3_MULTI # 들어오는 요청
      produce: B3_MULTI # 나가는 요청
  logging:
    pattern:
      level: "%5p [%X{traceId:-},%X{spanId:-}]"
...
```

`B3_MULTI`는 여러가지 별도 헤더(`X-B3-TraceId`, `X-B3-SpanId`, `X-B3-ParentSpanId`, `X-B3-Sampled` ) 로 받거나 보내겠다는 것

zipkin의 endpoint는 dev, prod 분리하여 설정하였다.

```yaml
...
management:
  zipkin:
    tracing:
      endpoint: "<http://localhost:9411/api/v2/spans>"
...
```

```yaml
...
management:
  zipkin:
    tracing:
			endpoint: "<http://zipkin-service:9411/api/v2/spans>"
...
```

### WebSocket에서 설정

그냥 위처럼 하고 zipkin 서버를 9411포트로 실행시키면 http 요청은 바로 찍히는게 볼 수 있다.

그런데 webclient를 사용하는 경우 조금 더 설정해줘야 한다.

아래와 같이 요청 보낼 때 헤더 설정해주고 span의 시작과 끝을 설정해준다.

```java
...
public class SendResponseFAMessageService implements SendResponseFAMessageUseCase {
	...
	// zipkin의 brave 라이브러리
	private final Tracer tracer; 
	...
	public void sendResponseFAMessage(SendMessageReq faRequestMessage, String eventName, Long faTypeId) {
		...
		// 새로운 span을 생성 및 시작. span name은 기존에 찍히는 http 형식과 맞춤
		Span span = tracer.nextSpan().name("ws "+renderType+" "+url).start();
		// span 범위 설정 : fa 요청 보내고 받는 거까지로 설정하겠다는 거임
		try (Tracer.SpanInScope ws = tracer.withSpanInScope(span)) {
			Mono<FaResponse> faResponseMono = webClient.get()
				.uri(url)
				// fa-server에서 읽을 수 있도록 헤더 설정!
				.header("X-B3-TraceId", span.context().traceIdString()) 
				.header("X-B3-SpanId", span.context().spanIdString())
				...
			;
			...
			faResponseMono.subscribe(faResponseContent -> {
				...
			});
		} finally {
			// span 끝
			span.finish();
		}
```

## TWM-FA-SERVER 설정

zipkin_set.py를 새로 만들었음

```python
import random
import requests
from requests.exceptions import Timeout
from py_zipkin.zipkin import zipkin_span, ZipkinAttrs

# zipkin 서버로 요청 (여기는 아직 dev랑 prod 분리 안함)
def http_transporter(encoded_span):
    headers = {"Content-Type": "application/x-thrift"}
    try:
        requests.post(
            "<http://localhost:9411/api/v2/spans>",
            data=encoded_span,
            headers=headers,
            timeout=5,
        )
    except Timeout:
        print("The request timed out")

# zipkin에서는 trace_id와 span_id를 64bit hex string으로 표현
def generate_random_64bit_string():
    return f"{random.getrandbits(64):016x}"

def setup_zipking_middleware(app):
    @app.middleware("http")
    async def middleware(request, call_next):
        headers = request.headers
        trace_id = headers.get("X-B3-TraceId")
        span_id = headers.get("X-B3-SpanId")

        # 만약 해당 시점이 최초 호출이라면, trace_id와 span_id를 생성
        if not trace_id or not span_id:
            trace_id = generate_random_64bit_string()
            span_id = generate_random_64bit_string()

				# 일단 기본 세팅대로 
        zipkin_attrs = ZipkinAttrs(
            trace_id=trace_id,
            span_id=span_id,
            parent_span_id=None,
            flags="0",
            is_sampled=True,
        )

				# span 설정과 함께 여기서 요청을 보내는 것
        with zipkin_span(
            service_name="twm-fa-server",
            span_name=f"http {request.method} {request.url.path}",
            transport_handler=http_transporter,
            sample_rate=100.0,
            zipkin_attrs=zipkin_attrs,
        ):
            response = await call_next(request)

            return response
```

main.py에는

`setup_zipking_middleware(app)`

이것만 `app = FastAPI()` 아래에 추가함

## Zipkin을 EKS에 띄우기

mysql에 기록 저장하는 것으로 하려고 했음

db만 붙여두면 테이블은 알아서 생성한다고 한다.

- `zipkin_spans`: 추적의 각 부분(span)에 대한 정보
- `zipkin_annotations`: 각 span에 연관된 주석(annotation)
- `zipkin_dependencies`: 서비스 간의 의존성 정보

직접 본적은 없다.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      app: zipkin
  template: 
    metadata:
      labels:
        app: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim 
          env:
            - name: STORAGE_TYPE
              value: "mysql" 
            - name: MYSQL_HOST 
              valueFrom:
                secretKeyRef:
                  name: mysql-secret
                  key: host 
            - name: MYSQL_TCP_PORT 
              valueFrom:
                secretKeyRef:
                  name: mysql-secret
                  key: port 
            - name: MYSQL_DB 
              valueFrom:
                secretKeyRef:
                  name: mysql-secret
                  key: db 
            - name: MYSQL_USER 
              valueFrom:
                secretKeyRef:
                  name: mysql-secret
                  key: username 
            - name: MYSQL_PASS 
              valueFrom:
                secretKeyRef:
                  name: mysql-secret 
                  key: password
          ports:
             - containerPort: 9411

---
apiVersion: v1
kind: Service
metadata:
  name: zipkin-service  
spec:
  type: NodePort  
  ports:
    - port: 9411  
      targetPort: 9411  
      protocol: TCP   
      nodePort: 30100   
  selector:
    app: zipkin
```

예시 코드에서 NodePort 이길래 이거 ClusterIP로 바꾸고 우리꺼 Ingress에 넣을라했음

여기서부터 사건 시작..

Zipkin UI 에 접근할 때 그냥 뚫어두면 다 들어올 수 있음

로그인 방식으로 못들어가나 싶어서 알아보다가

DataDog에 그대로 못넣나? 했는데 갑자기 뤼튼이 마이그레이션하는법 알려줌.. DataDog APM이 똑같은 일을 해준다.

## 느낀 점

머리가 나쁘면 몸이 고생한다.

미리 좀 파악하고 들어가자.