# Port
운영 체제 통신의 종단점

```plaintext
기본 지정 포트
http : 80, https: 443, ssh: 22, sftp: 21, mysql: 3306
```

포트는 항상 열려 있지 않음 (http의 80은 열려있음)
	→ 그렇기 때문에 열려있는지, 인바운드 아웃바운드는 잘 구성이 되어있는지 확인해야함

## 포트는 어디까지 열어야 할까?
두군데서 열어야 합니다.

-   os : 방화벽
-   공유기 : 방화벽, 포트포워딩
-   클라우드(AWS) : 보안그룹설정(방화벽), 포트포워딩(인바운드, 아웃바운드)