# 추상 메소드(Abstract Method)

선언은 되어 있으나 코드가 구현되어 있지 않은 메소드

abstract 키워드와 함께 원형만 선언하고 코드는 작성하지 않는다.

~~~
public abstract String getName();
public abstract void setName(String s);

// 컴파일 오류 : abstract 키워드를 붙이고 모드가 작성되어 있으면 안된다.
public abstract int getAge() { return "20"; } 
~~~

# 추상 클래스(Abstract Class)

**실체 클래스의 공통적인 부분을 추출해 어느정도 규격을 잡아놓은 추상적인 클래스**

추상 클래스는 상속에서의 슈퍼 클래스를 말한다. 

이때도 abstract 키워드를 사용하며, 추상클래스가 되는 경우는 두가지가 있다.

- 추상 메소드를 포함하는 클래스
- 추상 메소드가 없지만 abstract로 선언한 클래스

주의할 점은 추상 메소드를 가지고 있다면 반드시 추상 클래스여야 한다는 것이다.

또, 추상 클래스는 객체(인스턴스)를 생성할 수 없다.

추상 클래스는 객체를 생성할 목적으로 만드는 클래스가 아니다.

실행 코드가 없는 추상 메소드를 포함할 수 있기 때문에 객체를 생성하면 컴파일 오류가 발생한다.

레퍼런스 변수의 선언은 가능하다.

```java
// Person이라는 추상 클래스가 있을 때
Person person;          //에러 아님
person = new Person();  //에러
```

그러면 이 추상 클래스는 왜 사용하는 것일까?

추상 클래스를 이용하면 설계와 구현을 분리할 수 있다. 

미리 추상 클래스로 방향을 잡아두고, 이 추상 클래스를 상속 받아서 그 내부를 서브 클래스에서 구현하면 구현 작업이 쉬워진다.

계층적 상속관계를 가지는 클래스들의 구조를 만들 때에도 적합하다.

## 추상 클래스의 구현

추상 클래스에 선언된 모든 추상 메소드를 서브 클래스에서 오버라이딩하여 구현하는 것을 말한다.

만약에 어떤 Shape이라는 클래스가 있고, 그 클래스를 상속받은 Line, Rect, Circle 클래스가 있다고 하자

Shape에는 draw()라는 메소드가 있고, 서브 클래스에서 각자 draw()를 오버라이딩 한다

그러면 굳이 추상 클래스를 쓰지 않아도 구현이 가능한데 어떤 차이가 있을까?

추상 클래스로 선언하지 않는 경우 서브 클래스에서 draw()를 오버라이딩하지 않아도 무관하다.

그런데 만약 Shape이 추상 클래스, draw()가 추상 메소드로 선언되었다면,

서브 클래스들은 반드시 draw()를 오버라이딩해야 한다.

그렇지 않으면 컴파일 오류가 발생한다.

이로서 추상 클래스는 추상 메소드를 통해 서브 클래스가 구현할 메소드를 명료하게 알려주는 인터페이스의 역할을 하고, 

서브 클래스는 추상 메소드의 목적에 맞게 구현하는 다형성을 실현한다.

## 추상 클래스의 상속

그런데 구현하지 않고 상속 받은 서브 클래스가 있다.

이때는 서브클래스 또한 추상 클래스이고 abstract 키워드를 붙여주어야 컴파일 오류가 발생하지 않는다.

추상 메소드를 오버라이딩하지 않는 경우도 마찬가지다.