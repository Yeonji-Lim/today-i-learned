## '/etc/profile' E212：Can't open file for writing 에러

수정하려고 했더니 생긴 에러,, sudo vi로 다시 들어가거나 저장할 때 다음과 같이 입력해서 저장하자

~~~
:w !sudo tee % > /dev/null
~~~
