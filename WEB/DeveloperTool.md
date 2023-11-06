- Elements : html/CSS 상태 확인
- Console : 콘솔 (변수 정보를 확인하고 오류 메시지 표시)
- Sources : 스크립트 디버깅 (break point 지정 및 변수 모니터링 등)
- Network : 브라우저에서 발생하는 통신 상태
	- Fetch/XHR : API의 request, response 확인
		1. Name : 리소스의 이름과 URL 표시
		2. Status : 작동 여부 표시 ( 200: 정상작동 )
		3. Type : 파일의 형식
		4. Initiator : 요청을 발생시킨 코드 표시 (클릭하면 코드로 이동)
		5. Size : 리소스들의 파일 사이즈
		6. Time : 요청과 응답까지 걸린 시간 확인
		7. Waterfall : 타임라인 세부 정보
	- 백엔드 프론트엔드 소통이 잘 안됐을 때 확인
	  백엔드와 프론트엔드가 api를 주고 받을 때 네트워크가 통신하는데, 통신이 제대로 됐는지 안됐는지 확인할 수 있음
- Performance(예전 Timeline패널) : 성능 측정
- [Memory](Memory)(예전 Profiles 패널) : 메모리 사용 형태를 작성하고 누수 탐색.
- Application(예전 Resources 패널) : 쿠키 및 스토리지 등의 내용 수집
- Audits : 페이지를 분석하고 최적화를 위한 팁 나열
- Security : Mixed content 이슈, 인증서 문제 등을 디버깅

![](https://i.imgur.com/0ANu81Z.png)
NHN FORWARD 2020

# 멘토링 내용

다룰 내용
![](https://i.imgur.com/aJSAN5m.png)
![](https://i.imgur.com/hQera48.png)
-> 크롬의 버그

![](https://i.imgur.com/UlWRcYM.png)
![](https://i.imgur.com/sAf8465.png)
디바이스설정에서 저걸로 느리게 랜더링 하는거 해볼 수 있음 -> 어떤게 먼저 뜨는지 테스트 가능


왜 가로/세로 지원? -> 웹 접근성! 지침에 나온다.

W3C : 휠체어 앞에 휴대폰 거치대 -> 방향 전환이 자유롭지 못할 수도 있다.

## 해당 페이지에 쓰인 모든 리소스 보기 및 검색

![](https://i.imgur.com/j9oaV1y.png)
오른쪽 위 오픈 파일 이렇게 서치 가능

## 브라우저 피드백 보기

![](https://i.imgur.com/TkjPTAG.png)

![](https://i.imgur.com/O2zgbHI.png)
크롬 브라우저에서 먼가 위험한 거 경고해줌

ex : doctype을 제대로 지정하지 않으면 html5으로 랜더링하지 않음, iframe 안에서 안적어둠

## 페이지 로딩시 HTTP failure 확인

네트워크 

fetch/XHR : ajax 같은 것들

development resource는 network 탭에서 잡지 못하는 것들을 잡아줌
여기서 못 가져오는 것 확인해볼 수 있음

![](https://i.imgur.com/v83dRhv.png)
.map file
![](https://i.imgur.com/rFZ0yZ5.png)

오른쪽 클릭해서 copy url해서 열어보자 -> 안열리면 잘 막아둔거 

![](https://i.imgur.com/U8yhRxY.png)

## 클라이언트 캐시 컨트롤

리스폰스 헤더 설정 : 웹서버에서 함
마인타입 기준으로 image/jpeg 이런 식으로 클라이언트 캐시를 얼마나 보관할 것인지 
사용자 관점에서의 캐시다 (서버가 아님)
금액적인 것 때문에 중요함
클라이언트 캐시가 없으면 매번 새로운 리소스를 보내주어야 함
일반적인 사용자는 캐시를 잘 안지움
개발자는 캐시를 지우고 새고 하기 위해 ctrl + shift + r

근데 브라우저 단에서 이거 말고도 지원을 해줌

디저블 캐시 
![](https://i.imgur.com/sWFZ3Tc.png)

네트워크 탭에서도 설정 가능

![](https://i.imgur.com/wQs0EDv.png)

## 웹 접근성 관련 (색맹, 색약 테스트)

![](https://i.imgur.com/UdDao0C.png)

![](https://i.imgur.com/ruhRYbL.png)

## repaint 성능 분석 및 테스트

서비스에서 브라우저가 웹을 어떤 순서로 그릴지 정해져 있음

tap키를 누르면 어디로 먼저 가게 할 것인지도 설정가능

repaint : 브라우저가 그려주는 과정

![](https://i.imgur.com/bjTJDBZ.png)
![](https://i.imgur.com/jH4xugq.png)

쿠팡이 리페인팅이 잘 되어있음 뭔가 움직이고 그런게 없고 빡 나옴

## 탭을 비롯한 애니메이션 테스트

캐러셀 : 슬라이드쇼와 같은 방식으로 콘텐츠를 표시하는 UX 구성 요소
캐러셀 테스트 할 때 많이 씀

animation 했을 때 헤더가 쭉 내려가는 게 보임 

![](https://i.imgur.com/Cp4pXll.png)

10%로 하면 느려지면서 애니메이션이 보임

탭 넘어갈 때 씀

무한 스크롤 

캐러셀도 무한 하게 갈 수 있게할 수 있음
끝까지 가면 처음으로 가고 할 수 있는데 이게 부자연스러울 수도 있다.
이걸로 테스트 가능

## 페이지 렌더링시 레이어 성능 분석

![](https://i.imgur.com/EVUoMlx.png)
![](https://i.imgur.com/RDAqhli.png)
각 컴포넌트가 어떤 width를 가지는디

넘어가는 너비는 반응형 테스트를 잘 해야 함

![](https://i.imgur.com/k96fnsG.png)
이거는 옛날 네이버 화면. 저렇게 넘어가는게 많이 있음

## userAgent 변경

크로스 브라우징 테스트할 때 함 
![](https://i.imgur.com/RAQ0ssA.png)

- 참고
![](https://i.imgur.com/CjBNwiX.png)
웹 컨텐츠 압축
-> 각각의 성능 비교해볼 수 있음

![](https://i.imgur.com/DPkidiX.png)
크로스 브라우징 테스트를 할 수 있다.

![](https://i.imgur.com/5OqzleC.png)

## 일부자원 제거 테스트(디버깅)

![](https://i.imgur.com/B9jbBeU.png)

![](https://i.imgur.com/O7KlIGT.png)
활성화 후 +

![](https://i.imgur.com/PAZo4KP.png)
모든 css가 빠짐

## 난독화 코드 보기

![](https://i.imgur.com/Z0GJOfU.png)
저게 프리티 프린트
압축 코드를 보기 좋게 펼쳐줌

## 요소 식별시 사라질 때

![](https://i.imgur.com/JxA0tQn.png)
저거 처럼 나중에 호버하면 나오는 거 보고 싶을 때 어떻게 하지?

css 하나 체크 해놓고?

클릭하고 ctrl + shift + c를 누르면 됨 

## 코드 모듈성 체크
- common 파일 만들기(common.css, common.js)

여러 파일에서 쓰이는 파일
유틸성 코드들을 많이 넣어둠
여기에 넣을 코드라는 것은 어떻게 식별?
기준이 모호하다

어떤 기준으로 common파일을 넣어야 하는가?
공통된 ui, 기능들 모아둔다.
여러번 사용? -> '여러번' 이라는 것은 어떻게 체크함?

![](https://i.imgur.com/8bTQCcZ.png)
오른 쪽 아래에 커버리지를 누른다음 새고

![](https://i.imgur.com/csHwQbE.png)
빨간색이 많은 것
![](https://i.imgur.com/uGdjxCU.png)

이 파일에서 커버리지가 46.7%라는 것임

![](https://i.imgur.com/oOqQhUx.png)
빨간색 줄 코드는 이 페이지에서 안 탔다는 것임

커버리지 체크해보고 평균적으로 커버리지가 높은 것을 common으로

## JS 이벤트 핸들러 찾기

![](https://i.imgur.com/5kDxmgd.png)
저거 체크하면 조상도 체크할 수 있음
체크해제해서 클릭 이벤트 걸린거 리스너로 볼 수 있음

네이버에서 이렇게 코드가 안나올 때가 있음
![](https://i.imgur.com/PTm2Mhv.png)

콘솔에서 top.request.reload()하면 원래 나왔음 

## 모던하게 셀렉터 뽑기

![](https://i.imgur.com/TknfDxs.png)
얘 같은 경우에 클래스도 안되어있는데 어떻게 셀렉터?

- Xpath를 쓰기도 함
- 오른쪽 클릭 > copy로 
	- selector
	- js path

이게 모던한지는 몰라도 여기서 힌트를 얻을 수 있음

클론 코딩
![](https://i.imgur.com/JsKVFC1.png)
얘가 가지고 잇는 css를 다 가져올 수 있다.

![](https://i.imgur.com/eotOFlt.png)
주요 스타일을 다 뽑을 수 있음
-> 이거만 부여해도 똑같이 만들기 가능

![[Pasted image 20230606230031.png]]

<!--Upload failed, remote server returned an error: [object Object]-->
![[Pasted image 20230606230049.png]]
이거 움직임 -> 이벤트 리스터 잡기 애매함
어떻게 잡음? : 영역을 크게 잡고 그 안에 tag

<!--Upload failed, remote server returned an error: [object Object]-->
![[Pasted image 20230606230151.png]]

얘가 레이어를 잡고 잇음

<!--Upload failed, remote server returned an error: [object Object]-->
![[Pasted image 20230606230220.png]]
이렇게 잡을 수가 있음..?
<!--Upload failed, remote server returned an error: [object Object]-->![[Pasted image 20230606230301.png]]

속성을 부여하는 애가 누군지 볼 때 attribute

node removed -> 계속 삭제될 때 삭제하는 애가 누군지 볼 수 있음

![](https://i.imgur.com/rWJ1I9I.png)
실시간 검색어 -> x, 증시 탭

여기서 속성은 attribute
property와 다름 (JS)

![](https://i.imgur.com/qityruu.png)

![](https://i.imgur.com/2eJdHXw.png)
지금 잡고 잇는거 볼 수 있음

![](https://i.imgur.com/YLhZDSN.png)
이렇게 검색할 필요 없이

![](https://i.imgur.com/UyZ0tl5.png)
여기서 프로퍼티 누르면 이 태그가 가지고 있는 프로퍼티 다 뜸

![](https://i.imgur.com/SqbzU7O.png)

computed는 최종적인 결과물
useragent는 무시

![](https://i.imgur.com/NbX349t.png)

![](https://i.imgur.com/uiPu3Y0.png)
이렇게 color검색해서 가지고 있는거 다 볼 수 있음

![](https://i.imgur.com/JasWxYx.png)


![](https://i.imgur.com/rjURHiQ.png)

![](https://i.imgur.com/Gw4kaq2.png)
iframe -> CORS에 위배되지 않는 선에서 할 수 있음 보통 광고에서 함
![](https://i.imgur.com/89N4PsO.png)
플러그인 제끼고 이렇게 뜸

![](https://i.imgur.com/RHF9ckm.png)

광고에 있는 것을 식별하고 싶으면 이렇게 누르고 해야 함

![](https://i.imgur.com/dqI1gvh.png)

![](https://i.imgur.com/PPtY9cj.png)

scope 영역을 보는 것이 중요하다. 
자바스크립트에서 클로저 변수를 식별할 수 있음
클로저를 계산하는 상황은 별로 없음
![](https://i.imgur.com/OupUpQj.png)

![](https://i.imgur.com/Qt5FhwO.png)

![](https://i.imgur.com/7JVhODF.png)

여기까지로 바로 디버그 걸 수 있음

![](https://i.imgur.com/D9yDGFs.png)
저놈을 조사하고 싶으면

![](https://i.imgur.com/etB1dFV.png)
watch에 넣음녀 값이 변하는 것을 볼 수 있음

![](https://i.imgur.com/WrvQOsk.png)

리액트 함수 만들어주는 snippet이 있음
여기서 말하는 것은 브라우저 스니펫

코드 조각을 보관하는 것

![](https://i.imgur.com/zyymD0u.png)
![](https://i.imgur.com/nf5fKPp.png)
작업할 때 필요한 코드들을 넣을 수 있음

![](https://i.imgur.com/Q7eU7Bu.png)

![](https://i.imgur.com/aJ3Dy5t.png)

![](https://i.imgur.com/9d2OZDi.png)

브라우저 단에서의 코드 에디터
테스트 코드들을 여기에 넣어놓는 경우도 있음

![](https://i.imgur.com/G8VCMXV.png)

회원가입 버튼을 눌럿을 때 구동이 되는 경우
서버에 가기 전에 올바른 요청인지 ajax가 확인

프론트 엔드에서 보낸 코드에서는 문제가 없는데, 
백엔드에서 처리하는 코드는 문제가 있는 그런 상황이라면
거기에 맞는 ajax를 날릴 것임
우리가 보냈던 ajax를 모던하게 다시 보내기 가능
![](https://i.imgur.com/7wKgBvG.png)
![](https://i.imgur.com/316oZwP.png)
이 ajax만 다시 보내기 가능

block request url로 해서 이거 없애고 보내기도 가능

![](https://i.imgur.com/85mTyvC.png)

RPA : 핫한 키워드

![](https://i.imgur.com/7asAYwT.png)
![](https://i.imgur.com/6VHy4uG.png)
쭉 로그인까지 하고 다시 페이지 와서 끔

리플레이하면 다시 그대로 함!

![](https://i.imgur.com/bYTeOhR.png)
이거를 또 코드로 뺄 수 잇음

실무에서 브라우저 테스팅 자동화에 쓰임

![](https://i.imgur.com/uMzpUfC.png)

![](https://i.imgur.com/7axteTn.png)
![](https://i.imgur.com/pYZdDSr.png)
LCP?
Last Content..

어떤 작업이 길어지는지 볼 수 있음

예전에는 FPS분석 할 때 퍼포먼스 탭 사용했었음

## 라이트 하우스

![](https://i.imgur.com/hOrWzmq.png)
웹 접근성
아직 부족, 영어위주이기 때문에 한국어 페이지랑 잘 맞지 않음

extention이 더 좋음, 그래서 이거는 잘 사용안함

