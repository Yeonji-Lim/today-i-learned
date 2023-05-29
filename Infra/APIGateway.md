# API Gateway
서비스로 전달되는 모든 API 요청의 관문(Gateway)역할을 하는 서버

API Gateway : 시스템의 아키텍처를 내부로 숨기고 외부의 요청에 대한 응답만을 적합한 형태로 응답한다. 

-> 이에 따라 클라이언트는 시스템 내부의 아키텍처자 마이크로 서비스 형태인지 아닌지 알 필요가 없다.

요청을 받으면 응답 정보를 하나의 응답으로 취합하여 클라이언트에 다시 전달

## 역할
- 요청 일괄 처리
- 전체 시스템 부하를 분산 : 로드 밸런서 역할
- 동일한 요청에 대한 불필요한 반복작업을 줄이는 캐싱
- 시스템상을 오가는 요청과 응답에 대한 모니터링 가능

모든 요청이 병렬로 처리될 수도 있다.