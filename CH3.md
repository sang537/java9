# 3 인터페이스와 람다 표현식
## 3.1 인터페이스
리모콘 같은 존재로 이해하면 된다.<br>
버튼을 만들어두는 것.<br>
실제 어떻게 동작할지는 후에 어떻게 구현하는지에 달려있다.
### 3.1.1 인터페이스 선언
기본 구현을 해도 되고 안해도 된다.<br>
기본 구현을 안하고 선언함 한 메서드를 추상(abstract) 메서드라고 한다.<br>
인터페이스의 모든 메서드는 자동으로 public이 된다.<br>
따라서 선언 안해줘도 된다.
### 3.1.2 인터페이스 구현
<pre>
<code>
public class ClassName implements InterfaceName {
  public returntype methodname() {
    인터페이스 내의 메서드는 public 안해줘도 public 이지만, 구현할 때는 무조건 public 붙여줘야 한다.
  }
}
</code>
</pre>
### 3.1.3 인터페이스 타입으로 변환 (서브타입 -> 슈퍼타입)
<pre>
<code>
인터페이스가 클래스의 슈퍼타입
InterfaceName variable = new Class which implements the interface();
</code>
</pre>
### 3.1.4 캐스트와 instanced 연산자 (슈퍼타입 -> 서브타입)
<pre>
<code>
Interface if = new Class();
if(if instanceof Class) {
  Class class = (Class) if;
}
</code>
</pre>
### 3.1.4 인터페이스 확장 (extends)
Channel 인터페이스를 구현하는 클래스는 두 메서드를 모두 구현해야 하며, 두 인터페이스 타입 중 어느 것으로도 객체를 변환할 수 있다.
<pre>
<code>
public interface Closeable {
  void close();
}
public interface Channel extends Closeable { 
  boolean isOpen();
}
</code>
</pre>
### 3.1.6 여러 인터페이스 구현
클래스는 인터페이스를 몇 개든 구현할 수 있다.
<pre>
<code>
public class FileSequence implements IntSequence, Closeable {
  ...
}
</code>
</pre>
이렇게 구현하면 FileSequence 클래스는 IntSequence와 Closeable을 슈퍼타입으로 둔다.
### 3.1.7 상수
인터페이스 안에는 인스턴스 변수를 둘 수 없다.<br>
인터페이스는 객체의 상태가 아니라 동작을 명시한다.<br>
따라서 인터페이스에 정의한 변수는 자동으로 public static final이 된다.
## 3.2 인터페이스의 정적 메서드, 기본 메서드, 비공개 메서드
자바 8 이전에는 인터페이스의 모든 메서드가 추상 메서드여야 했다. 메서드의 바디가 없어야만 했다.<br>
자바 9에서는 실제 구현이 있는 메서드 세 정류 (정적, 기본, 비공개)를 인터페이스에 추가할 수 있다.<br>
### 3.2.1 정적 메서드
팩토리 메서드는 특히 인터페이스에 아주 잘 맞는다.<br>
예전에는 정적 메서드를 동반 클래스에 두었다. Colletion/Collections같이.<br>
그런데 이제 이런 분할이 필요 없다.
### 3.2.2 기본 메서드
default 제어자를 붙여야 한다.<br>
이 인터페이스를 구현하는 클래스는 오버라이드하거나 기본 구현을 상속하는 방법 중 하나를 택.<br>
기본 메서드의 주요 용도는 인터페이스의 진화. <br>
만약에 기존에 있던 인터페이스에 새로운 기본 메서드를 추가했다고 가정해보자.<br>
여기에 기본 메서드라는 개념을 적용시키지 않는다면,<br>
이미 해당하는 인터페이스를 implement하고 있는 클래스들은 다 호환에 문제가 생기게 된다.
### 3.2.3 기본 메서드의 충돌 해결
두 개 이상의 인터페이스를 구현할 때 기본 메서드들의 이름 및 매개변수 타입이 같은 경우 <br>
이 때는 더 정확하게 지정해주면 된다.
<pre>
<code>
public class Employee implements Person, Identified {
  public int getId() { return Identified.super.getId(); }
}
</code>
</pre>
### 3.2.4 비공개 메서드
비공개 메서드는 static이나 인스턴스 메서드는 될 수 있지만, default 메서드는 될 수 없다. (오버라이드가 가능하므로) <br>
비공개 메서드는 인터페이스 자체에 있는 메서드에서만 쓸 수 있으므로 인터페이스 안에 있는 다른 메서드의 헬퍼 메서드로만 사용할 수 있다.
## 3.3 인터페이스의 예
### 3.3.1 Comparable 인터페이스
### 3.3.2 Comparator 인터페이스
### 3.3.3 Runnable 인터페이스
<pre>
<code>
class HelloTask implements Runnable {
  public void run() {
    for (int i = 0; i < 1000; i++) {
      System.out.println("Hello, World!");
    }
  }
}

Runnable task = new HelloTask();
Thread thread = new Thread(task);
thread.start();
</code>
</pre>
### 3.3.4 사용자 인터페이스(GUI) 콜백

## 3.4 람다 표현식
### 3.4.1 람다 표현식 문법
### 3.4.2 함수형 인터페이스
## 3.5 메서드 참조와 생성자 참조
### 3.5.1 메서드 참조
### 3.5.2 생성자 참조
## 3.6 람다 표현식 처리
### 3.6.1 지연 실행 구현
### 3.6.2 함수형 인터페이스 선택
### 3.6.3 독자적인 함수형 인터페이스 구현
## 3.7 람다 표현식과 변수 유효 범위
### 3.7.1 람다 표현식의 유효 범위
### 3.7.2 람다 표현식을 감싸는 유효 범위에 속한 변수 접근
## 3.8 고차 함수
### 3.8.1 함수를 반환하는 메서드
### 3.8.2 함수를 수정하는 메서드
### 3.8.3 Comparator 인터페이스의 메서드
## 3.9 지역 클래스와 익명 클래스
### 3.9.1 지역 클래스
### 3.9.2 익명 클래스
