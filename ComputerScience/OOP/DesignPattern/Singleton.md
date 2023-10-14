# 요약
하나의 클래스에 오직 하나의 인스턴스만 가지는 패턴
보통 데이터 베이스 연결 모듈에 많이 사용
(+) 인스턴스 생성 비용 절약
(-) 의존성이 높아짐, 결합이 강해짐 -> [DI](DI)를 통해 모듈간의 결합을 느슨하게 만들어 해결 가능
(-) TDD에서의 걸림돌이 된다. -> 각 테스트마다 독립적인 인스턴스를 만들기 어렵기 때문임

# 싱글톤 패턴
Singleton Pattern
어플리케이션이 시작될 때 어떤 클래스가 최초 1번만 메모리를 할당하고 그 메모리에 [인스턴스](Instance.md)를 만들어서 사용하는 [디자인 패턴](Design_Pattern.md)

즉, 객체의 [인스턴스](Instance.md)가 오직 1개만 생성된다.

인스턴스가 1개만 생성되는 싱글톤 패턴을 이용하면 하나의 인스턴스를 메모리에 등록해서 여러 스레드가 동시에 해당 인스턴스를 공유하여 사용할 수 있게끔 할 수 있기 때문에 요청이 많은 곳에서 사용하면 효율을 높일 수 있다.

만들 때 동시성 문제를 고려해서 설계해야 한다는 주의 사항이 있다.

## 장점
- 메모리 측
- 메모리 낭비 방지 : 최초 한번의 new -> 고정된 메모리 영역 -> 추후 접근 시 메모리 낭비 방지
- 데이터의 쉬운 공유 : 싱글톤으로 만들어진 클래스의 인스턴스는 전역
- 이미 생성된 인스턴스 활용 -> 속도의 이점

인스턴스가 절대적으로 한 개만 존재하는 것을 보증한다.

[DBCP(DataBase Connection Pool)](DBCP.md)처럼 공통된 객체를 여러개 생성해서 사용해야 하는 상황에서 많이 사용

두 번째 이용 시부터는 객체 로딩 시간이 줄어 성능이 좋아진다.

## 단점
- 구현 코드 자체가 많이 필요하다
- 테스트하기 어렵다 : 싱글톤 인스턴스는 자원을 공유 -> 테스트가 격리된 환경에서 수행되려면 매번 인스턴스의 상태를 초기화 해주어야

- 싱글톤 인스턴스가 너무 많은 일을 하거나 많은 데이터를 공유시킬 경우에 다른 클래스의 인스턴스들 간에 결합도가 높아짐
	-> 개방-폐쇄 원칙 위배
	-> 객체 지향 설계 원칙에 어긋남
	-> 수정이 어려워지고 유지보수 비용이 높아짐
	-> 멀티쓰레드 환경에서 동기화 처리를 안하면 인스턴스가 2개 생성될 수 잇는 가능성

- 의존 관계상 클라이언트가 구체 클래스에 의존 : new 키워드로 클래스 안에서 객체를 생성함 -> [SOLID](SOLID.md) 원칙 중 DIP 위반, [OCP](OCP.md) 위반 가능성 높음

- 자식 클래스를 만들 수 없다.
- 내부 상태를 변경하기 어렵다.

따라서 꼭 필요한 경우가 아니라면 싱글톤 패턴은 지양하자

## 예제로 이해하기
```java
public class WhiteBoard {  
    private static WhiteBoard whiteBoard = null;  
    
    private WhiteBoard() {}  
    
    public static WhiteBoard getInstance() {  
        if(whiteBoard == null) {  
            whiteBoard = new WhiteBoard();  
        }  
        return whiteBoard;  
    }  
}
```

기본 생성자를 통해 생성할 수 없기 때문에 외부에서 인스턴스에 접근하려면 

클래스 변수 및 메서드에 접근을 허용해야 하기 때문에 두 메서드는 [정적 타입](static)으로 선언

### 문제점
동시에 이 화이트보드에 접근하는 경우를 생각하자 (여러 스레드가 공유되고 있는 상황)

동시에 화이트보드가 있는지 없는 지를 확인할 수 있다. 어떤 사용자는 화이트보드가 있는데도 불구하고 없다고 생각하고 한번 더 객체를 생성해버릴 수 있다. -> 더이상 싱글톤이 아니다.

아래와 같이 특정 변수를 공유한다면 더 문제가 크다

```java
public class WhiteBoard {  
    private static WhiteBoard whiteBoard = null;  
    private String content = "";  
	
    private WhiteBoard() {}  
    
    public static WhiteBoard getInstance() {  
        if(whiteBoard == null) {  
            whiteBoard = new WhiteBoard();  
        }  
        return whiteBoard;  
    }  
	
    public void print() {  
        content += "ㅁ";  
        System.out.println(content);  
    }  
}
```

content 값은 여러 스레드가 공유하고 있는데 서로 다른 프로세스에서 처리되고 있다. -> 값이 일관되지 않을 수 있다.

### 해결 방법

이런 멀티 스레드 환경에서 싱글톤의 문제를 해결할 수 있는 방법은 두가지가 있다.

1. 정적 변수에 인스턴스를 만들어 바로 초기화
2. 인스턴스를 만드는 메서드에 동기화

#### 정적 변수에 인스턴스를 만들어 바로 초기화

객체가 생성되기 전 클래스가 메모리에 로딩할 때 만들어져 초기화가 한 번만 실행

-> 조건문으로 존재 유무를 체크하지 않아도 되므로 문제 원천 차단

#### 인스턴스를 만드는 메서드에 동기화

하지만 여전히 content에 대해서는 문제가 해결되지 않았음

`synchronized` 라는 키워드를 통해 여러 쓰레드에서 동시에 접근하는 것을 막을 수 있다.

```java
public class WhiteBoard {  
    private static WhiteBoard whiteBoard = new WhiteBoard;  
    private static String content = "";  
	
    private WhiteBoard() {}  
    
    public static WhiteBoard getInstance() {  
        return whiteBoard;  
    }  
	
    public synchronized static void print() {  
        content += "ㅁ";  
        System.out.println(content);  
    }  
}
```

그런데 인터페이스를 구현하는 경우에는 이 두가지 방법들을 사용할 수 없다.

-> 인터페이스는 정적 메소드를 가질 수 없다.


