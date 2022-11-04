# Jackson

자바용 Json/XML/YAML/CSV 형식의 데이터를 지원하는 data-processing library

- 스트림 방식이므로 속도가 빠르고 유연하다 
- 다양한 third party 데이터 타입을 지원함
- annotation 방식으로 메타 데이터 기술
	-> JSON의  약점 중 하나인 문서화와 데이터 validation 문제 해결 가능

## Class에서 Json으로 변경
Jackson을 사용해서 class 변수를 자동으로 json 형태로 변환해줄 수 있음
그런데 이때 다음과 같은 조건을 만족해야 함

-   Class에 @RestController가 있어야 함
-   Class에 @Controller가 붙어있다면 Function에 @ResponseBody가 있어야 함

## Jackson Property

### @JsonIgnore
읽지 않음
적용하고 싶은 변수 상단에 작성

### @JsonInclude
다음의 코드로 null이 아닌 것만 포함할 수 있음
클래스 상단에 다음과 같이 작성
`@JsonInclude(JsonInclude.Include.NOT_NULL)`

- ALWAYS : 속성의 값에 의존하지 않고 항상 포함
- NOT_EMPTY : null 또는 빈 값이 아니면 포함
- NOT_NULL : null이 아니면 포함
- NOT_DEFAULT : bean의 기본 생성자로 정의된 필드값과 다르게 변경된 필드만 포함

### @JsonProperty
클래스의 프로퍼티 이름을 변경해서 보여주고 싶을 때 사용
해당 변수의 상단에 작성
`@JsonProperty(value=변경하고자 하는 이름)`

### @JsonFormat
날짜, 시간 값을 직렬화할 때 형식 지정
해당 변수의 상단에 작성
`@JsonFormat(shape=JsonFormat.Shape.STRING, pattern="yyyy-MM-dd")`

## 장점
- 모든 JAX-RS 및 Spring Framework에 내장
- 광범위한 annotation을  지원

Spring boot에서는 jackson을 선택한 것 같다. 
jackson을 기본으로 사용하고, 더 간단히 작업하고 싶을 때 [gson](GSON)을 사용하면 될 것 같다. 