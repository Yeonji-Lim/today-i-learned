# Predicate
```java
@FunctionalInterface 
public interface Predicate<T> { 
	// 주어진 arguments를 검증 
	boolean test(T t); 
	
	// 다른 Predicate와 연결하는 역할 && 
	default Predicate<T> and(Predicate<? super T> other) { 
		Objects.requireNonNull(other); 
		return (t) -> test(t) && other.test(t); 
	} 
	
	// test()의 반대 결과 반환 (ex: true -> false) 
	default Predicate<T> negate() { 
		return (t) -> !test(t); 
	} 
	
	// 다른 Predicate와 연결하는 역할 || 
	default Predicate<T> or(Predicate<? super T> other) { 
		Objects.requireNonNull(other); 
		return (t) -> test(t) || other.test(t); 
	} 
	
	// 동일한지 체크 
	static <T> Predicate<T> isEqual(Object targetRef) { 
		return (null == targetRef) ? Objects::isNull : object -> targetRef.equals(object); 
	} 
	
	@SuppressWarnings("unchecked") 
	static <T> Predicate<T> not(Predicate<? super T> target) { 
		Objects.requireNonNull(target); 
		return (Predicate<T>)target.negate(); 
	} 
}
```

인자를 두개 받으면 BiPredicate이다.
## 예제
```java
@Test public void test() { 
	Predicate<Integer> predicate1 = (num) -> num < 10; 
	Predicate<Integer> predicate2 = (num) -> num > 5; 
	assertThat(predicate1.and(predicate2).test(7)).isTrue(); 
}
```