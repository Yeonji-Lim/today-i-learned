# authorizationGrantType cannot be null

![](https://i.imgur.com/ATD3Bjh.png)

```
security:  
    oauth2.client:  
        registration:
            kakao:
	            client_id:   
				redirect_uri:   
				client-authentication-method: POST  
				authorization-grant-type: authorization_code  
				scope: profile_nickname, account_email  
				client-name: Kakao
```

위와 같이 `authorization-grant-type` 의 값이 들어가야 함