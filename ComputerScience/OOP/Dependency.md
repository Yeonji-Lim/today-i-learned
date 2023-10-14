# 의존성

한 객체가 다른 객체를 사용할 때 의존성이 있다고 한다.

```java
public class Store { 
	private Pencil pencil; 
}
```

Store 객체가 Pencil 객체에 의존성이 있다.  
== Pencil의 변경사항에 대해 Store가 변해야 한다. 

Association --> **A _has-a_ C** object (as a member variable)

Dependency --> **A _references_ B** (as a method parameter or return type)

```java
public class A {
    private C c; // association
    public void myMethod(B b) { // dependency
        b.callMethod();
    }
}
```