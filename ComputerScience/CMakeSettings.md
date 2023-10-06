# CMake Project for macOS, VSCode

윈도우와 맥이 함께 c++ 플젝을 cmake로 관리하고자 할 때..

맥으로 먼저 만들고 윈도우에 공유하려 했지만 안됐고, 윈도우에서 Visual Studio로 cmake 를 만든 다음

맥에서 다음 링크를 참조해서 맥 환경을 따로 설정했다.

근데 이제 여기서 나는 이미 윈도우가 설정되어있으니 out/build/x86-debug가 있는 상황

그래서 나는 build대신 out/build/macos-debug에 build함

https://popcorn16.tistory.com/31

그리고 주의해야 할 것은 vscode에서 cmake 플러그인으로 빌드하려고 할 때 그 cmake 프로젝트 안으로 들어가야 된다.

![image](https://user-images.githubusercontent.com/57888020/170510049-a043439e-5070-4c53-80e4-98bbd6b85b4a.png)

지금 레포지토리 안 구조가 이런 식인데, 여기서 한번더 안으로 들어가서 빌드해야 함

![image](https://user-images.githubusercontent.com/57888020/170510125-827be1a5-6c46-4942-8fa6-65b8a96939c7.png)


그상태에서 fn+F7누르거나

command+shift+p > CMake: Build 선택

![image](https://user-images.githubusercontent.com/57888020/170510163-29e3c4e0-804b-4324-932d-6d057e0980fb.png)

정상 빌드시 다음과 같이 출력됨

~~~
[build] Build finished with exit code 0
~~~

실행은 다음과 같이 함

![image](https://user-images.githubusercontent.com/57888020/170510200-a57a3a03-a3c4-4f53-99aa-d1ff1c2725ff.png)
