# Lambda
익명 함수, Anonymous functions -> [일급 객체](First-class_Citizen)의 특징

이름을 가질 필요가 없다.

## 특징
### 장점
- 코드의 간결성
	- 불필요한 반복문 삭제
	- 복잡식 -> 단순식
- 지연 연산 수행
	- 불필요한 연산 최소화
- 병렬처리, 멀티쓰레딩

### 단점
- 호출이 까다롭
- [Stream](Java/Stream.md)사용 시 단순 for, while보다 성능이 떨어짐
- 가독성 안좋음

## 표현식
- `->` 함수 몸체 사용
- 단일 실행 문이면 `{}` 생략
- return으로면 구성되어 있으면 `{}` 생략 불가

- [함수형 인터페이스](Functional_Interface)로만 사용 가능