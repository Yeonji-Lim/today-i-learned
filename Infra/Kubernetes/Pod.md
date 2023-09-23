# Pod
가장 기본적인 배포단위, 컨테이너를 포함하는 단위

```yaml
apiVersion: v1
kind: Pod
metadata:
 name: nginx
spec:
 containers:
 - name: nginx
   image: nginx:1.7.9
   ports:
   - containerPort: 8090
```
