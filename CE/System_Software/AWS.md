# AWS

## 특징


## 구축(EC2)
### public IPv4 Address
해당 서버의 주소
-> 외부에서 접근하기 위해서 사용하는 주소로, 그 값이 바뀔 수도 있다.
그런데 바뀌지 않는 고정주소를 부여하고 싶다면 탄력적 IP를 부여하는 것

### Elastic IP
적절한 IP 주소를 필요할 때 할당받음

### 접속하기
```shell
chmod 400 [키페어_이름].cer
ssh -i [키페어_이름].cer ubuntu@[public_ip]
```
