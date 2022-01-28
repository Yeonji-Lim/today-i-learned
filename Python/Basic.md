## list안에 이중 for문이 있을 때 앞의 for문이 더 큰 for문

~~~
for i in v: 
    for j in i: 
        if i > 4:
            print(j) 

[j for i in v for j in i if i > 4]
~~~

위와 아래는 같은 의미

##

__name__  : 모듈의 이름이 저장되는 변수

__file__ : 현재 실행되고 있는 파일의 경로가 저장되는 변수

## python list slicing

## python with문

자원을 획득 -> 사용 -> 반납 하는 형식으로 동작한다.

~~~
with EXPR as VAR:
    BLOCK
~~~