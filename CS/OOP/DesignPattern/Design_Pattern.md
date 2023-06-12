# 디자인 패턴
설계 문제에 대한 해답을 문서화하기 위해 고안된 형식 방법

소프트웨어를 설계할 때 특정 맥락에서 자주 발생하는 고질적인 문제들이 또 발생했을 때 재사용할 할 수 있는 훌륭한 해결책

> 바퀴를 다시 발명하지 마라(Don’t reinvent the wheel)

## 왜 디자인 패턴을 써야하는 가
반복적으로 발생하는 문제에 동일한 솔루션이 적용될 때, 이러한 설계를 패턴이라고 한다.

유연하고 유지보수하기 좋은 프로그램을 개발하기 위해, 문제 해결에 효율적인 솔루션을 설계하기 위해 디자인 패턴을 알아야한다.

## 종류

### 생성 패턴 (Creational Pattern)

객체의 생성 방식을 결정한다. 

-   추상 팩토리 메서드 (Abstract Factory Methods) : 관련된 부품을 조립해서 제품을 만든다.
-   팩토리 메서드 (Factory Methods) : 인스턴스 작성을 하위 클래스에게 맡긴다.
-   빌더 (Builder) : 잡한 인스턴스를 조립한다.
-   프로토타입 (Prototype) : 복사해서 인스턴스를 만든다.
-   [싱글톤 (Singleton)](Singleton.md) : 단 하나의 인스턴스.

### 구조 패턴 (Structural Pattern)

객체간의 관계를 조직하여 더 큰 구조를 만든다.

-   어댑터 (Adapter) : 한 꺼풀 덧씌워 재사용.
-   [브리지 (Bridge)](Bridge.md) : 기능의 계층과 구현의 계층을 분리한다.
-   [컴퍼지트 (Composite)](Composite.md) : 그릇과 내용물의 동일시.
-   [데코레이터 (Decorator)](Decorator.md) : 장식과 내용물의 동일시.
-   퍼사드 (Facade) : 간단한 창구.
-   플라이웨이트 (Flyweight) : 동일한 것을 공유해서 낭비를 없앤다.
-   프록시 (Proxy) : 필요해지면 만든다.

### 행위 패턴 (Behavioral Pattern)

객체의 행위를 조직, 관리, 연합

-   책임 연쇄 (Chain of Responsibility) : 책임 떠넘기기.
-   [커맨드 (Command)](CE/OOP/Design_Pattern/Command.md) : 명령을 클래스로 만든다.
-   인터프리터 (Interpreter) : 문법 규칙을 클래스로 표현한다.
-   [이터레이터 (Iterator)](Iterator.md) : 하나씩 세다.
-   미디에이터 (Mediator) : 상대는 카운셀러 한사람뿐.
-   메멘토 (Memento) : 상태를 보존한다.
-   [옵저버 (Observer)](Observer) : 상태의 변화를 통지한다.
-   스테이트 (State) : 상태를 클래스로서 표현한다.
-   [스트레티지 (Strategy)](Strategy) : 알고리즘을 모두 교체한다.
-   템플릿 메서드 (Template Meothods) : 체적인 처리를 하위 클래스에게 맡긴다.
-   비지터 (Visitor) : 구조 안을 돌아다니면서 일을 한다.
