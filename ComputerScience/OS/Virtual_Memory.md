# Virtual Memory
[메모리](Memory)가 물리 메모리보다 많아보이게 함
프로세스가 여러개라도 실제 특정 시점에 사용하는 메모리는 작다는 것에서 착안

저장 매체(SSD/HDD)에 프로세스를 위한 시스템 공간을 만드는 기능
프로세스간 공간 분리로, 프로세스 이슈가 전체 시스템에 영향을 주지 않을 수 있음

## Memory Management Unit (MMU)
[CPU](CPU)에 코드 실행시, 가상 주소 메모리 접근이 필요할 때, 해당 주소를 물리 주소값으로 변환해주는 하드웨어 장치

[[Page]] [[Paging_System]]
