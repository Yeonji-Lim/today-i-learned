# JVM Execution Engine
Class Loader에 의해 JVM으로 Load된 Class 파일(바이트 모드) 들은 [Runtime Data Area](Runtime_Data_Area.md)의 Method Area에 배치되는데, 

JVM은 Method Area의 바이트코드를 Execution Engine에 제공.
Class에 정의된 내용대로 바이트코드 실행

## 실행 방식

바이트코드를 명령어 단위를 읽어서 실행. 두가지 방식 혼합 사용

1. [Interpreter](Interpreter) 방식
   바이트코드를 한줄 씩 실행. 초기 방식 -> 속도가 느리다. 
2. [JIT(Just In Time) 컴파일 방식](JIT_Compile) 또는 동적 번역(Dynamic Translation)
   그런데 바이트코드를 Native Code로 변환하는 것은 오래 걸림
   모든 코드를 JIT 컴파일러 방식으로 실행하지 않고 인터프리터 방식을 사용하다 일정 기준이 넘어가면 JIT 컴파일 방식으로 명령어 실행