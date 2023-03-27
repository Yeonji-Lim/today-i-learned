# With
메모리 상에 가상의 테이블을 저장할 때 사용한다.

RECURSIVE의 여부에 따라 재귀, 비재귀 두 가지 방법으로 사용 가능

WITH 구문 이후에 오는 쿼리에서 임시 테이블의 테이블명을 사용하여 값을 참조할 수 있다.

```sql
WITH (RECURSIVE)[TABLE명] AS
(
    [SELECT문]
)
```

WITH RECURSIVE 구문은 가상 테이블을 생성하면서 가상 테이블 자신의 값을 참조하여 값을 결정할 때 사용된다.

0 ~ 10의 값을 갖는 임시 테이블을 생성  

```sql
WITH RECURSIVE CTE AS(
    SELECT 0 AS NUM # 초기값 설정
    UNION ALL
    SELECT NUM+1 FROM CTE
    WEHRE NUM < 10 # 반복을 멈추는 조건
)​
```

참고 : https://horang98.tistory.com/10