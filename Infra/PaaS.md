# 컨테이너, 오케스트레이션 툴

<img width="638" alt="image" src="https://user-images.githubusercontent.com/57888020/166128669-070cc79c-a68f-487b-8e1c-3a367869cc3a.png">

VM, Container

<img width="662" alt="image" src="https://user-images.githubusercontent.com/57888020/166128678-ad1ed013-68ae-4b36-87eb-dff35f1ef9d9.png">

<img width="305" alt="Container" src="https://user-images.githubusercontent.com/57888020/166128689-85131bae-4df2-40a5-8eba-24d0d7f12b4b.png">

Node : cluster

<img width="754" alt="kube-controller-manager" src="https://user-images.githubusercontent.com/57888020/166128690-e08e65db-9923-4954-9016-0c85719b5532.png">

* cAdvisor : Container Advisro
* Pod : 컨테이너를 하나이상 모아둔 것

<img width="599" alt="Tomcat 8 5" src="https://user-images.githubusercontent.com/57888020/166128693-ca9a0b0a-8055-42d1-be50-081d69b85f98.png">

Openshift -> PaaS

# Proxy

![Forward Proxy Flow](https://user-images.githubusercontent.com/57888020/166128698-5d644be0-90bc-41d8-8be0-4645f9545e3d.png)

프록시 서버 : 보통 아파치 vs nginx 구조
nginx -> 수많은 사용자에게 동시 서비스 제공하는 것에 초점
경량 아키텍처 
Nginx는 정적 콘텐츠에 적합하고, 동적 콘텐츠에서는 프로세스 속도 저하가 있음
단일 스레드에 여러 연결을 처리함

아파치 : 다양한 동적모듈을 로드하기 위한 더 많은 문서와 더 나은 지원
엔진엑스 : 트래픽이 많은 웹 사이트를 위한 많은 정적 컨텐츠 및 미디어 스트림 제공

그래서 nginx를 apache앞에 새워서 리버스 프록시로 처리 가능하다고 함
미리 랜더링된 페이지를 nginx가 빠르게 보여주는 방식으로

# 트랜스코더

콘텐츠를 클라이언트에게 전달하기 전에 본문 포맷을 수정할 수 있다.
이와 같이 데이터의 표현 방식을 자연스럽게 변환하는 것을 트랜스코딩이라고 부른다. (무손실 압축)
중개자에 의한 콘텐츠의 변형이라는 의미로 볼 수 있다.
예를 들어 GIF 이미지를 JPG 이미지로 변환 할 수 있고, 크기, 강도, 압축 등 변환할 수 있다.

출처: https://mygumi.tistory.com/146 [마이구미의 HelloWorld]

네이버의 실시간 영상 트랜스 코딩
https://d2.naver.com/helloworld/0216497

Boss 와 worker를 두어서 처리
보스는 여러 워커와 통신
영상을 여러 부분으로 잘라서 분산 트랜스코딩

<img width="874" alt="Pasted Graphic 4" src="https://user-images.githubusercontent.com/57888020/166128704-cb3729cc-0dc8-4c12-ac35-f8091ad20551.png">

html 태그별 적합한 제공 방식이 다르다면 이런 방식을 생각
