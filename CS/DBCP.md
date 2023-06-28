# DataBase Connection Pool
JSP에서 DB 연결할 때 사용한 그 Connection에 대한 Pool 
- HTTP 요청에 따라 pool에서 connection객체를 가져다 쓰고 반환한다.
- 이와 같은 방식으로 물리적인 데이터베이스 connection(연결) 부하를 줄이고 연결 관리 한다.
- pool에 미리 connection이 생성되어 있기 때문에 connection을 생성하는 데 드는 요정 마다 연결 시간이 소비되지 않는다.
- 커넥션을 계속해서 재사용하기 때문에 생성되는 커넥션 수를 제한적으로 설정함