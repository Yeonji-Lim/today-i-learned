# Kafka [Pub/Sub Model](Pub_Sub)
topic에 이벤트를 보내고
이벤트는 topic의 각 partition에 분산되어 저장

![](https://i.imgur.com/R7nAnix.png)
topic을 구독하고 있는 consumer group내의 consumer는 각각 1개 이상의 partition으로부터 이벤트를 가져온다.

partition개수보다 consumer 개수가 많다면 아무일도 하지 않는 consumer가 생기기 때문에 항상 partition 수를 consumer보다 같거나 크게 해주는 것이 좋다.

우체통 같은 것이라고 생각하자
producer가 consumer 1에게 보내려고 보낸 메시지가 같은 consumer group 내의 다른 consumer가 소모할 수 도 있다. 이때는 consumer1은 메시지 존재조차 모름