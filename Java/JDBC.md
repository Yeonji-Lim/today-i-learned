# JDBC
JAVA에서 데이터베이스에 접속할 수 있도록 지원하는 JAVA API

데이터베이스 접근 후 삽입, 조회등의 처리를 지원

# DB Connect

[DB 접속](Connect_to_DB.md)

jdbc에서 db 접근시 url
```
jdbc:DB_VENDER://IP_ADDR:IP_PORT/INSTANCE
```
여기서 인스턴스는 db명

# DB 접근 과정
1. Driver 로드
2. Connection 객체 생성
3. Statement 객체 생성
4. 쿼리 실행
5. 결과 수행
6. 객체 연결 해제