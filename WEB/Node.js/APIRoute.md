Route : 경로, 출발지와 목적지가 있다. 라우팅에 의한 결과

Routing : 경로를 찾아가게 하는 과정, 목적에 따라 효율적인 라우팅 프로토콜을 선택하는 것

Routing [Protocol](Protocol) : 찾아주는 규칙을 사용하는 프로토콜

# Next.js의 라우터

페이지 개념을 기반으로 구축된 파일 시스템 기반 라우터

pages 폴더에 추가된 파일로 라우트를 자동 생성한다.

pages/api 폴더 외에 위치한 모든 파일은  html로 반환


## Index Route

index 라는 이름을 가진 파일을 루트로 자동 라우팅

## Nested Route

중첩된 파일은 차례로 풀어서 라우팅

~~~
pages/api/events/index.ts --> /api/events
~~~

## Dynamic Route

대괄호를 사용하면 Request 객체를 통해 대괄호 안의 값을 사용할 수 있다.
~~~
pages/api/events/[eventId]/orders/index.ts --> /api/events/:eventId/orders
~~~

## API Route

Next.js로 API를 만드는 솔루션.

이걸 작동하게 하려면 함수를 기본값으로 보내야 함


## 라우팅 (Routing)

라우터로 패킷을 전송하는 것

IP 네트워크에서는 패킷의 전송을 제어하는 라우팅 테이블이 중요하다.

라우팅 테이블 : 수신할 곳의 네트워크 & 그 네트워크에 대한 전송방법 에 대한 정보가 담긴 테이블

라우팅은 전송 규칙에 따라 수행되고,

라우팅테이블은 전송규칙을 결정하는 데에 중요한 요소.


라우팅 테이블은 영구적이지 않다.

새로운 네트워크의 추가, 네트워크 접속 상태의 변경에 따라 라우팅 테이블을 수정해주어야 한다.

라우팅 테이블을 수정하는 방식에 따라 정적 라우팅과 동적 라우팅이 나뉜다.


### 정적 라우팅 (Static Routing)

라우팅 테이블을 수동으로 관리

수동으로 수정할 때 이외에는 고정 -> 그래서 정적 라우팅이라고 함

네트워크 전체의 규모가 아주 작거나 구성을 변경할 일이 별로 없는 경우에 사용


### 동적 라우팅 (Dynamic Routing)

라우팅 테이블을 자동으로 관리

라우터들끼리 정기적으로나 필요에 따라서 네트워크 접속 라우터에 대한 정보를 교환, 자동 변경

새로운 네트워크가 연결되면 인접 라우터로 그 정보를 전달


웹에서는 라우트의 경로에 특정 값을 넣어 해당 페이지로 이동할 수 있게 하는 것을 말한다.

리액트에서의 동적 라우팅의 방식은 2가지가 있다.

1. Query parameters

2. URL parameters

Next.js에서 동적 라우팅으로 입력될 값은 폴더나 파일 명에 대괄호('[]')로 씌워진 값이며,

req 객체의 query가 동적라우팅으로 입력된 값을 가지고 있다.

한편 이 query는 path의 query parameter도 가지고 있다.


## HTTP Request가 들어왔을 때

보통 이렇게 3단계가 진행된다.

1. Validation : 입력값 검증

2. 데이터 추가/조회/변경/삭제

3. 결과 반환

근데 만약 입력값 검증 결과 올바른 데이터가 아니면 실패결과를 반환한다.


## [Validation](Validation)

Next.js에서는 req의 query가 동적 라우팅으로 입력된 값을 가지고 있다고 하였다.

그래서 이 값을 가지고 Validation을 하면 다음과 같다. 여기서 동적 라우팅으로 입력된 값이 eventId라고 하자

~~~
...
const { eventId } = req.query;

// Validataion, 유효성 검사
if(eventId === undefined) {
    res.status(400).send('eventId');
    return;
}
...
~~~

그런데 체크하는 값이 많아진다면 모두 체크하기 어려운데, Fastify 프레임워크의 Ajv모듈을 이용해서 유효성 검사를 할 수 있다.

