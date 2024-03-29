# Tip

## API 설계
API 설계시 Post, Get 등 http 메소드와 관련된 이름으로 설정하면 컴파일 단계에서 예상치 못한 에러가 발생될 수 있다. 다른 이름으로 잘 피해가야 한다.

## AWS와 Spring
Spring은 엔터프라이즈, AWS는 개인이다 보니, Spring이 무거워서 잘 올라가지 못하는 경우가 많다.

## Delete
실무에서는 삭제할 때 DB에서 진짜로 삭제하는 것이 아니라 Patch를 활용해서 유저가 보지 못하도록 상태 값을 바꾼다.

나중에 전략으로 활용을 할 수 있음, 법적으로 특정 기간 동안만 보관 가능하도록 함 

그런데 보여줄 때 마다 필터를 한번 더 걸어줘야 하는 번거로움이 있음

그런데 함수를 patch로 하고 메소드만 delete 로 하는 것은 안좋음 patch로 햇으면 메소드도 patch 여야 함

## Dto를 메소드 마다 다르게 해야 하는 이유
아무리 메소드 마다 요청과 응답이 같다고 해도 다르게 하는 것이 좋다

1. 확장성
2. 다보내면 보안적으로 위험해질 수 있고, 패킷의 크기가 커져서 안좋음
3. 그리고 보통 클라이언트 입장에서는 보내진 데이터는 필요한 데이터라고 생각해서 쓰이지 않는 데이터가 포함되어 있는 것은 안좋음

## URI
플랫폼이 여러개인 경우 플랫폼 별로 나눈다.
/app, /web