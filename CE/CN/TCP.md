# Transmission Control [Protocol](Protocol)
전송 제어 프로토콜

인터넷 상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜
IP가 데이터 배달을 처리한다면 TCP는 패킷을 추적 및 관리함

- 연결형 서비스, 가상 회선 방식
    - 발신지와 수신지를 연결하여 패킷을 전송하기 위한 논리적 회로를 배정
    - 연결 : 3-way handshaking / 해제 : 4-way handshaking
- 흐름제어, 혼잡제어 → UDP보다 속도 느림
- 높은 신뢰성 보장 ← 연결형 서비스
- 파일 전송

타이머는 Retransmission, Persistence, Time waited, Keep alive가 있다.

- Flow Control : 송신과 수신 측의 데이터 처리 속도 차이를 해결해줌
- Congestion Control :  수신 측으로 유입되는 트래픽 양이 대역폭을 넘어가지 않게 제어