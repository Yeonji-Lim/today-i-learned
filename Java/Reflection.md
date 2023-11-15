# Reflection
객체를 통해 클래스의 정보를 분석해내는 프로그램 기법

Spring에서 BeanFactory라는 Spring Container 개념에서

BeanFactory는 객체의 인스턴스를 생성하는데, 이 때 필요한 기술이 Reflection

원래 자바에는 동적으로 객체를 생성하는 기술이 없었다. 이를 가능하게 하는 것이 Reflection

효과
생성자, 메소드, 필드 등 클래스에 대한 정보를 아주 자세히 알아낼 수 있다.

Reflection이 있기에 Spring에서 `@Component`, `@Bean`과 같은 어노테이션을 프레임워크의 기능을 사용할 수 있다. 사실 어노테이션은 Reflection이 없다면 아무 역할도 하지 못한다.

Reflection을 사용하면 접근 제어자와 무관하게 클래스의 필드나 메소드도 가져와서 호출할 수 있다.

## 종류
### Class 클래스
java.lang에서 제공

#### 획득 방법
1. class 프로퍼티로 획득
2. getClass() 메소드로 획득
3. Class 클래스의 forName() 정적 메소드
   그 메소드 안에 [FQCN](FQCN) 을 전달하여 획득
   
#### getXXX() vs getDelcaredXXX()
Class 객체의 메소드
getXXX() : 상속받은 클래스와 인터페이스를 포함하여 모든 public 요소
getDelcaredXXX() : 상속받은 클래스와 인터페이스를 제외하고 해당 클래스에 직접 정의된 내용만

#### Constructor
Class 객체에서 Constructor 타입으로 생성자를 가져올 수 있음

이런식으로 Field, Method, Annotation을 가져올 수 있다. 

## 단점
일반적으로 메소드를 호출한다면 컴파일 시점에 분석된 클래스를 사용
근데 리플렉션은 런타임에 클래스를 분석한다. -> 속도가 느림 (JVM을 최적화할 수 없기 때문)
