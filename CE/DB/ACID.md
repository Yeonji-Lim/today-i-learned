# Atomic (원자성)

All or Nothing 모든 작업이 실행되거나 실행되지 않아야 함

> ex : A 계좌에서 B 계좌로 잔액 송금
> 
> `A계좌 잔액 줄이기` 작업과 `B계좌 잔액 늘리기` 작업은 함께 성공하거나 함께 실패해야 함

# Consistency (일관성)

모든 트랜잭션이 종료된 후에는 DB의 제약조건을 모두 지키고 있는 상태가 되어야 한다.

> ex : 잔액은 0원 이상
> 
> 이를 위반하는 트랜잭션은 모두 중단됨

# Isolation (격리성)

- 트랜잭션은 다른 트랜잭션과 독립적으로 동작해야 한다.

- A 트랜잭션이 하는일은 B 트랜잭션이 몰라야한다.

> 현실
> - 성능과 안정성의 트레이드 오프
> - 다음의 순서로 성능은 떨어지고, 격리성(고립성)은 증가
> 	  READ_UNCOMMITTED > READ_COMMITTED > REPEATABLE_READ > SERIALIZABLE

# Durability (지속성)