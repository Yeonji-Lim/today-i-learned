
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

하루를 기다렸는데, 안돌아가고 컴퓨터가 살짝 맛이 가려해서 데스크톱으로 옮겼다

이번에는 window의 vmware에서의 kali linux다.
​

그런데 원래대로 하려고 하니, john password.txt에서 패스워드 해시가 로드되지 않았다고 한다..

이상하네.. 맥에서는 되었는데 뭐가 문제인지 모르겠다.

그래서 일단은 계정을 지워주기 위해서 deluser를 했다.


adduser useradd가 있고 deluser userdel이 있다는데, 

adduser로 해서 그러는지 sudo deluser하니까 계정이 잘 지워졌다.
​

그리고 useradd 로 다시 계정을 만들었다.

알아보니까 홈디렉토리가 생성되느냐 안되느냐의 차이라고 한다. 


어제는 이거 안돼서 adduser 했던건데 갑자기 잘된다?

아마도 kali로 한것과 root로 한것의 차이가 아닐까 생각한다. 

​

그리고 나서 패스워드를 passwd로 설정해주었다. 


전처럼 뭔가 길게 안나오고 그냥 패스워드 입력 부분만 간단하게 나오는 것을 볼 수 있다.

그리고 다시 다음과 같이 입력

~~~
unshadow /etc/passwd etc/shadow | egrep '(^user.)' > password.txt
~~~

그리고 나서 john password.txt를 시도해봤는데 안된다..


패스워드를 이미 한번 크랙하고 나면 이렇게 된다고 하는데,, 나는 처음부터 떴는데,,?

일단 한번 해결 방법을 따라 시도해본다.


.pot파일을 지워주라고 하는데 나랑 뭔가 구조가 다른 것 같아서 좀 겁먹은 상태로 일단은 최대한 파일들을 뒤져봤다.

그렇게 찾아 보다가 결국 pot으로 끝나는 파일은 찾을 수가 없었다.
​

그러다가 unshadow할 때 /를 etc/shadow에 안붙이고 /위치에서 진행했는데 이번에는 /etc/shadow로 etc/위치에서 진행했다.

그래도 여전히 같은 오류로 안됐다.


tail etc/shadow로 확인해 봤는데 password.txt 파일에서 본 것과 비슷한 내용이 잘 확인이 된다.


... 이쯤에서 그냥 john의 GUI인 johnny를 쓰기로 했다.

kali linux에 johnny를 설치해준다.

~~~
sudo apt-get update
sudo apt-get install johnny
~~~

그리고 johnny 어플리케이션을 실행시키고 

좌측상단의 Open password file로 아까 만든 password.txt를 열었다.

아.. 실행이 안되고 log 확인해보라길래 왼쪽 아래에 있는 Console log를 들어가보니.. 아까와 같은 내용이 찍혀있었다.

그래서 이번에는 이렇게 해서 shadowfile을 만들고 이 파일을 열어보았다.

그래도 같은 이유로 동작이 안되었다.


애증의 존더리퍼 맥에서도 되는거였다...

그것도 모르고 리눅스에서 안돼서 윈도우로 넘어가려 함

아무튼 다음과 같이 설치한다.

~~~
git clone "https://github.com/magnumripper/JohnTheRipper.git" && cd JohnTheRipper/src && ./configure && sudo make -s clean && sudo make -sj4
~~~
살펴 보니 뭔가 구조가 다른 듯 해서  brew 로 한번 설치해본다.

~~~
brew install john
cd /usr/local/share
ln -s /usr/local/Cellar/john/1.9.0/libexec john
cd john
cp john.ini john.conf
~~~

그런데 이때 john.ini는 없고 john.conf만 있었다.

그래도 일단 cd로 나가서 john을 실행해보니 잘 실행

그런데 실제로 john에 들어가보니.. 아무것도 없었다...;

일단 해시 파일을 만들기 위해서 /usr/etc에 들어갔는데 passwd는 있는데 shadow는 없었다.

알아보니 맥은 etc/passwd etc/shadow를 지원하지 않는다고 한다.

대신 dscl을 이용할 수 있다.

...
