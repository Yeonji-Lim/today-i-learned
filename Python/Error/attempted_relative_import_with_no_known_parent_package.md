
## User-Defined Module, 커스텀 모듈이 실행시 포함이 안될 때

conda나 pip로 설치하는 모듈, 즉, built-in package를 import 하는 경우가 absolute import이다.

사용자에게 만들어진 module 을 import 하는 경우는 relative import


1. sys.modules

이미 로딩된 패키지와 모듈을 딕셔너리 형태로 저장

처음 import한 패키지나 모듈은 sys-module 탐색 중에는 찾을 수 없다.

idle에 sys.modules를 치면 그 목록을 볼 수 있다.


2. built-in modules

파이썬에서 제공하는 공식 라이브러리


3. sys.path

string 요소로 모듈의 경로를 list 형태로 저장하고 있다.

직접 만든 모듈이나 패키지를 사용하고 싶다면 append를 사용하면 된다.

~~~
import sys
sys.path.append('경로')
~~~

## attempted relative import with no known parent package 에러

main 모듈에서 상대경로를 사용하는 경우 파이썬이 상대경로의 출발점인 main 모듈의 위치를 찾지 못하기 때문에 발생하는 오류


모듈을 실행하는 방법은 2가지가 있다.

1. 인터프리터에서 직접 실행

2. 다른 모듈에서 import해 실행


직접 실행하는 1번 방법의 경우, 모듈의 이름(__name__)은 자동적으로 __main__으로 변경된다.

그런데 모듈 실행 뒤 상대 경로를 통해서 다른 모듈을 import 하고자 할 때,

파이썬은 모듈의 이름에 기반을 두고 현재 모듈의 위치를 찾는다.

그렇기 때문에 모듈의 이름이 __main__으로 변경된 상태에서는 현재 모듈의 위치를 찾을 수 없다.


이러한 경우에는 상대경로가 아닌 절대 경로를 사용해 주어야 한다.

~~~
.
ㄴ sub
|  ㄴ b.py
|  ㄴ c.py
ㄴ a.py
~~~

a.py를 실행하는데, b.py를 a.py에 import 해야하는 경우, 절대 경로를 사용한다.

~~~
# a.py
from sub.b import b
~~~

a를 실행하는 상황에(메인 파일), b 모듈에서 c모듈을 import 하는 경우에는 상대경로로 설정해야 한다.

왜냐하면 메인 파일이 실행되면 그 메인을 기준으로 절대 경로가 잡히게 되고,

그렇게 되면 b모듈은 경로 내에서 sub 패키지의 하위 모듈로 등록되기 때문이다.


정리하면 a.py를 실행하는 경우 다음과 같다.

~~~
# a.py
from sub.b import b # 절대경로

# b.py
from .c import c # 상대경로
~~~

b.py를 실행하는 경우, 이제는 b.py가 메인 모듈이 되므로 다음과 같다.
~~~
# b.py
from c import c # 절대경로
~~~