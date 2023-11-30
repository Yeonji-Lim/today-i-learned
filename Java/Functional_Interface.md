# 함수형 인터페이스
1개의 [추상 메소드](Abstract_Method)를 갖는 인터페이스(Single Abstract Method Interface) : `default method` 또는 `static method` 는 여러 개 존재해도 상관 없다

[Java8](Java8.md) 부터 인터페이스는 기본 구현체를 포함한 [디폴트 메소드](Default_Method)를 포함할 수 있다.

여러 개의 디폴트 메서드가 있어도 추상 메서드가 오직 하나면 함수형 인터페이스

[람다](Lambda) 표현식은 함수형 인터페이스만 가능

## @FunctionalInterface
해당 인터페이스가 함수형 인터페이스 조건에 맞는지 검사

## 기본적으로 제공하는 함수형 인터페이스
매번 직접 만드는 것은 번거로움

기본 제공만 사용해도 웬만한 람다식은 다 만들 수 있음 

![](https://i.imgur.com/lMOxmtX.png)
