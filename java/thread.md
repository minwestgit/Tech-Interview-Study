## 쓰레드 구현 방법

### 1. Runnable 인터페이스 구현

```java
public class MyThread implements Runnable {
  @Override
  public void run(){
    // 수행 코드.
  }
}

public static void main(String[] args){
  Runnable runnable = new MyThread();
  Thread t = new Thread(runnable, "mythread");
}
```

- Runnable 인터페이스를 구현하므로 다른 클래스를 상속받을 수 있다.
- run() 메소드를 오버라이드 하면 된다.
- 다만, start() 메소드가 없기 때문에 Runnable 인터페이스를 구현한 클래스의 객체를 만들어 Thread를 생성할 때, 생성자의 매개변수로 넘겨주고 쓰레드 객체의 start() 메소드를 수행한다.
<br>

### 2. Thread 클래스 상속

```java
public class MyThread extends Thread {

  public void run(){
    // 수행 코드.
  }
}
```

- Thread 클래스를 상속받으면 다른 클래스를 상속받지 못한다.(다중 상속 불가능 - 자바의 특징)
- run() 메소드를 직접 구현해야 한다.
- 또한, Thread 클래스를 상속받으면 스레드 클래스의 메소드를 바로 사용할 수 있지만, Runnable 구현의 경우 Thread 클래스의 static 메소드인 currentThread()를 호출해 현재 스레드에 대한 참조를 얻어와야만 호출이 가능하다.
<br>

#### 스레드의 실행을 run()이 아닌 start()로 하는 이유
start() 메소드를 호출하면 JVM은 알아서 스레드를 위한 콜 스택을 새롭게 만들어주고 context switching을 통해 스레드답게 동작하도록 해준다. start()는 스레드가 작업을 실행하는 데 필요한 콜 스택을 생성한 다음 run()을 호출해서 그 스택 안에 run()을 저장할 수 있도록 해준다.
