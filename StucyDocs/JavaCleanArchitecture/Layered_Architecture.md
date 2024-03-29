# 계층형 아키텍처의 문제점

## 계층형 아키텍처는 데이터베이스 주도 설계를 유도한다.
---
- ORM 사용으로 데이터베이스 중심적인 아키텍처가 만들어진다.
- **비즈니스 관점에서 도메인 로직이 먼저 만들어져야 한다.**
- ORM 사용으로 도메인 계층(Service)는 자연스럽게 영속성 계층과 강한 결합을 하게 된다.
	- 서비스가 엔티티와 레포지토리를 같이 참조
	- 도메인 로직을 구현하면서 eager, lazy 로딩 문제, 트랜잭션 관리, 캐시 초기화 등의 문제들을 신경
	- 영속성 계층이 도메인 코드에 녹어들어 둘 중 하나를 바꾸는 것이 어려워진다.

## 지름길을 택하기 쉬워진다.
---
지름길 ex : 컨트롤러가 서비스를 거치지 않고 바로 엔티티와 레포지토리에 접근 -> 도메인 로직을 웹 계층에 구현

## 테스트를 어렵게 만든다.
---
웹 계층 테스트에서 영속성 계층도 mocking 해야 함 -> 서비스 계층만 해도 진짜 귀찮았는데,, 엄청 별로다

## 유스케이스를 숨긴다.
---
- 계층형 아키텍처에서는 넓이를 제한하지 않음 : 여러 유스케이스를 담당하는 넓은 서비스가 만들어지기도 한다.
	- 넓은 서비스 : 영속성 계층에 많은 의존성

## 동시작업이 어려워진다.
---
- 넓은 서비스 -> 충돌 가능성 높아짐

# 엄격한 계층형 아키텍처
엄격한 룰로 유지보수하기 좋은 아키텍처를 만들 수 있지만 

이 말은 계층형 아키텍처가 그만큼 잘못된 것들을 허용한다는 의미