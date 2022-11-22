# 쿠키

[HTTP](HTTP) 쿠키, 웹 쿠키, 브라우저 쿠키

**서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각**

브라우저는 이 데이터 조각을 저장해 두었다가 동일한 서버 재요청시 저장된 데이터를 함께 전송

주로 두 요청이 동일한 브라우저에서 들어왔는지를 판단할 때 사용된다.

이를 통해 사용자 로그인 상태를 유지할 수 있다. 
→ [Stateless](Stateless) HTTP [프로토콜](Protocol)에서 상태 정보를 기억해주기 때문

쿠키 사용 목적

-   [세션](Session) 관리 : 서버에 저장해야 할 로그인, 장바구니, 게임 스코어 등의 정보 관리
-   개인화 : 사용자 선호, 테마 등의 세팅
-   트래킹 : 사용자 행동을 기록하고 분석

현재는 쿠키 보다 mordern storage API들을 사용해 정보를 저장하는 것을 권장함

ex : 웹 스토리지 API와 IndexedDB