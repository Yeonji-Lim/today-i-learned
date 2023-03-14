
# 객체 참조에 의한 호출(Call by object reference)

파이썬의 경우, Call by reference, Call by Value가 아닌 Call by object reference 이다.

공유에 의한 호출(Call by sharing)이라고도 부른다.

파이썬은 모든 것이 객체(object)고 하나의 개체는 하나의 인스턴스로 존재한다.

즉 a = 2 같은 경우 a에 2가 할당되는 게 아니라 2라는 인스턴스를 가리키게 되는 것


객체의 종류에 따라 call by reference 또는 call by value 가 결정된다.
-   immutable object(int, float, str 등)일 경우 call by value로 넘어가서 값을 바꿀 수 없다.
-   mutable object(list, dict, set 등)일 경우 call by reference로 넘어가서 값을 바꿀 수 있다.