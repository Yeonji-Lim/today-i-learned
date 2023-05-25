# Web Real-Time Communication
브라우저와 서버가 통신 x

브라우저끼리 통신하여 중간자인 서버없이 브라우저 간에 오디오, 영상 미디어, 데이터 등을 교환할 수 있도록 하는 기술

[websocket](websocket)에 비해 
- 영상, 오디오, 임의의 데이터의 통신이 high-performance, hight-quality 이도록 설계되었다.
- 브라우저간 직접 통신이어서 훨씬 빠르다
- 지연시간이 훨씬 짧다(low-latency)

WebRTC도 websocket을 사용한다.

P2P 연결인데 심각한 부하를 다룰 수 있기 때문에, websocket또는 socket.io를 사용하여 Signaling서버는 필요하다.


