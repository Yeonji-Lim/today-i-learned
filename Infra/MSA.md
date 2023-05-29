# 마이크로 서비스 아키텍처
애플리케이션을 독립적인 요소로 분해하여 서비스 제공

하나의 애플리케이션을 구성하면서 분할된 다수의 서버 또는 컨테이너를 통해 애플리케이션 기능뿐만아니라 데이터까지 분리

개발 주기의 단축, 쉬운 배포와 복구, 높은 확장성과 개방성 때문에 클라우드 네이티브 아키텍처에서 반드시 필요한 기술로 언급됨

마이크로 서비스가 구현되는 방식은 현대적이고 클라우드에 기반한 애플리케이션을 위한 자연스러운 토대를 만든다. 

중요한 것은 기술적으로 아키텍처를 잘 설계하는 것도 있지만, 서비스를 개발하는 팀의 구조를 아키텍처에 맞는 구조로 잘 만드는 것

개발된 시스템을 직접 배포하고 운영하는 플랫폼을 지원하기 위해서는 벤더에 종속적이지 않고 개발자가 쉽게 운영할 수 잇는 인프라 관리 기술이 필요함 -> 도커 컨테이너의 등장

## 예시
4개의 마이크로 서비스로 구성된 아키텍처

![](https://i.imgur.com/fvOn2dT.png)
(출처 : http://guruble.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4microservice-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B7%B8%EA%B2%83%EC%9D%B4-%EB%AD%A3%EC%9D%B4-%EC%A4%91%ED%97%8C%EB%94%94/)

- User Service는 REST API를 이용해서 Order Service를 활용하여 API Gateway를 통해 정보를 웹브라우저 화면에 표시하거나 모바일 클라이언트에 데이터를 제공함
- 알림이 필요한 경우 실제 알림이 어떤 과정을 통해 처리되는지 신경쓸 필요없이 알림 서비스를 이용하여 원하는 요청을 호출

여기서 중요
- 각 서비스를 위한 데이터 베이스가 따로 있다.
	- MSA가 가지는 근본적인 장점을 최대한 활용하기 위해서는 서비스별로 별도의 DB를 사용하는 것이 필요하다. 
	- 각 서비스의 특수성에 따라 가장 효율적인 DB를 선택하여 사용하는 것이 가능