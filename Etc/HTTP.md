# HTTP 통신과 HTTP 요청

## Socket 통신과 HTTP 통신

먼저 Socket 통신에 대해 알아야 한다.

Socket은 네트워크 상에서 돌아가는 두 개의 프로그램 간 양방향 통신에서 통신단자이다.

이때, 소켓은 두 프로그램 모두에 생성된다.

​

어떤 A가 통신을 하기 위해서 소켓을 오픈한다고 하자

B가 A와 통신하기 위해서는 A의 ip주소와 이 소켓의 포트번호가 필요하다

그래서 B가 ip주소 : 포트번호 이런 식으로 A에게 보내면 그때에 A와 통신이 가능하다

​

그런데 이때 C도 A와 통신하고자 한다고 하자.

A는 B와 하나의 소켓의 포트번호로 통신하고 있기 때문에 같은 번호로 C와 통신할 수 없다.

​

그래서 이를 해결하기 위해서 스레드의 개념을 이용한다.

먼저 A가 어떤 포트 번호로 소켓을 연다. 이 포트번호로 B가 통신을 요청하면, - main 스레드

A는 다른 소켓을 생성해서 랜덤으로 포트번호를 부여한다. 

그리고 B는 생성된 다른 소켓으로 통신을 한다. - 스레드1

C는 A가 처음 열었던 소켓의 포트 번호로 통신을 요청한다.

A는 다른 소켓을 생성해서 랜덤으로 포트번호를 부여한다.

그리고 C는 생성된 다른 소켓으로 통신을 한다. - 스레드2

​

그런데 이때 한번 연결되면 계속 연결된 상태로 있다. 

시간을 쪼개서(time slice) 동시동작하게 한다. 

그렇기 때문에 연결된 대상이 많아지면 부하가 높아진다.

​

이렇게 부하를 높이지 않기 위해 http통신은 연결을 끊어버리는 stateless 방식을 쓴다.

http 통신은 문서를 전달하는 통신이기 때문에 어떤 문서를 요청하면 문서를 바로 전달해주고 연결을 끊는다. 

연결이 끊겨있기 때문에 스레드 같은 것을 이용할 필요 없이 다른 대상이 통신을 요청해도 된다. 

그런데 대신, 같은 대상이 다시 요청을 하면 여전히 바로 응답을 하지만, 응답하는 쪽에서는 전에 응답했던 대상과 같은 대상인지 알지 못한다.

이런 단점을 보완해서 만들어진 것이 웹 서버다.

​

## 요청

웹 서비스는 HTTP를 이용해서 요청을 받는다. 

예를 들어 브라우저 주소창에 google.com을 입력하면 브라우저는 google 서버로 아래와 같은 요청을 보낸다.

~~~
GET / HTTP/2
Host: www.google.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:89.0) Gecko/20100101 Firefox/89.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: ko-KR,ko;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
~~~

부분적으로 살펴보자

### Start Line
~~
GET / HTTP/2
~~
Method는 "GET"이었으며, 요청을 보내는 위치(Path)는 "/"이고, 프로토콜 버전은 "HTTP/2"라는 것을 말한다. 

메소드로는 GET 말고도 POST, PUT, DELETE 등이 있다.

그리고 패스에는 쿼리 파라미터(Query Parameter)가 있을 수 있다.

~~~
/users?id=123&name=test
~~~
위와 같은 패스에서 쿼리 파라미터는 "?id=123&name=test"이다.

"/users"까지가 path임을 "?"로 구분하고, 파라미터는 id와  name 두 개 이다. 각각의 값은 "&"로 구분한다.

### Header

이 예시에서는 Start Line을 제외한 부분이 헤더다.

이 중에서 일반적으로 많이 쓰이는 것은 Host, User-Agent, Accept등의 필드이다. 

~~~
GET / HTTP/2
Host: www.google.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:89.0) Gecko/20100101 Firefox/89.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: ko-KR,ko;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
~~~

### Body

헤더 뒤에 Blank Line 이 있다면 그 뒤는 Body다.

Body는 주로 사용자가 제공해야 하는 정보를 담는다.

예를 들어 로그인하려고 할 때, 아이디와 비밀번호 등의 내용은 Body에 담긴다.

이렇게 HTTP 요청은 Start Line, Header, Body로 이루어져 있다.