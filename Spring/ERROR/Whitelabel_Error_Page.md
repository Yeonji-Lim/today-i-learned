# Whitelabel Error Page

![[whitelabel_error_page.png]]
## 원인 및 해결책

실행시 이런 페이지가 나오는 경우 원인은 2가지이다.

### 1. localhost:8080 으로 연결 시 기본값인 index.html이 없다
스프링 구동시 처음에는 무조건 index.html을 찾도록 설정되어 있기 때문에 index.html이 없으면 에러가 발생한다.

### 2. 없는 파일을 경로로 지정하였다.
