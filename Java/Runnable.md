# Runnable
구현할 메소드가 `run()` 하나 뿐인 [함수형 인터페이스](Functional_Interface) 
-> [람다](Lambda)로 깔끔하게 구현 가능

구현체를 호출하려면 Runnable 형 인자를 받는 생성자를 통해 별도의 Thread 객체를 생성하고 start() 메소드를 호출해야 한다.

```java
Thread thread1 = new MyThread();
thread1.setName("Thread #1");

Runnalbe runnable1 = new MyRunnable();
Thread thread2 = new Thread(runnable1);
thread2.setName("Thread #2");

thread1.start();
thread2.start();
```

