# Pipeline
하나의 처리 과정([Process](Process.md))을 여러 세부 처리 과정(Subprocess)으로 나누어 처리하는 기법

각 Subprocess는 동시에 다른 데이터를 취급한다.

Segment간 데이터 이동은 레지스터를 통해 이루어진다.

## 설계와 구현
실제 구현에서 각 세그먼트의 수행 속도가 서로 다르다. 대표적인 설계로 산술 파이프라인과 명령어 파이프라인이 있다.
수행시간이 가장 늦는 세그먼트로 인해 레지스터 전송에 싱크를 맞추어야 한다 

명령어 파이프라인의 경우 분기가 발생했을 때 파이프라인을 모두 비우고 분기 이후의 명령어들은 모두 무시되어야 한다.

## 연산 용어
- k : 파이프 라인 단계, 세그먼트
- n : taks 수, 실행 명령어 수
- T : 소요되는 클럭 사이클 수, 명령어 실행시간

## 정상 동작을 방해하는 것
- Resource Conflict
- Data Dependency
- Branch Difficulty
- 