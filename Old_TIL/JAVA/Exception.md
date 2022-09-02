## JAVA Exception

JAVA에서는 오류가 있다면 Exception이라는 예외가 발생시킨다.

예를 들어서 숫자를 0으로 나누면 ArithmetricException, 존재하지 않는 파일을 열려고 한다면 FileNotFoundException이라는 이름의 예외가 발생한다.

그리고 예외가 발생하면 프로그램을 중단하고 오류 메시지를 보여준다.


예외 처리는 try catch 구문으로 수행할 수 있다.

~~~
try {
    ...
} catch(예외1) {
    ...
} catch(예외2) {
    ...
...
} finally {
    ...
}
~~~

try 문 안의 수행할 문장들에서 예외가 발생하면 해당 예외의 catch문이 수행된다.

배열에서 인덱스의 범위를 넘어가는 예외는 ArrayIndexOutOfBoundException인데,

이 경우 커스텀 오류구문을 출력하고 싶다면 다음과 같이 작성하면 된다.

~~~
int[] array = {1, 2, 3};
try {
    System.out.println(a[3]);
} catch (ArrayIndexOutOfBoundException e) {
    System.err.println("배열의 인덱스 범위를 벗어났습니다.");
} finally {
    System.out.println("finally 구문입니다.");
}
~~~

이때 e는 ArrayIndexOutOfBoundException 클래스의 객체로, 오류 객체라고 한다.

그리고 finally 구문은 예외처리 발생 여부와 상관없이 무조건 수행된다.


그런데 이때 예외를 직접 만들어보고 활용할 수도 있다.


만약에 String을 입력 받으려고 하는데 그 길이가 10이 넘어가면 안된다고 하자

~~~
public class Example {
    public void inputString(String str) {
        if(str.length() > 10) {
            return;
        }
        System.out.println("입력한 String은 "+str+" 입니다.");
    }

    public static void main(String[] args) {
        Example ex = new Example();
        ex.inputString("this is long string");
        ex.inputString("OK");
    }
}
~~~

이렇게 해당 조건의 경우에 return이 되게끔 해도 되지만 적극적으로 예외를 발생시킬 수 도 있다.

위 파일에 LengthException 클래스를 작성하고 return 대신에 예외를 던져주게 하면 다음과 같다.

~~~
class LengthException extends RuntimeException {
}

public class Example {
    public void inputString(String str) {
        try {
            if(str.length() > 10) {
                throw new LengthException();
            }
            System.out.println("입력한 String은 "+str+" 입니다.");
        } catch(LengthException e) {
            System.err.println("LengthException 발생");
        }
    }

    public static void main(String[] args) {
        Example ex = new Example();
        ex.inputString("this is long string");
        ex.inputString("OK");
    }
}
~~~

try catch 문으로 예외를 처리한다.


메소드가 그 밖으로 예외를 던질수도 있다.

그 경우에는 throws를 사용한다. 이 경우 "예외를 뒤로 미루기"라고 한다.

~~~
class LengthException extends RuntimeException {
}

public class Example {
    public void inputString(String str) throws LengthException {
        if(str.length() > 10) {
            throw new LengthException();
        }
        System.out.println("입력한 String은 "+str+" 입니다.");
    }

    public static void main(String[] args) {
        Example ex = new Example();
        ex.inputString("this is long string");
        ex.inputString("OK");
    }
}
~~~

이렇게 되면 예외를 처리해야 하는 대상이 main 메소드가 되므로 main 메소드에서 컴파일 에러가 발생한다.

main 메소드를 다음과 같이 변경해서 에러를 해결할 수있다.

~~~
class LengthException extends RuntimeException {
}

public class Example {
    public void inputString(String str) throws LengthException {
        if(str.length() > 10) {
            throw new LengthException();
        }
        System.out.println("입력한 String은 "+str+" 입니다.");
    }

    public static void main(String[] args) {
        Example ex = new Example();
        try {
            ex.inputString("this is long string");
            ex.inputString("OK");
        } catch(LengthException e) {
            System.err.println("LengthException 발생");
        }
    }
}
~~~

inputString 메소드에서 예외 처리를 하는 경우, 두 개의 inputString 호출에서 첫번째는 예외가 발생하지만 다음 호출은 수행된다.

그런데 main 메소드에서 예외 처리를 하는 경우, 첫번째에서 예외가 발생하고 catch문으로 빠지기 때문에 두번째 호출이 수행되지 않는다.


그래서 Exception을 처리하는 위치는 중요하다.

프로그램의 수행 여부를 결정하고, 트랜잭션 처리와 밀접한 관계가 있기 때문이다.

그래서 예외처리는 프로그램의 부분만 알아서는 안되고 전체를 관통하여 모두 알아야만 정확히 할 수 있다.

