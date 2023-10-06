# AAA 패턴
테스트 코드를 아래 3단계 순서로 구분한다.

- Arrange : 테스트를 실행하기 전에 필요한 것들을 준비 
	
	(ex : Mock 객체 생성, 테스트 전에 호출되어야 할 API 호출)
	
- Act : 테스트 코드 실행, 우리가 보고자하는 행동
	
	이 행동은 [SUT](SUT.md)의 상태를 바꾼다. 
	
- Assert : 실행한 코드가 예상대로 동작했는지 확인 ex : assertTrue(), assertThat()

pytest 공식문서에서는 테스트 과정에서 위 과정과 함께 cleanup과정도 포함하였다.

- Cleanup : 다른 테스트들이 해당 테스트의 영향을 받지 않도록 원상복구 시키는 작업