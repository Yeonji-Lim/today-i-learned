# Paging
크기가 동일한 [[Page]], 가상 주소 공간([[Virtual_Memory]])과 이에 매칭하는 물리 주소 공간을 관리

하드 웨어의 지원이 필요함

리눅스에서는 4KB로 페이징

페이지 번호를 기반으로 가상 주소/물리 주소 매핑 정보를 기록/사용

# Paging System
[[Process]]의 [[PCB]]에 Page Table 구조체를 가리키는 주소가 들어있음
Page Table에는 가상 주소와 물리 주소간 매핑 주소가 있음 

## CR3
page에 사용되는 레지스터
Page-Directory Base (다른 말로 Page Directory의 PFN(Page Frame Number)라고 함)에 CR3가 가르키는 Page Directory의 주소가 저장되어 있음

CR3에 의해 각각의 프로세스가 독립적인 메모리 주소 공간을 가질 수 있다.
-> 그래서 운영체제에서 CR3의 역할이 중요

Process Switching이 일어날 때 Process는 메모리 페이지를 변경해야 함
연산해야하는 대상이 변경되기 때문에 연산 대상이 변경되어지면 당연히 연산 대상의 데이터도 변경되어야 하기 때문

## TLB
Translation Lookaside Buffer
페이지 테이블의 캐시, 일종의 주소 변환 캐시

### 발생 이유 
-> #모름
모든 가상 메모리 참조는 두 번의 메모리 참조를 수반함 
해당 페이지 테이블 항목 참조 / 요구된 데이터 접근을 위한 참조

## Demand(ed) Paging 요구 페이징
프로세스 모든 데이터를 메모리로 적재하지 않고, 실행 중 필요한 시점에서만 메모리로 적재함 

<-> 선행 페이징 (Anticipatory Paging or prepaging)

## Page Fault
어떤 페이지가 실제 물리 페이지에 없을 때 일어나는 [[Interrupt]]

page fault가 일어나면 운영체제가 해당 페이지를 물리 메모리에 올림