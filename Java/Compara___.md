# [Comparable](Comparable) and [Comparator](Comparator)

## Interface

두 클래스 모두 [인터페이스](Interface) -> 즉, 구현해야 사용이 가능하다.

> Interface
> 필수 요소들을 선언만 해둠, 구체적인 구현을 해서 사용한다.

## 객체를 비교할 수 있도록 만든다.

비교할 수 있는 변수(`primitive type`)을 제외한 객체에서, 

비교가 가능하도록 기준을 정해준다.

# 비교 대상
두 클래스는 서로 비교의 대상이 다르다. 

## Comparable
자기 자신을 기준으로 매개변수 객체를 비교

## Comparator
자기 자신과 무관하게 두 매개변수 객체를 비교

# import
Comparable은 import가 필요 없지만, Comparator의 경우 util의 import가 필요하다.