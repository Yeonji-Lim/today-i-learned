# Web Real-Time Communication
브라우저와 서버가 통신 x

브라우저끼리 통신하여 중간자인 서버없이 브라우저 간에 오디오, 영상 미디어, 데이터 등을 교환할 수 있도록 하는 기술

[websocket](websocket)에 비해 
- 영상, 오디오, 임의의 데이터의 통신이 high-performance, hight-quality 이도록 설계되었다.
- 브라우저간 직접 통신이어서 훨씬 빠르다
- 지연시간이 훨씬 짧다(low-latency)

WebRTC도 websocket을 사용한다.

P2P 연결인데 심각한 부하를 다룰 수 있기 때문에, websocket또는 socket.io를 사용하여 Signaling서버는 필요하다.

## STUN, TURN

NAT 환경에서는 각 Peer에 대해 직접적인 시그널링이 불가능함
![](https://i.imgur.com/xc89adc.png)

먼가가 뚫어주어야 함 : UDP Hole Punching

그래서 STUN, TURN 서버가 필요하다

### STUN
Session Traversal Uilities for NAT

1. 클라이언트는 자신의 Public IP를 확인하기 위해 STUN 서버로 요청해서 받음
2. 자신이 받은 Public IP를 이용하여 시그널링을 할때 받은 그 정보를 이용해서 시그널링

- 두 Client가 같은 네트워크에 존재하고 있을때는 이것으로는 해결이 되지 않음
- Symmetirc NAT의 경우는 어플리케이션이 달라지면 NAT의 매핑테이블이 바뀔 수 있음

> Symmetirc NAT : 접속하는 서버에 따라 외부 포트가 달라짐

### TURN
클라이언트들이 통신할 때 Public 망에 존재하는 TURN 서버를 경유하여 통신

1. 자신의 Private IP가 포함된 TURN 메세지를 턴서버로
2. TURN 서버는 메세지에 포함된 Network Layer IP 주소와 Transport Layer의 UDP 포트 넘버와의 차이를 확인하고 클라이언트의 Public IP로 응답
3. NAT는 NAT 매핑테이블에 기록되어 있는 정보에 따라서 내부 네트워크에 있는 클라이언트의 Private IP 로 메세지를 전송

TURN 서버는 ICE의 일부로 사용될 수 있도록 디자인됨