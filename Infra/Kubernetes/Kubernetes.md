# Kubernetes

## 설치가 어려운 이유

k8s에 들어가 있지 않은 것
- etcd : 오픈 소스 -> 알아서 구축
- k8s maste : stateless -> Clustering과 같은 HA기능 x
- node에서 제공하는 것들 : Kublet, Kube-proxy -> 나머지(container runtime, OS) 제공 x