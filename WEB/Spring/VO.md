# Value Object
값 오브젝트로써 값을 위해 쓰임

주소가 달라고 값이 같으면 같은 객체로 처리

getter, 로직을 포함할 수 있지만, setter는 포함할 수 없다. 값의 비교를 위해 `equals()`, `hashCode()`등을 오버라이딩해야한다. 