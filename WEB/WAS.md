# Web Application Server
웹 애플리케이션을 수행하는 [미들웨어](ComputerScience/SoftwareEngineering/Middleware.md)

웹 서버와 JSP/Servlet 애플리케이션 수행을 위한 엔진으로 구성

데이터 접근, 세션 관리, 트랜잭션 관리 등을 위한 라이브러리를 제공하고 있다.

예시 : Spring, node, express, django, tomcat

클라이언트가 볼때는 웹 서버와 WAS가 하나의 큰 서버로 보임

![[웹서버와WAS.png]]

웹 서버는 문지기 역할 요청이 어떤 WAS로 가야하는지 보내줌

WAS는 받으면 응답을 웹서버로 전달하고 웹 서버가 클라이언트에게 전해줌

보통 서버들을 다 한번에 같은 컴퓨터에 안둔다.

![[웹서버와WAS2.png]]
관련 용어 : 클러스터링, 스케일업, 스케일 다운