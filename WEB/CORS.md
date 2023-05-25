# Cross-Origin Resource Sharing, 교차 출처 리소스 공유

추가 HTTP 헤더를 사용해 

한 출처에서 실행 중인 웹 어플리케이션이 

다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 

브라우저에 알려주는 체제

이때 출처(Origin) : domain, protocol, port

웹 어플리케이션은 리소스가 자신의 Origin과 다를 때 CORS 요청을 실행한다.

이에 대한 응답으로 서버는 Access-Control-Allow-Origin 헤더를 보낸다.

![](https://i.imgur.com/XLZ9EBA.png)


# 참고
https://dev-gorany.tistory.com/212