# Docker

컨테이너 기반 가상화 도구

리눅스 컨테이너 기술인 LXC 기반

VM 처럼 하드웨어를 가상화해주는 것이 아니라, Guest OS를 Isolation 해준다.

Container에 Host OS와 Container의 OS의 다른 부분이 같이 패키징 된다.

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

