## AWS 서버를 ssh로 접속하기

makemethink.tistory.com

이때 default region name은 처음에 설정한 지역을 보고 설정하면 된다.

## ssh pem key 설정

~~~
$ cd ~/.ssh
$ cp "[pem파일경로]" ./
~~~

이렇게 해주면 다음과 같이 접속가능

~~~
$ ssh -i "[pem파일명].pem" [계정명]@[host주소]
~~~

그런데 이때 사용하는 aws 인스턴스의 이미지에 따라 계정명이 달라지니 주의하도록 하자

## EC2로 프로젝트 배포하기

내 프로젝트는 톰캣으로 한거였기 때문에 설치..

파일질라가 필요함

