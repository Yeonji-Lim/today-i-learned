# Elasticsearch
Apache Lucene(루씬) 기반의 Java 오픈소스 분산 검색 엔진

루씬 라이브러리를 단독으로 사용 가능

방대한 양의 데이터를 신속하게 거의 실시간 (Near Real Time, NRT)으로 저장, 검색, 분석할 수 있음

검색을 위해 단독으로 사용되기도 하고, 

ELK( Elasticsearch / [Logstatsh](Logstatsh) / [Kibana](Kibana) )스택으로 사용되기도 함

## 관계형 DB와 비교

![](https://i.imgur.com/YTw18vb.png)
![](https://i.imgur.com/HJ4IJOv.png)

(출처: https://www.slideshare.net/deview/2d1elasticsearch)

## 아키텍처

![](https://i.imgur.com/YmpOpcL.png)
(출처 : https://github.com/exo-archives/exo-es-search)

### Cluster
Elasticsearch에서 가장 큰 시스템 단위

최소 하나 이상의 노드로 이루어짐

서로 다른 클러스터는 데이터의 접근, 교환을 할 수 없는 독립적인 시스템

- 여러 대의 서버가 하나의 클러스터를 구성하거나
- 한 서버에 여러 개의 클러스터 존재

### node
하나의 단위 프로세스

역할에 따라 Master-eligible, Data, Ingest, Tribe 노드

종류 잘 #모름 

#### Master-eligible
클러스터를 제어하는 마스터 노드

-   인덱스 생성, 삭제
-   클러스더 노드들의 추적, 관리
-   데이터 입력 시 어느 샤드에 할당할 것인지

#### Data
CRUD 작엄과 관련

CPU, 메모리 등 자원을 많이 소모하므로 모니터링이 필요

마스터 노드와 분리되는 편이 좋음

#### Ingest
데이터를 변환하는 등의 사전 처리 파이프라인 실행

#### Coordination only node
data node와 master-eligible node의 일을 대신

대규모 클러스터에서 이점

로드 밸런서와 비슷한 역할