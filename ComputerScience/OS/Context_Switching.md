# Context Switching

[cpu](CPU)에 실행할 [[Context]]를 교체하는 기술

[프로세스](Process)의 경우 기존에 실행되던 프로세스를 중단하고 다른 프로세스를 실행하는 것을 말한다

process context switching은 [[PCB]]를 사용해서 동작한다.

# Context Switching의 동작

A라는 프로세스가 running 상태이고 B라는 프로세스가 ready 상태라고 할 때

1. 스케줄러가 A를 중단하고 B를 실행할 것을 요청

2. CPU는 다음 프로세스의 정보를 불러오기 위해 [메모리](Memory) 검색
   
3. CPU 캐시 메모리 초기화
   - 현재 캐시는 지금 프로세스의 캐시이기 때문
   - 민감한 데이터일 수 있으니 보안 측면
   - 현재 메모리의 내용을 반영하여 일관성을 유지, 데이터 불일치와 관련된 문제를 방지하고, 프로세스 간에 예상치 못한 동작이 발생하는 것을 방지
     
4. A프로세스에서 SP값과 PC값을 PCB에 저장
   - SP([Stack Pointer](Stack_Pointer)) : 스택의 데이터 위치를 가리킴
   - PC([Program Counter](Program_Counter)) : 다음에 실행할 코드의 위치값을 가짐
 
5. A는 ready 또는 block 상태로, CPU에서 B 실행
   - dispatch가 일어남 : B는 ready에서 running 상태로

6. 다시 A로 돌아갈 경우 현재 SP값과 PC값을 담은 PCB를 저장, A의 PCB를 찾아서 SP값과 PC값을 덮어씀

