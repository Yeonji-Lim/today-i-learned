# 팩토리 패턴
객체의 생성을 캡슐화한다.

두가지가 있다!

## 팩토리 메소드 패턴
객체를 생성하기 위한 인터페이스를 정의하는 데, 어떤 클래스의 인스턴스를 만들지는 서브 클래스에서 결정 -> 서브클래스에게 클래스 인스턴스를 만드는 일을 맡긴다.

[의존성 역전 원칙](DIP)을 준수하기에 적합한 방법이다.

팩토리 메소드(createProduct)를 포함하는 추상 클래스를 정의한다.

## 추상 팩토리 패턴

인터페이스를 이용하여 서로 연관된, 또는 의존하는 객체를 구상 클래스를 지정하지 않고도 구성한다.
