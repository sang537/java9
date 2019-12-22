# 2 객체 지향 프로그래밍
## 2.1 객체 사용
  함수(function)와 다른 점: 상태(status)를 지닌다.<br>
  캡슐화: 객체의 메서드 내부에서 무슨 일이 일어나는지 몰라도 된다는 원칙
### 2.1.1 접근자 메서드와 변경자 메서드
  호출되는 객체를 변경하는 메서드는 변경자(mutator)라고 하고<br>
  변경하지 않는 메서드를 접근자(accessor)라고 한다.
### 2.1.2 객체 참조
## 2.2 클래스 구현
### 2.2.1 인스턴스 변수
  인스턴스 변수로 객체의 상태를 나타낸다.<br>
  주로 private처리 한다.
### 2.2.2 메서드 헤더
### 2.2.3 메서드 바디
### 2.2.4 인스턴스 메서드 호출
### 2.2.5 this 참조
### 2.2.6 값을 사용한 호출
<pre>
<code>
  public void replaceWithZombie(Employee e){
    e = new Employee(“”, 0);
  }
</code>
</pre>
  이렇게 해도 받은 e 객체가 변하지 않는다.<br>
  그냥 e에 새로운 참조가 설정될 뿐..
## 2.3 객체 생성
### 2.3.1 생성자 구현
이름이 클래스와 같고, 반환 타입이 없다.
<pre>
<code>
public Employee(String name, double salary){
this.name = name;
this.salary = salary;
}
</code>
</pre>
### 2.3.2 오버로딩 (Overloading: 중복 정의)
이름은 같지만 매개변수가 다른 메서드가 여러 개
### 2.3.3 다른 생성자에서 특정 생성자 호출
호출하는 쪽 생성자 바디의 첫 번째 문장으로만 허용한다.<br>
호출할 생성자 이름이 아니라 this 키워드 사용
<pre>
<code>
public Employee(double salary){
  this(“”, salary); // Employee(String, double)을 호출한다.
  // 이 this는 생성될 객체 참조가 아니다. 같은 클래스에 속한 다른 생성자를 호출할 때 사용하는 특수 문법이다.
  // 이후에 다른 문장 올 수 있다.
}
</code>
</pre>
### 2.3.3 기본 초기화
숫자는 0, 불 값은 false, 객체 참조는 null
### 2.3.4 인스턴스 변수 초기화
초기화 블록
### 2.3.5 최종 인스턴스 변수
참조 자체가 변하지 않는다는 것<br>
다른 객체로 변경할 수 없다는 것이지<br>
내용을 변경하는 것은 얼마든지 가능하다 (ex. ArrayList<>)
### 2.3.6 인수 없는 생성자
## 2.4 정적 변수와 정적 메서드 (static)
### 2.4.1 정적 변수
특정 인스턴스가 아닌 클래스 자체에 속한다.
### 2.4.2 정적 상수
Math.PI가 대표적
난수 생성기(Random) 등을 클래스에 만들어놓고 인스턴스에서 사용하기도 함<br>
매 번 호출하지 않아도 되어서 효율적
### 2.4.3 정적 초기화 블록 (static initialization block)
클래스를 처음 로드할 때 일어난다.<br>
주로 정적 변수를 초기화할 때 쓰는 듯 (ArrayList 등)
### 2.4.4 정적 메서드
Math.pow가 대표적<br>
왜 Math math = new Math를 안 하는 걸까?<br>
어차피 그 계산할 때 math라는 객체를 활용하지 않기 때문에 볼품없다고 여긴다
### 2.4.5 팩토리 메서드
[장점]<br>
서브클래스의 객체를 반환할 수 있다.<br>
공유 객체를 반환할 수 있다
## 2.5 패키지 (잘 모르겠음 이 부분)
### 2.5.1 패키지 선언
### 2.5.2 jar 명령
### 2.5.3 클래스 패스
### 2.5.4 패키지 접근
protected: 같은 패키지 내
### 2.5.5 클래스 임포트
### 2.5.6 정적 임포트
이렇게 하면 Math.pow를 그냥 pow로 사용할 수 있게 되는 것<br>
다수의 정적 메서드를 제공하는 클래스를 사용할 때 보통 정적 임포트 선언을 한다
## 2.6 중첩 클래스
### 2.6.1 정적 중첩 클래스 (static)
### 2.6.2 내부 클래스 (static 없음)
정적 중첩 클래스와의 차이는 내가 어떤 인스턴스 소속인지 알게 된다는 점
### 2.6.3 내부 클래스용 특수 문법 규칙
<pre>
<code>
public class Network {
  public class Member {
  …
    public Boolean belongTo(Network n) {
      return Network.this == n;
    }
  }
}
</code>
</pre>
## 2.7 문서화 주석
### 2.7.1 주석 넣기
/**로 시작 */로 끝<br>
태그는 @로 시작<br>
자유 형식 텍스트의 첫 번째 문장: 요약문
### 2.7.2 클래스 주석
@author<br>
@version
### 2.7.3 메서드 주석
@param<br>
@return<br>
@throws
### 2.7.4 변수 주석
공개 변수만 문서화
### 2.7.5 일반 주석
@since (ex. @since version 1.7.1)<br>
@deprecated (ex. @deprecated Use <code>setVisible(true)</code> instead
### 2.7.6 링크
@see package.Class#feature label (ex. @see com.samsung.Employee#raiseSalary(double))<br>
앵커 태그도 사용 가능
### 2.7.7 패키지 주석, 모듈 주석, 개요 주석
패키지 디렉터리에 자바 파일 package-info.java를 추가한다. <br>
첫 부분에는 /** */로 구분한 자바독 주석이 있어야 하고, 그 뒤에는 패키지 문이 있어야 한다. <br>
패키지 문 뒤에는 코드나 주석을 적지 말아야 한다.<br>
모듈을 문서화하려면 module-info.java 파일에 주석을 넣어야 한다. <br>
@moduleGraph 지시문을 사용하면 모듈 의존성 그래프를 넣을 수 있다.<br>
개요 주석은 overview.html 파일에 넣는데, 이 파일은 모든 소스 파일이 들어 있는 부모 디렉터리에 만든다. <br>
이 주석은 사용자가 내비게이션 바에서 개요를 선택하면 표시된다.
### 2.7.8 주석 내보내기
문서화하려는 소스 파일이 있는 디렉터리로 이동한다.<br>
<pre>
<code>
$javadoc –d docDirectory package1 package2 …
</code>
</pre>
