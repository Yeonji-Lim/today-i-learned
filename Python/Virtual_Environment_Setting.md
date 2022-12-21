# 가상환경 생성, 실행, 종료

## virtualenv 사용

```shell
brew install virtualenv
```

가상환경을 설정하고자 하는 위치로 이동하여 다음의 명령 입력

```shell
virtualenv [가상환경 이름]
```

다음의 명령으로 가상환경 실행

```shell
source [가상환경 이름]/bin/activate
```

`deactivate //` 입력시 종료

## python, python3 사용

python 명령으로 가상환경을 생성할 수 있다.

```
python -m venv [가상환경 이름]

# or

python3 -m venv [가상환경 이름]
```

그런데 이때 python 으로 만들어서 설치가 가능한 패키지와

python3 로 만들어서 설치가 가능한 패키지가 다르다.

python으로 가상환경을 만들었다가 다른 팀원은 되는 버전의 패키지가 나만 설치가 안되는 경험을 겪음 - AssetGenerator