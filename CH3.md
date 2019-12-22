# 3 인터페이스와 람다 표현식
## 3.1 인터페이스
리모콘 같은 존재로 이해하면 된다.
버튼을 만들어두는 것.
실제 어떻게 동작할지는 후에 어떻게 구현하는지에 달려있다.
### 3.1.1 인터페이스 선언
기본 구현을 해도 되고 안해도 된다.
기본 구현을 안하고 선언함 한 메서드를 추상(abstract) 메서드라고 한다.
인터페이스의 모든 메서드는 자동으로 public이 된다.
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
### 3.1.7 상수
## 3.2 인터페이스의 정적 메서드, 기본 메서드, 비공개 메서드
### 3.2.1 정적 메서드
### 3.2.2 기본 메서드
### 3.2.3 기본 메서드의 충돌 해결
### 3.2.4 비공개 메서드
## 3.3 인터페이스의 예
### 3.3.1 Comparable 인터페이스
### 3.3.2 Comparator 인터페이스
### 3.3.3 Runnable 인터페이스
### 3.3.4 사용자 인터페이스 콜백
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
