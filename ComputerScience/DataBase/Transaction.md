# 트랜잭션

트랜잭션의 특징 : [ACID](ACID.md)

데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위

-   데이터베이스의 상태를 변화시킨다는 것?
	
	== SQL을 이용하여 데이터베이스에 접근하는 것
	

이때 작업의 단위는 질의어 한문장이 아니라는 것을 주의하자!
q
많은 질의어 명령문들을 사람이 정하는 기준에 따라 정하는 것

ex : 게시판에 글을 올리고 글이 올려졌는지 확인 → insert 문 + select문

트랜잭션 설계를 잘하는 것이 데이터를 다루는 것에 많은 이점이 있다.

-   특징
	-   원자성 : 트랜잭션이 데이터베이스에 모두 반영이 되거나 전혀 반영이 되지 않아야
	-   일관성 : 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야
	-   독립성 : 트랜잭션 연산 중간에 다른 트랜잭션이 끼어들 수 없다.
	-   지속성 : 트랜잭션이 성공적으로 완료되면 결과는 영구히 반영되어야

트랜잭션의 반영, 취소를 COMMIT, ROLLBACK 연산으로 진행 가능