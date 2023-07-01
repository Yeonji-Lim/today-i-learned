# application.yml
action에서 따로 빼둔 application-secret.yml을 적용하려고 하니까 자꾸 안됐다.
원인은 application-secret.yml 위치 때문인데, echo 가 잘못 만들어져서 그런 것일 수도 있다.

```
- name: Set up application-secret.yml  
  env:  
    DB_URL: ${{ secrets.DB_URL }}  
    DB_USERNAME: ${{ secrets.DB_USERNAME }}  
    DB_PASSWORD: ${{ secrets.DB_PASSWORD }}  
  run: |  
    echo "spring:  
      datasource:  
        url: $DB_URL  
        username: $DB_USERNAME  
        password: $DB_PASSWORD  
        driver-class-name: com.mysql.cj.jdbc.Driver" > application-secret.yml
```

그냥 아예 시크릿에 파일 내용을 넣어버리고 그걸 가져오는 형식으로 했다.

```
runs-on: ubuntu-latest  
env:  
  working-directory: ./  
  APP_SECRET: ${{ secrets.APP_SECRET }}  
  
steps:  
  - uses: actions/checkout@v3  
  
  - name: Set up JDK 17  
    uses: actions/setup-java@v3  
    with:  
      java-version: '17'  
      distribution: 'corretto'  
  
  - name: Cache Gradle packages  
    uses: actions/cache@v2  
    with:  
      path: ~/.gradle/caches  
      key: ${{ runner.os }}-gradle-${{ hashFiles('**/*.gradle*', '**/gradle-wrapper.properties') }}  
      restore-keys: |  
        ${{ runner.os }}-gradle-  
  
  - uses: actions/checkout@v2  
  - run: touch ./src/main/resources/application-secret.yml  
  - run: echo -e "${{env.APP_SECRET}}" > ./src/main/resources/application-secret.yml  
  - uses: actions/upload-artifact@v2  
    with:  
      name: application-secret.yml  
      path: ./src/main/resources/application-secret.yml
```