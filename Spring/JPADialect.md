# JPA Dialect

JPA는 어플리케이션이 직접 SQL을 작성하는 것이 아닌 JPA가 직접 SQL을 작성하고 실행하는 형태이다.

-> 근데 이게 DBMS마다 설정이 다르다

application에 이 dialect의 버전을 명시해주지 않아서 에러가 발생할 수 있다.

나 같은 경우에 쿼리를 직접 작성해서 돌릴 때 에러가 났다.