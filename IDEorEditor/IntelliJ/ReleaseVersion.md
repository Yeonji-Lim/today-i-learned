# java: warning: source release 11 requires target release 11

이런 오류는 어딘가 자바 버전이 맞지 않는 것

1. build gradle

~~~
sourceCompatibility = '11'
~~~

2. File > Project Structure > Project 확인

3. File > Project Structure > SDKs 확인