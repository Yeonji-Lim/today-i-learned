# EC2로 jar파일 배포하기

## Region 확인하자! 서울로 되어 있는지
![](https://i.imgur.com/da4WRU6.png)

## 인스턴스 생성
![](https://i.imgur.com/tKZqQ60.png)

우분투, 프리티어 선택

## 키 페어 생성
![](https://i.imgur.com/9dLmxeA.png)

새 보안그룹으로 생성하자

## 접속하기
해당 인스턴스 > 연결 > 가장 마지막 명령 실행

## Java 설치

## FileZilla로 .jar 파일 전송

[참고 내용](FileZilla_EC2)

## jar 실행 권한 부여하기

권한 확인
```sh
ls -al
```

권한 부여가 안된 모습
![](https://i.imgur.com/Cmp99Yd.png)

권한 부여하기
```sh
sudo chmod +x [jar파일]
```

![](https://i.imgur.com/VZcoOdo.png)

## jar 파일 실행

```sh
sudo nohup java -jar [jar파일] &
```

nohup : 터미널 세션이 끊겨도 실행 유지
& : 백그라운드 실행

## 로그 보기

```sh
sudo cat nohup.out
```

## 실행중인 프로세스 목록 확인

```sh
ps -ef
```

-> 여기 중에서 내가 내린 명령어 확인
