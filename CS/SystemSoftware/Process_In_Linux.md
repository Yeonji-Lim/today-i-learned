# [Process](Process.md) in Linux

init Process는 Pid가 1이며, 운영체제에서 생성된다.

## Exec 계열 함수
현재 실행되고 있는 프로세스를 다른 프로세스로 대신하여 새로운 프로세스를 실행
새로운 프로세스의 main 함수부터 다시 시작

exec를 호출하는 코드에서 exec 뒤의 코드는 exec가 실패했을 때만 실행된다.

execve() 함수를 사용하면 환경 변수(Environment variable)을 임의로 설정할 수 있다.