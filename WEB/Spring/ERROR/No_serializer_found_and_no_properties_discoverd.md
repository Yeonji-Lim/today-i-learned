```
No serializer found for class com.example.alcoholfreeback.src.recommend.model.Message and no properties discovered to create BeanSerializer (to avoid exception, disable SerializationFeature.FAIL_ON_EMPTY_BEANS) (through reference chain: com.example.alcoholfreeback.src.recommend.model.ChatGPTReq["messages"]->java.util.ArrayList[0])
```

저 Message 클래스에 JsonProperty 붙여야 함

이 오류는 Spring Boot가 Message 클래스를 직렬화하지 못하기 때문에 발생합니다. Message 클래스에 직렬화기가 없거나 BeanSerializer를 생성하기 위해 발견된 속성이 없기 때문입니다. 이 문제를 해결하려면 다음을 수행하십시오.

- Message 클래스에 직렬화기를 추가
- BeanSerializer를 생성하기 위해 발견된 속성을 추가
- SerializationFeature.FAIL_ON_EMPTY_BEANS를 비활성화

Message 클래스에 직렬화기를 추가하려면 다음을 수행하십시오.

1. Message 클래스에서 @Serializble 애노테이션을 추가합니다.
2. Message 클래스의 모든 속성에 @Serializble 애노테이션을 추가합니다.

BeanSerializer를 생성하기 위해 발견된 속성을 추가하려면 다음을 수행하십시오.

1. Message 클래스의 모든 속성에 @JsonProperty 애노테이션을 추가합니다.

SerializationFeature.FAIL_ON_EMPTY_BEANS를 비활성화하려면 다음을 수행하십시오.

1. Spring Boot 애플리케이션의 application.properties 파일에 다음 속성을 추가합니다.

```
spring.jackson.serialization.fail-on-empty-beans=false
```