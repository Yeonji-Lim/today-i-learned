# 쉘 명령어

## 권한 chmod

>**chmod \[OPTION\] \[MODE\] \[FILE\]**
>OPTION
>-v        : 모든 파일에 대해 모드가 적용되는 진단(diagnostic) 메시지 출력.
>-f        : 에러 메시지 출력하지 않음.
>-c        : 기존 파일 모드가 변경되는 경우만 진단(diagnostic) 메시지 출력.
>-R        : 지정한 모드를 파일과 디렉토리에 대해 재귀적으로(recursively) 적용.
>MODE
>파일에 적용할 모드(mode) 문자열 조합.
>  u,g,o,a : 소유자(u), 그룹(g), 그 외 사용자(o), 모든 사용자(a) 지정.
>  +,-,=   : 현재 모드에 권한 추가(+), 현재 모드에서 권한 제거(-), 현재 모드로 권한 지정(=)
>  r,w,x   : 읽기 권한(r), 쓰기 권한(w), 실행 권한(x)
>  X       : "디렉토리" 또는 "실행 권한(x)이 있는 파일"에 실행 권한(x) 적용.
>  s       : 실행 시 사용자 또는 그룹 ID 지정(s). "setuid", "setgid".
>  t       : 공유모드에서의 제한된 삭제 플래그를 나타내는 sticky(t) bit.
>  0~7     : 8진수(octet) 형식 모드 설정 값.

### 파일 권한 숫자 표기 법
![](https://i.imgur.com/q811juQ.png)

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
