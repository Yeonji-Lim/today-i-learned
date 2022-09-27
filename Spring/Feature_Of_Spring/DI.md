# Dependency Injection
의존성 주입
객체의 의존 관계를 외부에서 넣어주는 것을 말한다.

Spring에서는 모든 클래스의 메소드에서 같은 오브젝트를 공유해서 사용할 수 있다.

[IoC](IoC)원칙을 실현하기 위한 [디자인 패턴](Design_Pattern.md) 중 하나 이다.

## DI를 하는 두 가지 방법
### 1. [Component Scan](Component_Scan.md) 과 자동 의존관계 설정
- Component Scan으로 스프링 빈을 등록한다.
  
- 생성자에 `@Autowired`를 사용하면 객체 생성 시점에 스프링 컨테이너에서 해당 스프링 빈을 찾아서 의존성을 주입한다.
  이때 생성자가 1개만 있으면 `@Autowired` 생략가능 

### 2. 자바 코드로 직접 스프링 빈 등록

