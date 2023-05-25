# HTTP
HyperText Transfer [Protocol](Protocol.md)

웹 서버와 클라이언트는 지속적으로 연결을 유지한 상태가 아니라 요청 - 응답의 반복일 뿐이다.

-> 이전 요청과 새로운 요청이 같은 사용자(브라우저)에서 이루어졌는지 확인하는 방법이 필요함

-> 그렇게 등장한 것이 '[쿠키](Cookie)'와 '[세션](WEB/Session.md)'

주요 메소드 : GET, POST, PUT

중요 특징 : [Stateless](Stateless.md)

## Half Duplex, 반이중 통신
클라이언트가 먼저 요청을 보내고, 그 요청에 따라 웹 서버가 응답하는 형태
- 웹서버는 응답을 보낸 후 클라이언트와 연결을 끊는다.

양쪽이 데이터를 동시에 보내는 것이 아니기 때문에 반이중 통신