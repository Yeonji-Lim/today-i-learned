# 데이터 무결성
완전한 수명 주기를 거치며 데이터의 정확성과 일관성을 유지하고 보증하는 것
데이터베이스나 RDBMS 시스템의 중요한 기능

일반적으로 무결성 제한이나 규칙에 의해 데이터 베이스 시스템이 강제한다.
관계형 데이터 모델의 기본 기능

## 종류
### 개체 무결성([Entity](Entity) Integrity)
고유 키(유일 키)의 개념과 관련됨

- 모든 테이블이 기본 키를 가져야 한다. 
- 기본 키로 선택된 열울 고유해야 한다. 
- 기본 키는 빈 값이어서는 안된다.

### 참조 무결성(Referential Integrity)
외래 키(외부 키)의 개념과 관련됨 
- 모든 외래 키 값은 두 가지 상태 가운데 하나에만 속한다.
- 일반적인 상태는 외래 키 값이 데이터베이스의 특정 테이블의 기본 키 값을 참조하는 것
	-> 비즈니스 규칙에 따라 달라질 수도 있고 외래키 값은 빈 값을 허용함

### 범위 무결성([Domain](Domain) Integrity)
정의된 범위에서 관계형 데이터베이스의 모든 열이 선언되어야 한다.