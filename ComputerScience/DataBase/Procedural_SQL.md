# 절차형(Procedural) SQL

## 특징
- [DBMS](DBMS.md) 엔진에서 직접 실행
- 각 기능 별 모듈화 가능 : BEGIN/END의 Block화된 구조
- 연속적인 작업 처리에 적합 : 조건문, 반복문 등 단일 SQL 문장으로 처리하기 힘든 작업
- 일반적으로 Input/Output Packet이 적음 : DBMS 내부에서 직접 처리
- 타 절차형 언어에 비해 작업의 효율성이 낮음
- 벤더별 차이 때문에 이식시 수정, 재컴파일이 필요함