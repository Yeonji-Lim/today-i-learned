# ssl.SSLCertVerificationError

python requests 패키지를 사용한 파일을 ubuntu에서 실행했더니 위와 같은 에러가 발생했다.

http 요청을 보낼 때 ssl 인증없이 요청을 보낼 수 있도록 verify=false 조건을 넣어주어야 한다.