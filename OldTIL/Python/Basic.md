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

# python int()

괄호 안의 값을 정수로 나타낸다.

~~~
x = int(3.5) # 실수를 정수로 반환, 3

x = int(a, base = 16) # 진법을 함께 표시, 10

x = int('13') # 문자열을 정수로 반환, 9 (아스키값 57이 아님, 그냥 정수 13)

x = int('x') # 오류, 변환할 정수가 없음.
~~~

# python split()

문자열 쪼갤 때 쓰는 함수

~~~
string.split(sep , maxsplit)
~~~

sep : 어떤 문자를 기본 값으로 자를 것인지, default는 none

maxsplit : 몇번 자를 것인지, default는 -1

​

# Argparse

python 표준 라이브러리에서 제공하는 command-line parsing module.

파이썬 스크립트 호출 시 인자값을 줘서 동작을 다르게 하고 싶은 경우에 사용한다.

# python heapq

이진트리 기반의 최소 힙 자료구조.

우선순위 큐라고 생각하면 된다.

~~~
import heapq
...
heapq.heappush(heap, item)
~~~