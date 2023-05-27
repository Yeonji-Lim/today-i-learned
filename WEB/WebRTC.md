# Web Real-Time Communication
브라우저와 서버가 통신 x

브라우저끼리 통신하여 중간자인 서버없이 브라우저 간에 오디오, 영상 미디어, 데이터 등을 교환할 수 있도록 하는 기술

[websocket](websocket)에 비해 
- 영상, 오디오, 임의의 데이터의 통신이 high-performance, hight-quality 이도록 설계되었다.
- 브라우저간 직접 통신이어서 훨씬 빠르다
- 지연시간이 훨씬 짧다(low-latency)

WebRTC도 websocket을 사용한다.

P2P 연결인데 심각한 부하를 다룰 수 있기 때문에, websocket또는 socket.io를 사용하여 Signaling서버는 필요하다.

## Signaling 서버가 필요한 이유
시그널링 : 서로 다른 네트워크에 있는 클라이언트가 상대방의 IP, 미디어 유형, 코덱 등을 초기화하는 과정

상대방의 주소를 알지 못한다면 P2P 통신이 불가능하다. 

상대방의 주소를 어딘가로부터 전달받아야 한다. : 시그널링 서버

시그널링 서버
- Peer 주소 알려줌
- 접속 정보 전달
- 영상 코덱 정보 전달

-> 클라이언트와 시그널링 서버 사이에 양방향 통신을 실시간으로 해야함 

-> 일반적으로 클라이언트와 시그널링서버의 통신은 WebSocket으로 구축함

하지만 명확한 가이드가 없다. : websocket이 아니라 Polling, SSE로 구현한 사례도 있음

## STUN, TURN

NAT 환경에서는 각 Peer에 대해 직접적인 시그널링이 불가능함
![](https://i.imgur.com/xc89adc.png)

먼가가 뚫어주어야 함 : UDP Hole Punching

그래서 STUN, TURN 서버가 필요하다

### STUN
Session Traversal Uilities for NAT
> 클라이언트가 자신의 공인 IP 주소와 포트를 확인하는 과정에 대한 프로토콜, 사설 주소와 공인 주소를 바인딩

클라이언트가 NAT 환경에 있는 경우 Public 종단에서 접근 가능한 IP와 Port를 판단해서 알려줌

1. 클라이언트는 자신의 Public IP를 확인하기 위해 STUN 서버로 요청해서 받음
2. 자신이 받은 Public IP를 이용하여 시그널링을 할때 받은 그 정보를 이용해서 시그널링

- 두 Client가 같은 네트워크에 존재하고 있을때는 이것으로는 해결이 되지 않음
- Symmetirc NAT의 경우는 어플리케이션이 달라지면 NAT의 매핑테이블이 바뀔 수 있음
-> TURN 서버 필요

> Symmetirc NAT : 접속하는 서버에 따라 외부 포트가 달라짐

### TURN
> 클라이언트가 패킷을 릴레이 시켜줄 서버를 확인하는 과정에 대한 프로토콜, 릴레이 주소(TURN 서버의 IP주소와 포트 넘버)를 할당한다. ICE에서 직접 사용한다.

클라이언트들이 통신할 때 Public 망에 존재하는 TURN 서버를 경유하여 통신

미디어 데이터를 대신 전달 : 서버 리소스 소모

1. 자신의 Private IP가 포함된 TURN 메세지를 TURN 서버로
2. TURN 서버는 메세지에 포함된 Network Layer IP 주소와 Transport Layer의 UDP 포트 넘버와의 차이를 확인하고 클라이언트의 Public IP로 응답
3. NAT는 NAT 매핑테이블에 기록되어 있는 정보에 따라서 내부 네트워크에 있는 클라이언트의 Private IP 로 메세지를 전송

TURN 서버는 ICE의 일부로 사용될 수 있도록 디자인됨

릴레이 역할을 하는 서버의 공인 주소를 할당하는 역할을 한다.

대규모 전개가 아니면 보통 릴레이서버 == 턴서버

## webRTC를 활용한 원격 게임

![](https://i.imgur.com/nkyCpmm.png)

![](https://i.imgur.com/qufxdtq.png)

![](https://i.imgur.com/UcDbVrR.png)

![](https://i.imgur.com/6mUnIc4.png)

![](https://i.imgur.com/2psWHo9.png)

![](https://i.imgur.com/zd7oOhT.png)


# 참고
https://brunch.co.kr/@linecard/156
https://www.youtube.com/watch?v=8jryUH6xmjU&ab_channel=kakaotech