# Validation 검증

두가지 분야에서 Validation이 등장한다.

## 테스트에서

실제 제품을 검사하고 테스트하는 동적인 과정, [Verification](Verification)과 비교된다.

참고 : [V&V](V&V)

- 단위 테스트
- 통합 테스트
- 시스템 테스트
- 인수 테스트
- 설치 테스트

## 개발에서 

올바르지 않은 데이터를 걸러내어 보안을 유지하기 위한 데이터 검증

서버 API구성의 기본은 Validation을 잘 처리하는 것.

외부에서 어떤 값을 날리든 Validation을 잘 처리하여 서버가 터지는 일이 없도록 유의하자. 

값, 형식, 길이 등의 형식적 Validation은 Controller에서, 

DB에서 검증해야 하는 의미적 Validation은 Provider 혹은 Service에서 처리하면 된다.


