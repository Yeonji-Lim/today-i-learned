# Heap
객체를 저장하는 가상 메모리 공간
new 연산자로 생성된 객체와 배열 저장

[프로세스](Process)의 Heap영역과 별개이다.

class area에 올라온 클래스들만 객체로 생성

![](https://i.imgur.com/0JbT8hr.png)

## 구성
- Permanent Generation
   Class, Method 등에 대한 Meta 정보가 저장되는 영역. JVM에 의해 사용됨
   [Reflection](Reflection)을 사용하여 동적으로 클래스가 로딩되는 경우 사용
   내부적으로 [Reflection](Reflection) 기능을 자주 사용하는 Spring을 이용하면 이 영역에 대한 고려가 필요함
- New/Young
	- Eden : 객체들이 최초로 생성되는 공간
	- Survivor 0/1 : Eden이 참조되는 객체들이 저장되는 공간
- Old
   New Area에서 일정 시간 참조되고 있는 살아남은 객체들이 저장되는 공간 Eden 영역에 객체가 가득차게 되면 첫번째 GC 발생