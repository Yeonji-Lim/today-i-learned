
# 패스워드 크래킹(Password Cracking)

컴퓨터 시스템에 저장된 데이터 혹은 네트워크 상에서 전송되는 데이터를 이용하여 암호를 복원하는 기술


목적은 다음의 3가지 이다.

1. 암호를 잃어버린 사용자를 위해 암호를 복구

2. 시스템에 허가되지 않은 접속을 하는 것

3. 관리자가 자신이 설정한 암호가 풀기 쉬운 지 체크


암호를 푸는데 걸리는 시간은 암호 강도(password strength)에 관련된다.


대부분의 패스워드 크래킹 기법은 다수의 후보 암호를 생성하여 이를 크래킹한다.

대표적으로 brute-force cracking은 가장 기본적인 방법으로, 가능한 모든 후보 암호를 생성, 성공할 때까지 다 시도해본다.

이러한 시도를 줄이기 위해서 dictionary attacks, pattern checking, word list substitution 등과 같은 방법을 사용한다.


패스워드 크래킹 프로그램의 능력 척도 : 1초에 체크할 수 있는 암호의 수


# John the Ripper

패스워드 강도를 테스트하는 윤리적 해커에게 유용한 도구.

단일보드, 사전, 단어 목록 모드와 같이 여러 종류의 크래킹을 수행한다.


처음해보는 패스워트 트래킹..

먼저 존더리퍼가 미리 깔려 있는 칼리 리눅스를 설치해주고 cd를 통해서 들어가주었다.

~~~
$ cd /etc/john
~~~
그리고 adduser로 user를 추가해주자

~~~
$ adduser user1
~~~

~~~
adduser: Only root may add a user or group to the system.
~~~
보니까 루트 계정이 아니라 kali 계정으로 하고 있었다. 일단 sudo로 설정

그리고 passwd로 비밀 번호를 설정할 예정이었는데,

바로 비밀번호 설정창이 나왔다.

처음 [sudo]에만 kali 비밀번호를 입력해주고 New password에서 user1의 비밀번호를 설정해준다.

만약에 이때 잘못 설정했다면 다음 명령어로 설정할 수 있다.

~~~
$ sudo passwd user1
~~~

이런 식으로 user1, user2, user3을 추가하였다.

그리고 나서 존더리퍼를 실행하려고 하는데, 다음 명령어로는 안됐다.

~~~
$ ./john/etc/shadow
~~~

해당하는 놈이 존재하지 않는다.

etc에 shadow가 있어서 그걸 실행해보려고 했지만 허가가 안되고 sudo를 써도 마찬가지.


결국 root 계정으로 바꿨다. 생각보다 루트 계정 전환은 쉬웠다.

~~~
$ sudo su
~~~
진짜 간단

그런데 여전히 안된다.

일단 password.txt에 user들과 그 비밀번호 정보를 저장한다.

~~~
# unshadow /etc/passwd etc/shadow | egrep '(^user.)' > password.txt
~~~

그리고 나서 다음 명령어를 이용해서 크랙할 수 있다!

~~~
# john password.txt
~~~

상당히 오래 걸릴 것 같은 조짐이 보인다

그리고 john으로 실행 시킨 후, adduser가 아니라 useradd를 하는 방법도 있는데,

지금 내가 추가한 것과 결국 같은 방법이다.
