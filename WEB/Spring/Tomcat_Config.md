https://memo-the-day.tistory.com/126 
# Spring Boot Tomcat을 구성하는 방법
[application.properties](application.yml_or_properties)를 수정하여 Spring Boot 웹 애플리케이션에 있는 기본적으로 사전 구성된 임베디드 Tomcat의 구성을 수정할 수 있다.

## 서버 주소 및 포트
```properties
server.address=my_custom_ip
server.port=80
```

서버 주소 default 값은 _0.0.0.0_ 으로 모든 IPv4 주소를 통한 연결을 허용함
포트는 기본적 으로 _8080_ 으로 설정
