Route : 경로, 출발지와 목적지가 있다. 라우팅에 의한 결과

Routing : 경로를 찾아가게 하는 과정, 목적에 따라 효율적인 라우팅 프로토콜을 선택하는 것

Routing Protocol : 찾아주는 규칙을 사용하는 프로토콜

​

# Next.js의 라우터

페이지 개념을 기반으로 구축된 파일 시스템 기반 라우터

pages 폴더에 추가된 파일로 라우트를 자동 생성한다.

pages/api 폴더 외에 위치한 모든 파일은  html로 반환

​

## Index Route

index 라는 이름을 가진 파일을 루트로 자동 라우팅

​

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