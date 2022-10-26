# 컨트롤러를 테스트하는 2가지 방법

## @SpringBootTest + @AutoConfigureMockMvc

1. 전체 Bean을 모두 생성
2. MockMvc를 통해 http 요청과 검증을 진행

## @WebMvcTest

내가 필요로 하는 MVC관련 Bean들만 생성한다.

- Controller, ControllerAdvice, Converter, Filter, HandlerInterceptor
- Service등 Controller에 의존하는 하위 레이어의 기능은 @MockBean을 통해 모킹해서 원하는 동작을 하도록 한다. (Mockito와 유사한 방식)