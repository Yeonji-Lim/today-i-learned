# [ALB](ALB.md)와 [API 게이트웨이](API_Gateway)

## 공통점
클라이언트 요청을 적절한 서비스로 라우팅하는 역할

## 차이
상황과 제공 기능에 있어서 차이

### 상황
- 여러 서버 간의 부하 분산 : ALB
- 주로 MSA에서 사용 : API Gateway

### 차이
- API Gateway가 더 부가적인 기능을 제공함
	- 요청 유효성 검사, 인증 및 인가, 요청 및 응답 변환, 쿼터 및 제한 설정
