# Load Balancer
서버의 부하를 분산시켜주는 시스템

- L4
	- 4계층 까지의 정보를 가지고 분산
	- [MAC](MAC_Address)주소(2), [IP](IP)주소(3), [포트](Port)(4)
- L7
	- 7계층 까지의 정보를 가지고 분산
	- URL의 endpoint를 보고 나누어 분산 가능
	- 패킷을 열어서 확인 -> DDOS 방어 가능
		- 계속 요청을 보내는 것을 알아채고 막음

참고 : [OSI 7계층](OSI 7 Layer)