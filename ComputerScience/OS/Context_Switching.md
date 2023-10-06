# Context Switching

cpu에 실행할 [[Context]]를 교체하는 기술

프로세스의 경우 기존에 실행되던 프로세스를 중단하고 다른 프로세스를 실행하는 것을 말한다

process context switching은 [[PCB]]를 사용해서 동작한다.

# Context Switching의 동작

A라는 프로세스가 running 상태이고 B라는 프로세스가 ready 상태라고 할 때

1. 스케줄러가 A를 중단하고 B를 실행할 것을 요청
   
2. A프로세스에서 SP값과 PC값을 PCB에 저장
   - SP(Stack Pointer) : 스택의 데이터 위치를 가리킴
   - PC(Program Cointer) : 다음에 실행할 코드의 위치값을 가짐
 
3. A는 ready 또는 block 상태로, CPU에서 B 실행
   - dispatch가 일어남 : B는 ready에서 running 상태로

4. 다시 A로 돌아갈 경우 현재 SP값과 PC값을 담은 PCB를 저장, A의 PCB를 찾아서 SP값과 PC값을 덮어씀

