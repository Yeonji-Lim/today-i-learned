# Hibernate

자바 언어를 위한 [ORM](ORM) 프레임워크

[JPA](JPA)의 구현체로, JPA 인터페이스를 구현하며, 내부적으로 [JDBC](JDBC) API를 사용한다.

## 장점

### 생산성
SQL을 직접 사용하지 않고, 메서드 호출만으로 쿼리가 수행돼요. 즉, SQL 반복 작업을 하지 않음으로 생산성이 높아져요

### 유지보수
테이블 컬럼이 변경되었을 때, 테이블과 관련된 DAO의 파라미터, 결과, SQL 등을 대신 수행해준다. 이로 인해 유지보수 측면에서 높아진다.

### 특정 벤더에 종속적이지 않음
- 추상화된 데이터 접근 계층을 제공하기 때문에 특정 벤더에 종속적이지 않다.
- 설정 파일에서 사용 DB를 언제든 바꿀 수 있다.

### 패러다임 불일치 해결
상속, 연관 관계, 객체 그래프 탐색, 비교 등 객체와 관계형 데이터베이스와의 패러다임 불일치를 해결

## 단점

