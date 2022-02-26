## '/etc/profile' E212：Can't open file for writing 에러

수정하려고 했더니 생긴 에러,, sudo vi로 다시 들어가거나 저장할 때 다음과 같이 입력해서 저장하자

~~~
:w !sudo tee % > /dev/null
~~~

## Found a swap file by the name ".zshrc.swp"

vi를 비정상으로 종료했을 때 나오는 메시지다. 해당하는 스왑파일(.swp)을 없애주자

~~~
$ rm -f ~/.zshrc.swp
~~~