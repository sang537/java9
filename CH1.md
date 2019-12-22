# 1 기본 프로그래밍 구조
## 1.1 첫 번째 프로그램
### 1.1.1 “Hello, World” 프로그램 파헤치기
객체는 특정 클래스에 속하며 그 객체를 클래스의 인스턴스라고 한다.
### 1.1.2 자바 프로그램 컴파일 및 실행
JDK (Java Development Kit) <br>
IDE (Integrated Development Environment)<br>
실행 단계<br>
바이트 코드로 컴파일해서 클래스 파일에 저장<br>
가상 머신을 구동하고 클래스 파일을 로드해서 바이트 코드를 실행<br>
한 번 작성하고, 어디서나 실행한다.<br>
$javac ch01/sec01/HelloWorld.java 컴파일러는 파일 이름으로 실행<br>
$java ch01.sec01.HelloWorld 가상 머신은 클래스 이름으로 실행
### 1.1.3 메서드 호출
System.out은 객체, PrintStream의 인스턴스<br>
PrintStream 클래스에는 println, print 등 메서드가 존재<br>
해당 클래스의 객체에서 작동하므로 인스턴스 메서드라고 함<br>
인스턴스 메서드를 호출하려면 점(.) 표기법을 사용<br>
Object.methodName(arguments)<br>
문자열은 String 클래스의 인스턴스<br>
String 클래스에는 String 객체의 길이 반환하는 length 메서드 존재<br>
System.out과 String 객체는 바로 사용할 수 있게 미리 준비된 객체이고 대부분은 생성(construct) 해야 한다.
### 1.1.4 JShell 실행 (자바9의 또 다른 방식의 실행 방법)
REPL(Read-Evaluate-Print-Loop) 제공<br>
입력된 모든 표현식의 값을 자동으로 출력(sysout하지 않아도)
## 1.2 기본 타입 (8개)
### 1.2.1 부호 있는 정수 타입 (4개)
	long 정수 리터럴은 접미어 L을 붙임. (ex. 4000000000L)
	byte나 short 타입 리터럴을 작성하는 문법은 없음 따라서 캐스트 표기법 씀
	(ex. (byte) 127 )
	16진수 리터럴에는 접두어 0x를 붙임 (ex. 0xCAFEBABE)
	2진수 값에는 접두어 0b를 붙인다 (ex. 0b1001은 9)
	숫자 리터럴은 밑줄(_)을 붙일 수 있다. (ex. 1_000_000 = 1000000)
### 1.2.2 부동소수점 타입 (2개)
	float 타입 숫자에는 접미어 F를 붙인다 안붙이면 double로 됨
	double 타입 리터럴에는 접미어 D를 선택적으로 붙일 수 있다
	Double에는 POSITIVE_INFINITY, NEGATIVE_INFINITY, NaN(Not a Number)등이 있다
	숫자가 아닌 값은 모두 서로 다른 값으로 간주한다.
	if(Double.isNaN(x))로 검사해야 한다. if(x == Double.NaN)는 검사가 제대로 안된다.
	부동소수점 수는 정확한 계산이 안된다. 2진수 체계로 나타내기 때문이다.
	정확한 계산이 필요한 경우에는 BigDecimal 클래스를 사용해야 한다.
### 1.2.3 char 타입 (1개)
\n : 줄 넘김<br>
\r : 출력 위치를 줄 맨 앞으로 이동<br>
\t : 탭<br>
\b : 백스페이스<br>
작은 따옴표와 백슬래시 자체를 나타낼 때는 백슬래시로 이스케이프 한다<br>
(ex. \’ \\)
### 1.2.4 boolean 타입 (1개)
boolean값과 0, 1은 아무 관계가 없다. 숫자 타입이 아니다.
## 1.3 변수
### 1.3.1 변수 선언
### 1.3.2 변수 이름
문자, 숫자, 기호, _, $로 구성할 수 있으나<br>
$는 자동으로 생성되는 이름용이므로 직접 이름 지을 때는 사용하면 안 된다.
### 1.3.3 변수 초기화
### 1.3.4 상수
System 클래스에는 상수가 선언되어 있어서 어디에서나 System.out으로 사용할 수 있다.<br>
public static final PrintStream out<br>
final 변수를 처음 사용하기 전에 딱 한번만 초기화한다면 나중으로 미룰 수도 있다.
## 1.4 산술 연산
### 1.4.1 할당
### 1.4.2 기본 계산
17/5는 3이다. 17.0/5.0은 3.4이다.
부동 소수점을 0으로 나누면 예외가 일어나지 않고, 무한대 값이나 NaN가 나온다.<br>
음수일 가능성이 있는 피연산자에 %를 사용할 때는 항상 주의해야 한다.<br>
이런 상황에서는 Math.floorMod(피연산자, x) 쓰면 된다. 
### 1.4.3 수학 메서드
정적(static) 메서드이므로 객체(인스턴스)로 호출할 수 없다.<br>
덜 효율적이어도 언제나 결과가 동일한 부동소수점 계산을 원한다면 StrictMath를 사용
### 1.4.4 숫자 타입 변환
1. 피연산자 중 하나가 double이면 다른 하나를 double로 변환<br>
2. 피연산자 중 하나가 float이면 다른 하나를 float로 변환<br>
3. 피연산자 중 하나가 long이면 다른 하나를 long로 변환<br>
4. 이외에는 두 피연산자를 int로 변환<br>
정수 타입을 부동소수점 타입으로 변환하는 것은 언제나 합법
### 1.4.5 관계 연산자와 논리 연산자
### 1.4.6 큰 숫자
BigInteger, BigDecimal
## 1.5 문자열
### 1.5.1 문자열 연결
<pre>
<code>
String names = String.join(“, “, “Peter”, “Paul”, “Mary”);
StringBuilder가 더 효율적
</code>
</pre>
### 1.5.2 부분 문자열
substring<br>
split<br>
input.split(“\\s+”)는 공백으로 split한다는 뜻
### 1.5.3 문자열 비교
null과 “”는 다르다<br>
equalsIgnoreCase<br>
compareTo (음수/양수)
### 1.5.4 숫자와 문자열 사이의 변환
### 1.5.5 문자열 API
http://docs.oracle.com/javase/9/docs/api에 접속해서 찾아보기
### 1.5.6 코드 포인트와 코드 유닛
자바 문자열은 UTF-16으로 인코딩된 16비트 숫자인 코드 유닛의 시퀀스
## 1.6 입력과 출력
### 1.6.1 입력 읽어 오기
### 1.6.2 포맷 적용 출력
System.out.printf(“%8.2f”, 1000.0/3.0);<br>
필드 폭은 8자리로 출력하고, 정밀도는 2자리로 출력한다.
## 1.7 제어 흐름
### 1.7.1 분기
switch<br>
if/else
### 1.7.2 루프
do/while<br>
while<br>
for<br>
for(;;)는 while(true)와 같다
### 1.7.3 중단과 계속
break<br>
labeled break<br>
continue
### 1.7.4 지역 변수의 유효 범위
## 1.8 배열과 배열 리스트
### 1.8.1 배열 다루기
### 1.8.2 배열 생성
객체의 배열을 생성한 후에는 객체로 채워야 한다. (인접 리스트 만들 때 처럼)
### 1.8.3 배열 리스트
ArrayList<>
다이아몬드 문법이라고 하고 제네릭이라고 부른다.
### 1.8.4 기본 타입의 래퍼 클래스
제네릭 클래스의 불편한 제약 하나는 기본 타입을 타입 매개변수로 쓸 수 없다는 점<br>
따라서 래퍼 클래스를 쓴다<br>
그러면 담을 때는 오토박싱, 꺼낼 때는 언박싱이 된다.<br>
if(numbers.get(i) == numbers.get(j))는 i와 j인덱스 두 숫자 같은지 검사하지 않음<br>
equals를 써서 비교해야 함. 래퍼 클래스 이기 때문에
### 1.8.5 향상된 for 루프
for(String name:friends)
### 1.8.6 배열과 리스트 복사
Arrays.copyOf
### 1.8.7 배열 알고리즘
sort<br>
fill<br>
toString<br>
Collections.reverse();<br>
Collections.shuffle();
### 1.8.7 명령줄 인수
### 1.8.8 다차원 배열
## 1.9 기능적 분해
### 1.9.1 정적 메서드 선언 및 호출
### 1.9.2 배열 매개변수와 반환 값
### 1.9.3 가변 인수
인수를 원하는 개수만큼 넘기도록 할 수 있다
<pre>
<code>
public static void main(String[] args) {
	double avg = average(3, 4.5, -5, 0);
	System.out.println(avg);
}
public static double average(double... values) {
	double sum = 0;
	for(double v: values) sum+=v;
	return values.length == 0?0:sum/values.length;
}
</code>
</pre>
 
