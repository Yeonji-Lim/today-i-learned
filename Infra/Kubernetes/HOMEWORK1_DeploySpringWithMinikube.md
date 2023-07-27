```
eval $(minikube docker-env)
```

minikube docker-env
-> minikube 클러스터 내에서 실행되는 도커 데몬을 가리키도록 도커 환경을 구성한다. 

$()
-> 명령 대체. 괄호안의 명령을 실행하고 해당 명령의 출력으로 바꿈

eval
-> $(minikube docker-env)의 출력을 가져오고, 이를 쉘의 명령으로 취급한다.

eval 없이 그냥 minikube docker-env을 실행하면 환경 변수 설정만 표시되지만 현재 쉘 세션에 적용되지 않는다. 

eval을 사용하면 환경 변수 변경 사항을 쉘 세션에 효과적으로 적용, Minikube의 Docker 데몬을 마치 로컬의 Docker 데몬인 것 처럼 사용 가능