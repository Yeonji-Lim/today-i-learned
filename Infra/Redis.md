# Redis

[인메모리 데이터베이스](In-Memory_DB), 캐시 시스템

고성능 키-값 저장소로서 문자열, 리스트, 해시, 셋, 정렬된 셋 형식의 데이터를 지원하는 [NoSQL](NoSQL)

## 다양한 자료 구조
다른 인메모리 디비랑 가장 큰 차이점이 다양한 자료구조!

![](https://i.imgur.com/AhRisXq.png)
개발의 편의성이 좋아지고 난이도가 낮아진다는 장점

## 주요 특징
- 영속성을 지원하는 인메모리 데이터 저장소
- 읽기 성능 증대를 위한 서버 측 복제를 지원
- 쓰기 성능 증대를 위한 클라이언트 측 샤딩(Sharding) 지원
- 문자열, 리스트, 해시, 셋, 정렬된 셋과 같은 다양한 데이터형을 지원. 메모리 저장소임에도 불구하고 많은 데이터형을 지원하므로 다양한 기능을 구현

## [Redis Stream](Redis_Stream)

## Pub/Sub mechanism
