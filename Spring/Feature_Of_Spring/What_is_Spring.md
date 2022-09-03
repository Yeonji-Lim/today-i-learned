# Spring

## 1. 프레임워크

## 2. 오픈 소스

## 3. [IoC 컨테이너를 가진다.](IoC_Container)

## 4. [[DI]]를 지원한다.

## 5. 많은 필터를 가지고 있다.

필터 : 검열의 역할, 문지기

스프링에는 많은 필터가 있는데 사용할 수도 있고, 사용안되고 있던 걸 사용할 수도 있고, 직접 필터를 생성할 수도 있음

실제로는 톰캣 안에 스프링 컨테이너가 있고 톰캣의 필터(web.xml)를 거치고 스프링 컨테이너의 필터(인터셉터, AOP)를 거치는 방식임

## 6. 많은 [[Annotation]]을 가지고 있다. 
-> 리플렉션, 컴파일 체킹

스프링에서는 어노테이션을 객체 생성에 쓴다.

런타임에서 클래스를 분석함 -> 리플렉션
메소드, 필드, 어노테이션을 보고 미리 설정한 행동을 함

리플렉션 : 런타임 시 해당 클래스가 어떤 것들을 들고 있는지를 분석함

## Message Converter를 가지고 있다. 기본값은 json


중간언어 : 주로 xml을 썼었는데 이제 주로 json을 쓰고 있음


ex : 자바 프로그램 <-> json <-> 파이썬 프로그램

이때 번역해주는게 Message Converter


8 bit = 1 byte : 통신의 단위, 하나의 문자


## BufferedReader와 BufferedWriter를 쉽게 사용할 수 있다.


원래 배열로 입력 받음

-> 배열은 크기가 고정적임


BufferedReader는 가변적으로 입력을 받을 수 있다.


@ResponseBody -> BufferedWriter

@RequestBody -> BufferedReader


## 계속 발전중이다.

# JPA

## Java Persistence API

Persistence : 영속성, 데이터를 생성한 프로그램의 실행이 종료되더라도 사라지지 않는 데이터의 특성

RAM이 아니라 하드디스크에 저장되는 것이랑 비슷한 느낌

JAVA에 있는 데이터를 영구히 기록할 수 있는 환경을 제공하는 API

### API? 

Application Programming Interface

프로그램을 만들기 위해서 제공되는 인터페이스

### 인터페이스?

상하관계가 존재하는 약속

✻ 프로토콜은 동등한 관계에서 하는 약속


## JPA는 ORM 기술이다.

Object Relational Mapping

마치 하인 같은 것


모델링 한다는 것 : 추상적인 개념을 현실세계로 뽑아낸다는 것

TRM : 테이블에 있는 데이터를 현재 언어의 타입에 매핑해야 함 -> 모델링


ORM은 오브젝트를 통해서 데이터를 생성하는 것임 : 모델링의 반대

이 과정을 위해서 필요한 것은 JPA가 가지고 있는 인터페이스


자바에서 어떤 클래스를 만들어서 실행을 하면 데이터의 테이블이 자동으로 생성되게 하는 기법을 ORM이라고 함


## JPA는 반복적인 CRUD작업을 생략하게 해준다.

원래는 이 작업을 위해서 자바가 DB에게 커넥션을 요청함 그러면 DB는 필요한 세션을 열어줌

그렇게 되면 연결이 되고 자바는 커넥션을 가지게 된다.

자바는 그러면 쿼리를 전송할 수 있다 데이터 베이스는 해당하는 처리를 해주고 자바에 응답을 하게 됨

자바는 이걸 받아서 데이터 베이스의 데이터 타입을 자바 오브젝트로 변경해야 한다.


위와 같은 일을 원래는 반복적으로 해줘야 하는데,

JPA를 쓰게 되면 이러한 일들을 함수 하나로 제공!

## JPA는 영속성 컨텍스트를 가지고 있다.

영속성 : 어떤 데이터를 영구적으로 저장


자바에서는 데이터를 영구적으로 저장할 때 파일 시스템이 아니라 DB를 이용한다.


컨텍스트 : Context, 어떤 대상의 모든 정보

개념이 많이 모호한 편임


영속성 컨텍스트

어떤 데이터를 DB에 저장하려 한다고 하자

그러면 바로 직접적으로 데이터가 DB에 바로 접근하는 것이 아니라 그 중간에 영속성 컨텍스트라는 것이 있다.

프로그램에서 DB에 접근하는 모든 정보를 영속성 컨텍스트가 알고있다.

DB에 저장하기 전에 영속성 컨텍스트 : 자바가 저장하는 모든 데이터를 알고 있다.


그래서 데이터를 저장하고 있으면 프로그램(자바)는 영속성 컨텍스트에 데이터를 던진다.

영속성 컨텍스트는 데이터를 데이터 베이스에 준다. 그렇게 해서 DB에 데이터가 저장된다.


그런데 그리고 나서 영속성 컨텍스트에서 이 데이터를 삭제하면 DB에 있는 해당 데이터가 삭제된다.

즉 영속성 컨텍스트에 있는 데이터와 데이터 베이스에 있는 데이터가 동기화되는 것!


어떤 데이터를 요청할 때 영속성 컨텍스트에 해당하는 데이터가 없다면 영속성 컨텍스트는 DB에서 해당하는 데이터를 가져다가

자바 객체로 변환하여 가지고 있는다. (내용은 같고 타입이 다름)

그리고 나서 영속성 컨텍스트가 자바 객체로 변환된 해당 데이터를 프로그램에게 넘겨준다.

이 상태에서 DB, 영속성 컨텍스트, 프로그램에 있는 그 데이터는 동일하다.


이때 프로그램에서 이 데이터를 변경하면 영속성 컨텍스트의 데이터는 자동으로 변경된다.

이 데이터를 DB에 넣으려고 시도하면 DB에 있는 데이터와 영속성컨텍스트에 있는 데이터가 달라진다.

이때는 insert 가 아니라 update가 자동으로 일어난다.

이런 일을 해주는 것이 영속성 컨텍스트.


자바가 DB에 대해 해야하는 모든 메타 데이터들을 영속성 컨텍스트가 가지고 있다.


## JPA는 DB와 OOP의 불일치성을 해결하기 위한 방법론을 제공한다.

DB의 특징 중 하나는 각각의 컬럼들을 가질 수 있는 자료가 기본 자료형이라는 것이다.

오브젝트를 가질 수 없음! 이를 해결하기 위해서 foreign key를 사용한다.


그런데 자바의 입장에서 보자

이 DB의 형태를 그대로 가져간다고 했을 때 foreign key의 값만을 알 수 있다.

구체적으로 어떤 객체를 가지고 있는지 확인하려면, 두번의 select를 하거나 join을 이용해야 한다.


그런데 자바는 기본 자료형이 아닌 오브젝트를 저장할 수 있다.

그렇게 해서 한번에 확인할 수 있다.


그러면 DB와 자바에서의 형태가 다르게 된다.

이때 JPA가 자동으로 자바에서 객체로 표현된 것에 자동으로 데이터를 매핑해준다.

DB에서는 JPA가 자동으로 foreign key를 생성해준다.

## JPA는 OOP의 관점에서 모델링을 할 수 있게 해준다.

상속, 컴포지션, 연관관계가 가능하다.

​
## JPA는 방언(dialect)처리가 용이하여 Migration을 하기 좋다. 

유지보수에도 좋다.

JPA에 연결되는 DB는 여러종류가 가능하다. 추상화객체로 다루기 때문에 이 추상화객체가 어떤 거냐에 상관이 없다.

마치 우리가 종이에 글을 쓸 때와 마찬가지다.

연필로 쓰다가 볼펜으로 쓴다고 글을 쓰지 못하는게 아니고 만년필, 붓, 형광펜 등 어떤 필기도구든지 그 필기도구를 이용해서 글을 쓸 수 있다.

## 웹서버

필요한 데이터를 가지고 있는 것

요청은 웹서버의 위치인 IP주소, 필요한 자원의 위치인 URL을 포함해서 요청함

​
## 톰켓

아파치라는 웹서버를 사용할 때, 자바코드가 포함된 .jsp를 요청하면 아파치는 이해하지 못함

그래서 이걸 해결하기 위해 톰켓을 쓴다. 이런 요청이 들어오면 제어권을 톰켓이 받는다.

그러면 톰켓은 .jsp에 있는 모든 자바코드를 컴파일하고 컴파일이 끝나면 그 데이터를 .html에 덮어씌움

아파치는 이 .html을 응답해주는 것


## 서블릿 컨테이너

클라이언트로 부터 요청을 받는다.

최초의 요청이면 객체를 생성한다. ( 메모리 로딩 -> 객체 생성 -> init() )

최초 요청이 아니면 기존에 생성된 객체로 응답


정적인 파일을 요청하면 톰켓이 일하지 않는다. 아파치가 일하게 됨

java파일을 요청하면 톰켓이 일함

Spring을 사용할 때도 정적인 파일을 요청하면 일하지 않음

그런데 사실 Spring은 정적인 파일을 요청할 수가 없음


URL : 자원에 접근하기 위함

URI : 식별자를 통해서 접근 -> 특정한 파일 요청을 할 수 없다. 요청시에는 무조건 자바를 거쳐야 한다.

그래서 URI를 통해서 접근하니까 정적인 파일을 바로 요청할 수 없음

~~~
http://naver.com/a.png        URL
http://naver.com/picture/a    URI
~~~

서블릿 : 자바로 웹을 할 수 있게 하는 것

그리고 이걸 모아둔 것이 서블릿 컨테이너


서블릿 컨테이너로 자바로된 요청이 들어오면 스레드가 생성된다.

그러면 이 스레드가 서블릿 객체를 만든다.

이 서블릿 객체가 필요한 일들을 진행한다. : 데이터베이스 커넥션, html 응답 등..


스레드가 왜 필요?

동시에 여러가지 요청이 들어올 수 있음

요청마다 스레드를 만들고 새로운 서블릿 객체를 만든다.

이렇게 하지 않으면 앞의 스레드로 만들어진 서블릿 객체가 일을 모두 끝낼 때까지 뒤의 요청에 대한 응답에 딜레이가 생긴다.


스레드는 무한정 만들어지지 않음

이 스레드가 한계까지 만들어져있고 모든 스레드가 응답을 하지 못할 때

새로운 요청이 들어오게 되면 대기하게 된다.

첫번째 스레드가 응답을 하게 되면 연결이 끝나게 된다.(stateless)

이 스레드는 사라지지 않고 대기하고 있는 요청에 할당된다.


## web.xml

마치 관문 같은 것.


- ServletContext의 초기 파라미터

    마치 암구호 같은 것. 알고 있는지 확인


- Session의 유효시간 설정

    인증해서 들어오는 것이 세션, 시간이 지나면 만료


- Servlet/JSP에 대한 정의

- Servlet/JSP 매핑

    요청한 식별자가 어디인지를 알려주고 안내


- Mime Type 매핑

    Mime Type : 들고올 데이터의 타입

    get 방식은 데이터를 가져오지 않음 select

    해당 하는 데이터 타입을 가질 수 있으면 가공, 맞는 곳에 적재


- Welcome File list

    어디 갈지, 가져오는 데이터가 없는 아무 이유없이 들어오는 경우에 보내는 곳


- Error Pages 처리

    이상하거나 모르는 곳으로 가려고 할 때 나오게 하는 Error Page


- 필터 설정

    위험 요소가 있는 경우, 금지하거나, 위험요소를 제거하고 들여보냄


- 리스너 설정

    특정 클라이언트의 특정 특징만 확인, 해당 클라이언트인 경우 강제로 특정한 곳으로 보냄


- 보안


## Front Controller 패턴

web.xml에 너무 많은 Servlet/JSP에 대한 정의가 들어있기 힘들다.

그래서 Front Controller를 두어서 최초 앞단에서 request 요청을 받아서 필요한 클래스에 넘겨준다.

이때 새로운 요청이 생기기 때문에 request와 response가 새롭게 new될 수 있다.

그래서 Request Dispatcher가 필요하다.


어떤 요청이 들어오는데, 특정 주소(.do)같은 것이 들어오게 되면 Controller에게 그 요청이 가게 되는 것으로 web.xmp에 미리 약속을 해두자.

이때, 최초의 URI 또는 자바 파일 요청이 들어오면 바로 자원으로 접근할 수 없다.

web.xml을 가지고 있는 톰켓으로 가게 된다.


이 톰켓은 그러면 request와 response 객체를 만든다.

~~~
request 객체 : 어떤 것을 요구하는지, 어떤 데이터를 가지고 요청하는지에 대한 정보

response 객체 : 응답 정보, 데이터
~~~

즉, 어떤 가변길이의 문자가 들어오면 톰켓은 이걸 자바가 쉽게 다룰 수 있는 객체로 만들어 주는 것


아무튼 이때, 특정 주소(.do)가 들어오면 web.xml에서 FrontController가 낚아채게 된다.

그렇게 되면 FrontController가 미리 설정한 자원으로 새로운 request 객체가 접근하게 된다.

이렇게 되면, 톰켓의 request, response 객체가 새로운 객체로 바뀌게 된다.

그런데 자원입장에서는 response를 보내야하는 곳이 원래 처음에 요청을 보낸 곳이 아니라 FrontController가 된다.


그래서 이를 해결하기 위해서 기존의 request, response 객체를 유지하는 방법이 있다.

즉, 이 상황에서 새로운 객체를 만들어서 기존을 덮어씌우거나 지우는 것이 아니라, 기존의 객체를 그대로 사용하는 것

이 역할을 해주는 것이 Request Dispatcher


## Request Dispatcher

필요한 클래스 요청이 도달했을 때, FrontController에 도착한 request, response를 그대로 유지시켜준다.


## Spring의 Dispatch Servlet

JSP를 사용한다면 Front Controller 패턴을 직접 짜거나 Request Dispatcher를 직접 구현해야 한다.

그런데 Spring에서는 그런 작업이 필요하지 않다.

Dispatch Servlet = Front Controller 패턴 + Request Dispatcher


DispatchServlet이 자동생성 되어질 때 수 많은 객체가 생성된다.(IoC) 보통 필터들이다.

해당 필터들은 내가 직접 등록할 수도 잇고, 기본적으로 필요한 필터들은 자동 등록되어진다.

## Spring Container


Dispatcher Servlet에서 생성되는 객체들이 관리되는 곳


### Application Context


어떤 요청이 들어오면 web.xml이 받아서 Dispatch Servlet이 동작해서 '컴포넌트 스캔'을 한다.


주소 분배를 해주는 거임. 근데 이때 모든 파일을 뒤져서 필요한 파일을 메모리에 올림

이때 어떤 것을 올리고 어떤 것을 올리지 않을 건지는 annotation으로 구분

아무튼 메모리에 떠있는 것으로 주소 분배함

스캔한다는 거는 메모리에 로딩한다는 거임


이렇게 메모리에 올리는 것을 ApplicationContext에 등록된다고 하고, 또 이걸 IoC라고 한다.

IoC는 제어의 역전을 의미함 그리고 이 객체들을 스프링이 직접관리함(어떤 어노테이션을 올릴건지)

개발자는 이 주소를 몰라도 된다. 왜냐면 필요할 때 DI(의존성 주입)하면 되기 때문


근데 이전에 하는게 있음

ContextLoaderListener

스레드 들이 공통적으로 요청하는 것이 있을 수 있음 이런 경우에는 DB connection이 필요

이 리스너가 이걸 띄움

어떻게? root-applicationContext라는 파일을 읽어서 띄워줌

(root-applicationContext파일과 servlet-applicationContext파일을 ApplicationContext라고 함)


root-applicationContext는 해당 어노테이션을 제외한 어노테이션 Service, Respository등을 스캔하고 DB관련 객체를 생성

그리고 이 파일은 ContextLoaderListener에 의해 실행

(servlet-applicationContext는 ViewResolver, Interrceptor, MultipartResolver 객체를 생성하고 웹과 관련된 어노테이션 Controller, RestController를 스캔함 그리고 이 파일은 Dispatch Servlet에 의해 실행됨)


아무튼 ContextLoaderListener는 web.xml이 실행해줌

그래서 root-applicationContext는 servlet-applicationContext보다 먼저 로드됨

이렇게 되면 리스너가 DB에 띄운 애들은 그 다음 단계에서 디스패처가 띄운 애들한테 접근을 할 수 없음근데 반

근데 반대는 가능


### Bean Tactory

@Bean으로 필요한 객체를 등록 : 초기에 메모리에 로드 x, 필요할 때 getBean()이라는 메소드를 통해 호출, 메모리에 로드

이것 또한 IoC이고 필요할 때 DI해서 사용가능

그런데 여기에 로드되는 객체들은 미리로드 x, 필요할 때 호출하여 로드 lazy loading이 된다는 점이 ApplicationContext랑 다름

## Handler Mapping

요청 주소에 따른 적절한 컨트롤로 요청

Handler Mapping이 특정한 주소를 찾아줌

해당 주소 요청이 오면 적절한 컨트롤러 함수를 찾아서 실행한다.

​

응답할 때는 html 파일을 응답할지 Data를 응답할지 결정해야 하는데, html 파일을 응답하게 되면 ViewResolver가 관여하게 된다.

하지만, Data를 응답하게 되면 MessageConverter(Jackson)가 작동하게 되는데, 메시지를 컨버팅할 때 기본 전략은 json이다.

​

## 전체적인 작동

1. 톰켓 실행시 web.xml 읽어들임

2. ContextLoaderListener가 미리 DB에 연결해서 올려둘 것들 올려둠

3. 요청이 들어오면 그때 필요한 거 메모리에 올림

4. DiapatcherServlet이 주소를 분배 해줌

5. 응답으로 Data나 html파일을 보냄