# Optional\<T\>

Java8에서 제공하는 NPE(NullPointerException)을 방지할 수록 도와주는 클래스

null이 올 수 있는 값을 감싸는 Wrapper 클래스

참조하더라도 NPE가 발생하지 않는다. 

## .of .ofNullable
다른 객체를 Optional로 감쌀 때 null을 허용하느냐에 따라 다른 메소드 사용

.of는 null을 입력하면 NPE 발생
.ofNullable은 null 허용

## .get
객체를 Optional에서 꺼낼 때

## .orElse .orElseGet

.orElse : T의 모든 매개 변수 사용
.orElseGet : T 유형의 개체를 반환하는 Supplier 유형의 인터페이스 허용

```java
public T orElse(T other) { 
	return value != null ? value : other; 
} 

public T orElseGet(Supplier<? extends T> other) { 
	return value != null ? value : other.get(); 
}
```

## .isPresent .ifPresent

.isPresent : true, false 체크
.ifPresent : 값을 가지고 있는지 확인 후 예외처리