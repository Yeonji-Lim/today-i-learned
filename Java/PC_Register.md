# [JVM](JVM)의 PC Register
[Thread](Thread)가 생성될 때마다 생기는 공간으로 
이 쓰레드가 어떤 명령을 실행하게 될지에 대한 부분을 기록

JVM은 Stack-Base 방식으로 작동하는데, JVM은 CPU에 직접 Instruction을 수행하지 않고, 스택에서 Operand를 뽑아내서 이를 별도의 메모리 공간에 저장함 이 메모리 공간을 PC Register라고 함