# AAA 패턴
테스트 코드를 아래 3단계 순서로 구분한다.

- Arrange : 테스트를 실행하기 전에 필요한 것들을 준비 ex : Mock 객체 생성, 테스트 전에 호출되어야 할 API 호출
- Act : 테스트 코드 실행
- Assert : 실행한 코드가 예상대로 동작했는지 확인 ex : assertTrue(), assertThat()