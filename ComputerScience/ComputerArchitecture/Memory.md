# 메모리

Code, Data, Heap, Stack으로 이루어져있다.
각각을 세그먼트라고 부르고
Code, Data는 정적 세그먼트, Heap, Stack은 동적 세그먼트임

![](https://i.imgur.com/p1jQGUI.png)

## Code

실행할 프로그램의 코드가 저장되는 영역
text 영역
프로그램이 시작하고 끝날 때까지 메모리에 계속 남아있음
컴파일된 기계어
CPU는 코드 영역에 있는 명령어를 하나씩 가져가서 처리함

## Data

전역(글로벌) 변수, 정적(스태틱) 변수, 문자열 상수

## Heap

런타임에 크기가 결정된다.
사용자의 동적할당

## Stack

컴파일 타임에 크기가 결정됨
지역 변수, 매개변수