# 멀티 프로세스
- [멀티 스레드](Multi_Thread)와 함께, 한 어플리케이션에 대한 처리 방식이다.
- 하나의 응용 프로그램에 대해 동시에 여러개의 프로세스 실행할 수 있게 하는 기술
	- 부가적인 기능을 위해서 이러는 것
- 하나의 부모 프로세스가 여러개의 자식 프로세스 생성
	- 프로세스 생성 [시스템 콜](System_Call)
- 부모 자식 간에 통신은 가능, 하지만 독립적으로 실행됨
- 마치 브라우저의 탭들과 같다. (실제로 크롬 브라우저는 멀티 프로세스)

## 장점
- 안정성
	- 독립된 메모리 공간 -> 다른 프로세스에 영향 x
- 병렬성
	- 멀티 프로세서와 함게 각 프로세스를 병렬적 실행 -> 분산처리로 빠르게
	- 멀티 스레드도 이 장점 있음
- 시스템 확장성
	- 새로운 기능, 모듈 추가시 다른 프로세스에 영향을 주지 않음 -> 시스템 규모 확장이 쉽다.

## 단점

### [Context Switching](Context_Switching) [Overhead](Overhead)
[멀티 태스킹](Multi_Tasking) 구성에 핵심인 컨텍스트 스위칭 과정에서 성능 저하 가능
빈번한 컨텍스트 스위칭 -> 비용 오버헤드
(스레드 스위칭은 더 가벼움)

그레서 멀티 프로세스 환경에서는 컨텍스트 스위칭 오버헤드를 최소화하는 것이 중요함
- 프로세스 수를 적정하게 유지
- [I/O 바운드](IO_Bound) 작업이 많은 프로세스와 [CPU 바운드](CPU_Bound) 작업이 많은 프로세스를 분리하여 관리
- CPU 캐시를 효율적으로 활용하는 방법

### 자원 공유 비효율성
각 프로세스가 독립적인 메모리 공간 -> 메모리 사용량 증가

만일 각 프로세스 간에 자원 공유가 필요하다면 프로세스 사이의 어렵고 복잡한 통신 기법인 [IPC](IPC)를 사용해야 함

그런데 IPC 자체로 오버헤드 발생
- 파이프나 소켓 같은 기법은 데이터 복사, 버퍼링 과정에서 성능 저하 가능

또한 코드 복잡도 증가