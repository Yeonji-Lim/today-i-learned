# Stateless
**서버가 클라이언트의 [세션](WEB/Session.md) 상태 및 세션 정보를 저장하지 않는 네트워크 [프로토콜](Protocol.md)**

-   요청에 대한 응답만 처리한다.
-   각 통신은 선행되거나 후속으로 따라오는 통신과 관련이 없다.
-   클라이언트가 송신하려 했던 모든 데이터가 서버쪽에 수신되었는지 확인하지 않음

ex : [UDP](UDP.md) 프로토콜, 온라인 검색

-   장점 : 확장성이 좋음
-   클라이언트 측에서 송신할 데이터의 양이 많아짐