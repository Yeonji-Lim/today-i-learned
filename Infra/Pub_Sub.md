# Pub/Sub Model

메시지 기반의 [미들웨어](Middleware) 시스템

publisher가 어떤 subscriber가 있는지 모르는 상태에서 미들웨어로 메시지 전송

## Message Filtering

### Topic-based system
publisher가 먼저 message의 topic를 정의한 후 topic으로 메시지 전송
subscriber는 subscribe한 topic으로 전송되는 메시지를 전송 받음

### Content-based system
subscriber가 먼저 message에 대해 자신이 원하는 topic를 정의
topic에 맞는 메시지만 publisher로부터 전송받음

### Hybrid system
위 두 유형을 합친 형태

## 장점

### loosely coupled
미들웨어로 연결을 약하게 만들었다
원래는 서로의 시스템 토폴로지에 대한 제약이 많았는데 신경쓸 필요가 없어지는 것

### Scalable
상대적으로 적은 설치 비용 및 규모에 비해 연결이 약함 -> 뛰어난 확장성

## 단점

### End-to-end 시스템의 강점 상실
직접 통신이 아니기 때문에 의도한대로 전달하지 못할 수 있음

## Redis 와 Kafka에서 Pub/Sub의 다른 점
1. 이벤트 저장 여부
2. 한 이벤트를 받을 수 있는 Subcriber 개수