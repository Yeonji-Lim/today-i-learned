# 중앙집 중식 로깅 시스템

## 배경
MSA에서는 각 서비스의 로그 파일이 분산되어있다.
이 때문에 트랜잭션을 처음부터 끝까지 추적하는 것이 불가능해진다. 

로그의 출처와 상관없이 모든 로그를 중앙 집중적으로 저장, 분석해야 한다.
서비스 실행 환경에서 분리하여 관리한다.

![](https://i.imgur.com/14Ci94d.png)
출처 : https://sonnson.tistory.com/27

- 로그 스트림 : 각 서비스에서 로그 메시지 만드는 것. Log4j, DB로그, Network 로그 등
- 로그 적재기 : 로그 메시지 수집 및 다른 종단점으로 보내기. Logstash, Fluentd, Logspout
- 로그 스트림 처리기 : 신속한 의사 결정에 필요한 실시간 로그 이벤트 분석. 알람 공지 및 대시보드로 정보 전송. kafka, apache flume, spark streaming, storm
- 로그 저장소 : 모든 로그 메시지를 인덱싱하여 검색 가능한 형식으로 저장. ElasticSearch(실시간 로그 저장), HDFS, MongoDB,..
- 로그 대시보드 : 로그 분석 결과 표현, 운영 및 관리 조직에서 사용. Kibana, Graphite, Grafana
