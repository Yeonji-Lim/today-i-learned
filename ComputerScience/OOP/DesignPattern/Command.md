# 커맨드 패턴

- 이벤트가 발생했을 때 실행될 기능이 다양하면서도 변경이 필요한 경우에 사용한다.
- 이벤트를 발생시키는 클래스를 변경하지 않고 재사용하고자 할 때 유용!
- 실행될 기능을 캡슐화 -> 호출자와 수신자 클래스 사이의 [의존성](Dependency.md)을 제거
	-> 기능이 변경되더라도 호출자 클래스를 수정할 필요 없음!

<img width="478" alt="image" src="https://user-images.githubusercontent.com/57888020/169934799-01ea0f02-2502-454c-adac-1a7d92149a19.png">

<img width="386" alt="image" src="https://user-images.githubusercontent.com/57888020/169935289-78789781-30c4-46a7-8afe-2aaf474c93d2.png">

- 호출자(Invoker) : 기능의 실행을 요구
- 수신자(Receiver) : 실제 기능을 실행
- Command : 실행될 기능의 인터페이스. 실행될 기능을 excute 메소드로 선언
- ConcreteCommand : 실제로 실행되는 기능을 구현. Command 인터페이스를 구현함

<img width="540" alt="image" src="https://user-images.githubusercontent.com/57888020/169935578-3d21615d-3816-482e-b1a0-6efaa6b7fa74.png">

작업 요청 자체가 객체화 -> 작업 요청 자체를 저장, 복구 확장 가능

## Command 지능화
단순히 받은 request를 receiver에게 전달하는 것만 수행할 수도 있지만,
주된 receiver의 도움 없이 자신이 모든 것을 구현하는 것까지 범위가 다양하다.

## undo, redo
실행된 Command를 저장하는 history 리스트 필요

