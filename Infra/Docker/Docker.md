# Docker

컨테이너 기반 가상화 도구

리눅스 컨테이너 기술인 LXC 기반

VM 처럼 하드웨어를 가상화해주는 것이 아니라, Guest OS를 Isolation 해준다.

Container에 Host OS와 Container의 OS의 다른 부분이 같이 패키징 된다.

## version
```sh
docker version
```

```
Client:
 Cloud integration: v1.0.35
 Version:           24.0.2
 API version:       1.43
 Go version:        go1.20.4
 Git commit:        cb74dfc
 Built:             Thu May 25 21:51:16 2023
 OS/Arch:           darwin/arm64
 Context:           desktop-linux

Server: Docker Desktop 4.21.1 (114176)
 Engine:
  Version:          24.0.2
  API version:      1.43 (minimum version 1.12)
  Go version:       go1.20.4
  Git commit:       659604f
  Built:            Thu May 25 21:50:59 2023
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.6.21
  GitCommit:        3dce8eb055cbb6872793272b4f20ed16117344f8
 runc:
  Version:          1.1.7
  GitCommit:        v1.1.7-0-g860f061
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

```

도커는 하나의 실행 파일이지만 위처럼 Client와 Server로 나누어져있다.

도커 커맨드를 입력하면 도커 클라이언트가 도커 서버로 명령을 전송하고 결과를 받아 터미널에 출력

![](https://i.imgur.com/deuU3F7.png)



## install

```zsh
brew install --cask docker
```

### Error

```
Error: It seems there is already a Binary at '/usr/local/bin/docker'.
```

```zsh
brew remove docker
```

이렇게 했더니 다음과 같은 오류 만남

```
Error: Cask 'docker' is not installed.
```

결국 --force 명령으로 설치

```
brew install --cask docker --force
```

