# IoC Container

[Inversion of Control](IoC.md)

~~~
**
Class    : 설계도 (추상적인 것)    -> 가구
Object   : 실체화가 가능한 것      -> 의자
Instance : 실체화가 된 것         -> 의자1, 의자2
~~~

생성된 object(instance)는 heap [메모리](Memory)에 올라가게 된다.

그리고 그걸 생성한 메서드가 관리하게 된다.


그래서 다른 메서드에서 같은 오브젝트를 사용하고 싶다면 공유 받아야함

스프링은 오브젝트 목록을 읽어서(스캔) heap 메모리에 알아서 띄워주고 관리함 -> IoC

모든 클래스의 메소드에서 같은 오브젝트를 공유해서 사용할 수 있음 (싱글톤)
