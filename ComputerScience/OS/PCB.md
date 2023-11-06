# PCB
PCB는 [Process](Process.md) Context/Control Block의 약자로, 프로세스가 실행중인 상태를 스냅샷으로 찍어서 보관하는 공간이다.

다음과 같은 내용이 저장된다.

- Process ID
- 레지스터 값
- scheduling Info
- Memory Info
- 기타

컨텍스트 스위칭은 기존에 실행되던 프로세스에 대한 pcb 정보를 메인 [메모리](Memory)에 저장하고 실행할 프로세스에 대한 pcb 정보를 메인 메모리에서 로드하는 방식으로 동작한다.