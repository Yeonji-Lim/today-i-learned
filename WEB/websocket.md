# websocket
새로고침 없이 화면을 바꿈

서버와 클라이언트가 실시간으로 양방향 통신을 할 수 있도록 해주는 프로토콜

전이중 통신(Full Duplex)을 지원하기 위한 프로토콜

> Ajax
> 페이지 이동 없이 페이지 내부만 새로고침
> HTTP를 이용하기 때문에 요청을 보내야 응답이 온다.
> 새로고침을 위해 버튼을 누른다거나 주기적으로 요청을 보내면 번거롭고 자원 낭비를 부른다.

프로토콜의 요청은 `ws://~`로 시작한다.

최초 접속은 [HTTP](ComputerScience/ComputerNetwork/HTTP.md) Request를 통해 HandShaking 과정을 통해 이뤄진다.
- 기존의 80, 443 포트로 접속 : 추가 방화벽을 열지 않고도 양방향 통신이 가능
- HTTP 규격인 [CORS](CORS) 적용이나 인증 등 과정을 기존과 동일하게 가져갈 수 있다.

## 도입이 적절한 경우
- 실시간성을 보장해야 하는 경우 
- 변경 사항의 빈도가 잦은 경우
- 짧은 대기 시간, 고주파수, 대용량의 조합인 경우

반대로 변경 사항의 빈도가 자주 일어나지 않고, 데이터의 크기가 작은 경우 Ajax, Streaming, Long polling 기술이 더 효과적일 수 있다

## 구현 in Spring

여러 클라이언트 핸들할 핸들러 필요

### TextWebSocketHandler
#모름 

config에서 websocket 활성화 시킴

### WebSocketConfigurer
#모름 

### WebSocketHandlerRegistry
#모름 여기에 핸들러 저장함


## WebSocket 이전
#작성필요 
https://dev-gorany.tistory.com/212

# 참고
https://dev-gorany.tistory.com/212
https://velog.io/@koseungbin/WebSocket