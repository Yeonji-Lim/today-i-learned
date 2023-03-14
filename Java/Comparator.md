# Comparator

참고 : [Compara___](Compara___)

- import : util
- [Interface](Interface)

## 구현해야 하는 메소드

``` java
public int compare(Type o1, Type o2) {...}
```

자기 자신과 상관없이 두 객체 비교

## 기능만을 따로 구현하기
클래스를 정의하고 그 안에서 Comparator를 정의하는 것이 아니라,

Comparator의 기능 그 자체만을 사용하고 싶을 때, 

이 기능만을 따로 두기 위해 익명 객체(클래스)를 이용한다.