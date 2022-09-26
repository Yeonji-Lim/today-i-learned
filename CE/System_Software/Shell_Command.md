# 쉘 명령어

## 권한 chmod
### 파일 권한 숫자 표기 법
![[chmod.png]]

사용자와 그룹에게 읽기, 쓰기 권한을 추가
```shell
chmod ug+rw fast.c
```

Chromedriver 파일에 소유자 읽기 권한을 제외한 모든 권한 삭제
```shell
chmod 
```

## 파일 관리
해당 디렉토리 내에 모든 '파일' 삭제
```shell
rm -r
```

## 내용 복사 저장
a.txt의 마지막 10라인을 b.txt에 저장
```shell
tail < a.txt > b.txt
```

## Foreground Process 실행 중지
`CTRL + Z`

## Background Process
실행 : 실행 명령 뒤에 `&`를 붙인다.
종료 : `kill -9 [pid]`

## 프로세스
```shell
ps
```

시스템이 사용하고 있는 모든 프로세스의 상태를 확인
```shell
ps -a
```
