# Method Area
== Class Area == Static Area
클래스 정보를 처음 메모리 공간에 올릴 때 초기화되는 대상을 저장하기 위한 메모리 공간
Runtime Constant Pool에 상수형을 저장하여 중복을 막는다.
## 저장되는 정보
- Field Information
	- 멤버 변수에 대한 정보 (이름, 타입, 접근 지정자 등)
- Method Information
	- 메서드에 대한 정보 (이름, 리턴 타입, 파라미터, 접근 지정자 등)
- Type Information
	- Class 인지 Interface 인지 혹은 Type의 속성, 이름, super class의 이름 등