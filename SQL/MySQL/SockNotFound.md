# ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

워크 밴치 커넥션 실패 -> 비번 틀렸을거라고 예상 -> 비번 변경을 위해 mysql -u root 시도 -> 이 에러

이런 과정을 거쳐 이 에러를 만나게 되었습니다.



자꾸 안된다 그래서 다지우고 다시 깔았는데도 똑같이 뜨더라구요



그런데 충격 진실..

https://stackoverflow.com/questions/15450091/error-2002-hy000-cant-connect-to-local-mysql-server-through-socket-tmp-mys

그냥 내가 터미널에서 mysql 명령어 사용 설정을 안한것..!

터미널에서 mysql 명령어를 사용하도록 하려면 다음의 명령어를 먼저 실행시켜야 하는..!

~~~
brew services start mysql
~~~

이렇게 뜨면서 mysql 명령어가 잘 먹힙니다.



그리고 나서 워크 밴치 들어가보니

안되던 커넥션이 아무 일 없었다는 듯이 잘 굴러가더군요 허허

어쩐지 비번을 그렇게 다채롭게 쓰는 사람이 아닌데 못맞추는게 이상했습니다.



아마 전에 삭제 후 다시 깔면서 이 설정을 안한 거 같아요

그냥 바로 쓸 수 있는 줄 알았는데 아니었네요 제가 예전에 해놓고 기억에서 지웠나봅니다.

## 221019..
또다시 이 문제에 걸렸고, 혹시나 싶어서 TIL에 검색한 결과 발견 ,, 다행히 같은 원인이었다.
기록의 중요성을 실감하고 있다.