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

# python range()

iterable한 객체를 생성한다.

range(n) : 0 이상 n 미만인 수를 차례로 나열하는 수열

range(a, b) : a 이상 b 미만인 수를 차례로 나열하는 수열

range(a, b, step) : a 이상 b 미만의 수를 step 간격으로 나열하는 수열


이때 step이 음수가 되면 역순!


# python list slicing(:)

슬라이싱 문법

[ : ] 처음부터 끝까지

[ start : ] start 인덱스부터 끝까지

[ : end ] 처음부터 end 인덱스까지

[ start : end ] start 인덱스부터 end 인덱스까지

[ start : end : step ] step만큼 문자를 건너뛰면서 start 인덱스부터 end 인덱스까지