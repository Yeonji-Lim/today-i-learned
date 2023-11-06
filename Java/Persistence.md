# 영속성(Persistence)
데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성

> 영속성을 갖지 않는 데이터는 단지 [메모리](Memory)에만 존재하기 때문에 프로그램을 종료하면 모두 잃어버리게 된다.

## Object Persistence
영구적인 객체
메모리 상의 데이터를 파일 시스템, 관계형 데이터베이스 혹은 객체 데이터 베이스등을 활용하여 영구적으로 저장하여 영속성을 부여

> 데이터를 데이터베이스에 저장하기
> 
> 1. JDBC : java
> 2. Spring JDBC : JdbcTemplate
> 3. Persistence Framework : Hibernate, Mybatis

## Persistence Layer
프로그램의 아키텍처에서 데이터에 영속성을 부여해주는 계층
JDBC를 이용하여 직접 구현 가능하나 Persistence framework를 이용한 개발이 많이 이루어짐

## Persistence Framework
JDBC 프로그래밍의 복잡함이나 번거로움 없이 간단한 작업만으로 데이터베이스와 연동되는 시스템을 빠르게 개발할 수 있다. 안정적인 구동을 보장한다. 
SQL Mapper와 [ORM](ORM)으로 나눌 수 있다.
ex : [JPA](JPA), Hibernate, Mybatis