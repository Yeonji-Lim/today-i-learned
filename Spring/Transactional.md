# @Transactional
#작성필요 

클래스나 메서드에 붙여줄 경우, 해당 범위 내 메서드가 트랜잭션이 되도록 보장해준다

직접 객체를 만들 필요 없이 선언만으로도 관리를 용이하게 해주기 때문에 선언적 트랜잭션이라고도 한다.

해당 어노테이션을 붙인 메서드의 경우

- 연산이 고립되어, 다른 연산과의 혼선으로 인해 잘못된 값을 가져오는 경우가 방지된다.
- 연산의 원자성이 보장되어, 연산이 도중에 실패할 경우 변경사항이 Commit되지 않는다.

UPDATE, DELETE 할 경우에 꼭 붙여주어야 함 -> 안 붙이면 `javax.persistence.TransactionRequiredException` 에러 발생

참고 : https://kafcamus.tistory.com/30