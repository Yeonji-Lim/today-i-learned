# TCP and UDP
- [TCP](TCP) : 신뢰성이 높은 프로토콜
	- 내가 전달했다는 것이 보장되는 것, 상대방이 받았는지 확인할 수 있음
	- 연결을 맺고 끊는 3 way hand shake, 4 way handshake
	- 흐름제어
		- 받는 사람의 상황을 인지한 채로 보냄
		- 다 받았는지 확인하고 추가로 보낸다.
	- 혼잡제어
		- 몇개의 메시지만 전달이 되도록 한정
	- 1:1만 가능
- [UDP](UDP) : 빠른 프로토콜
	- 비연결형 : 보내고 끝이다. 손상된 데이터에 대해 재전송하지 않음
	- 1:1, 1:n, n:n 가능