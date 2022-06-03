
# [SonarQube/macOS] 기존 프로젝트 테스트 해보기

알고 보니 별 거 아닌 과정이었는데 제가 뭘 잘 모르고 얼타서 좀 오래걸렸습니다.

1. 먼저 소나큐브를 mac에 설치 해줍니다.

brew로 설치해도 되는데, 이것 저것 해보다가 마지막에 된 것은 홈페이지 다운이었어요. 아마도 brew로 해도 될 거에요..!

저는 홈페이지 다운을 기준으로 설명하겠습니다.

https://www.sonarqube.org/downloads/

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMTU1/MDAxNjU0MjM2ODU5MDA3._RZCZDrjCDofvhBeSnPYOLjKQNA_kqDPfmIyT1-HZnIg.wv0FPaIwVc_LT1u0ySLh5yKTQsFIvuRULQdNdlfV3TYg.PNG.view7186/image.png?type=w966">


이걸 받아 줍니다.

그러면 zip파일이 받아질 텐데 압축을 풀고 나온 파일을 SonarQube로 바꿔준 다음, 응용 프로그램으로 폴더를 옮겨줍니다.


2. 그리고 SonarScanner도 받아줍니다.

https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfNTYg/MDAxNjU0MjM3MTMwNTg2.V2gbCURdq5Ag24y4FoqJP2kutEY7cr8MWlFnj6dFwXkg.Ns2ShiUHhaLaKfBw0UnLEPvyu4gYLzPE9Bg2Arr6p7Ug.PNG.view7186/image.png?type=w966">

맥용을 받아주면 됩니다.

그리고 이것도 압축풀고 SonarScanner로 이름 바꿔서 응용프로그램에 넣어주세요


3. 환경 변수 설정

각각에 대한 환경 변수를 추가해줍니다.

~~~
export PATH=$PATH:/Applications/SonarQube/bin
export PATH=$PATH:/Applications/SonarScanner/bin
~~~

소나큐브를 실행하기 전에 자바 버전이 꼭 11로 되어 있어야 합니다!

자바 버전이 현재 11버전인지 확인해주세요

~~~
java --version
~~~

4. 토큰 생성을 위한 소나큐브 실행


터미널에 다음의 명령을 입력해서 실행합니다!

~~~
sh /Applications/SonarQube/bin/macosx-universal-64/sonar.sh console
~~~

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfNDYg/MDAxNjU0MjQ4NTEyMzY5.3dKBpmrgqZLVI2nLaQ7IFBvIl3_vLvz7t8EFvBQMtQgg.B0elNG8-TvgnJ8BYWoDQc46vvMDAaOCTam3FSXDAfbMg.PNG.view7186/SE-c4ebcecf-14f9-4bd6-aa41-55825284f1ff.png?type=w966">

저 마지막 두 줄이 나올 때까지 기달립니다.

나왔다면 localhost:9000으로 접속합니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMTU2/MDAxNjU0MjM5MzA2NzQw.pNRgCSMBVcxJYEiFIN3Pz5-BlBv8Muh9VfGlmQw77t4g.tmrbIkvxvjKARHmod2cdL1S2ErqGzo0jWuvcdrnU34og.PNG.view7186/image.png?type=w966">

이런 로그인 창이 뜨는데, 처음에는 아이디와 비밀 번호 모두 admin을 입력해서 로그인하면 됩니다.

바로 비밀번호 바꾸라고 나올거에요

바꾸고 나면 다음 창이 나옵니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjcx/MDAxNjU0MjM5Mzg5NTQ2.1hNz6-6phry-oSn7RIQeVULiQuM00HEeqXRonQs56vAg.U_hVzax2uMJpVYzw509gpzBjqo9YLoPmjUiTwQca7tog.PNG.view7186/image.png?type=w966">

Manually를 선택합니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjYz/MDAxNjU0MjM5NTIzNTI3.75-fb9RoPxfuHXiL60pkWLy3VIjf75ECHc9xHdZRtrUg.K4SEOYocKBzIia61am_0dA5TcL15h1aY5QsLR0_6YUIg.PNG.view7186/image.png?type=w966">

원하는 이름으로 설정해줍니다.


<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjE4/MDAxNjU0MjQwNzI0OTQy.wmfAH-CHJJHi0dhLFdjBfwUUGGHry89CYfsFwmxFeWMg.C9qnl-o7v1Wt-WoukfbEBLqy0EQiNhw8ibRUXnYQNDYg.PNG.view7186/image.png?type=w966">

여기서 Locally 선택

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMTMx/MDAxNjU0MjQwNzgxODQ0.VNofMLOVuUSyhyh3TLCO_0Ff5wkgcCJ87E_4x9zSNfwg.h_dDDcZnCzDufKW-SUJVelSYc8pwQ2iIhFEuhq5R5pcg.PNG.view7186/image.png?type=w966">

이름은 그냥 test1로 해서 Generate 해줬습니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfNTMg/MDAxNjU0MjQ4NTE3MjAz.jpMfZjnNJyi0njmMmzmSm-S9fk9F1DHZKngLx34M-Vgg.WaeGWonhbe8A7PwiJrC1I3czG-u32WEHcc9tu3wwkfkg.PNG.view7186/SE-8f6383b0-0183-4635-9f7f-221def7dff61.png?type=w966">

토큰이 나오고 Continue 클릭! 이때 토큰은 따로 외우거나 복사해두지 않아도 됩니다


다음 화면에서 Others 선택, 운영체제는 mac 선택하면 다음과 같은 화면이 나옵니다.

만약 Maven, Gradle, .NET에 해당하는 프로젝트면 해당하는 걸로 선택하면 됩니다!

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjI5/MDAxNjU0MjQ4NTIyOTYx.XkxfcaitPf5nzyPnJq1s8lr4GBJbK7Vj_0BcaLcZB7gg.UeKdCCqRlhCEOImJiiHRSzqXWAn00ophBUkCOD1vVEUg.PNG.view7186/SE-79538a27-442e-4d76-9f2d-0e26d1236336.png?type=w966">

원하는 프로젝트로 넘어가서 저 명령을 치면 됩니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjUz/MDAxNjU0MjQ4NTgxOTEx.hy1rer0m-OkwPdK0rDF3MWVvmaIHa1igt1X3aeOPCnUg.8hhEZ_4Cied2UBtsDgnyjUgyBBJmdqmUyicfngek4Bcg.PNG.view7186/SE-308a54cb-cea9-4c55-a417-5cef5c4dae94.png?type=w966">

크흠.. sonar-scanner가 환경변수 설정이 되었다면 그냥 sonar-scanner 명령만으로 실행될텐데.. 여기서 저는 갑자기 안됐습니다 ㅠ

그래서 일단은 그냥 바로 경로를 집어 넣었습니다.

그리고 저는 프로젝트에 java 파일이 있어서 java 파일이 있는 경우 저렇게 바이너리 파일이 있는 경로를 따로 설정해줘야 하기 때문에 한줄이 더 늘어났습니다.

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfODYg/MDAxNjU0MjQ4NTg0NTQz.-f6DJdttISuc8ErnitcmKI4U2A3o3hSPw1Fnqi3wnKYg.FoXjX-bT8s7vD0Pmxf7IY9RB8yWzaP_ty-9V5A1WM8Ig.PNG.view7186/SE-cd6c4e8c-a41f-4ccb-822d-b9c7688ad2a8.png?type=w966">


이제 이걸 실행시키고 나서 다시 페이지로 돌아가면

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMjEx/MDAxNjU0MjQ3MjYyNjk0.EJ4HsY2LNWuikBzzVzTDCpnhz82atkY13FZ3DtN7YIgg.Z_9D-xmq8y7x1rfT7qXk6xVjjh9m90B-3OkDPMtKHtAg.PNG.view7186/image.png?type=w966">

이렇게 이쁘게 표시해주고 있습니다.

여기서 저 버그를 클릭하면 다음과 같이 세부 사항을 볼 수 있습니다

<img width="478" alt="image" src="https://postfiles.pstatic.net/MjAyMjA2MDNfMzUg/MDAxNjU0MjQ3NDY0MTE1.FSPTbQarSZnWtErNqzD3mLvlHFAINTIhKlvfhAqH13cg.-4WIArRZRhI9Jg36Xx8FSdF_nYSAQgf7FMe_4yYJ2F0g.PNG.view7186/image.png?type=w966">

끝~~

https://zeddios.tistory.com/976

https://cubenuri.tistory.com/222