## JavaScript The Good Parts

### 1. 자바스크립트의 좋은 점들
=========================
이 책의 요점은 어떻게 하면 나쁜 점을 피해서 좋은 결과를 얻느냐는 것이다.    
이 책에서는 자바스크립트의 진정한 본성을 드러내지 못 하는 우아하지 않은 기능들을 모두 제거해 버렸다.      
전적으로 자바스크립트의 좋은 점에만 초점을 맞출 것이다.
   
#### 01 | 왜 자바 스크립트 인가?
---------------------------
자바스크립트의 놀라운 점은 언어 자체에 대해 많이 모르거나   
심지어는 프로그래밍에 대해 잘 모르더라도 원하는 작업을 할 수 있다는 것이다.

#### 02 | 자바스크립트 분석
---------------------------
자바스크립트의 몇몇의 **매우 좋은 아이디어**에는 `함수`, `느순한 타입 체크`, `동적 객체`, `표현적인 객체 리터럴 표기법` 등이 있다.   
그리고 대표할 만한 **나쁜 아이디어**에는 프로그래밍 모델이 `전역변수`에 기초하고 있다는 것이다. 
  
자바스크립트의 함수는 어휘적 유효범위를 가진 **[일급 객체 (first-class object)](http:://en.wikipedia.org/wiki/First-class_object)** 이다.  
	
> 일급 객체 란?  
> 언어상에 제약이 없는 객체를 일급 객체라고 한다.   
> 즉 변수에 대입되거나 인수로 넘길 수도 있고, 반환값으로 사용하거나 연산등에 사용하는데 전혀 제약이 없는 객체이다.  
> 자바스크립트에서는 함수가 일급 객체이므로 이 모든 것이 다 가능하다.  
> 참고 : [http:://en.wikipedia.org/wiki/First-class_object](http:://en.wikipedia.org/wiki/First-class_object)
	
또한 주류가 된 첫 번째 **[람다(lambda)](http://en.wikipedia.org/wiki/Lambda)** 언어이며, 좀 더 깊이 들어가면, 이름처럼 자바에 가깝기보다는 `Lisp 언어` 그리고 `Scheme 언어`와 더 많은 공통점이 있다.

> 람다 란?  
> 람다는 Alonzo Church와 Stephen Cole Kleene의 람다 대수에서 유래한 것으로 익명 함수나 클로저 등을 정의하기 위한 표현식을 위미한다.  
> 참고 : [http://en.wikipedia.org/wiki/Lambda](http://en.wikipedia.org/wiki/Lambda)
	
자바스크립트는 느슨한 타입 체크 언어이다. 그래서 자바스크립트 컴파일러는 타입 오류를 찾을 수 없다.  
느슨한 타입 체크를 하는 언어를 사용하면 복잡한 클래스 계층을 구성할 필요도 없으며, 원하는 대로 동작하도록 타입 캐스팅과 씨름할 필요도 없다.

자바스크립트는 매우 강력한 객체 리터럴 표기법이 있다.  
이 표기법을 사용하면 단순히 필요한 요소들을 열거하는 방법으로 객체를 만들 수 있다.  
이러한 표기업은 유명한 데이터 교환 형식인 `JSON`에도 영감을 주었다.

자바스크립트는 클래스가 필요 없는 `객체 시스템`이 있어서 특정 객체에 있는 속성들을 다른 객체에 직접 상속할 수 있다.  
이러한 특성은 매우 강력하지만 클래스 기반의 언어에 익숙한 프로그래머에게는 친숙하지 않은 점이다.

자바스크립트(또는 JScript)를 정의하고 있는 표준은 [The ECMAScript Programming Language third Edition](http://www.ecmainternational.org/publications/files/ecma-st/ECMA-262.pdf)이다.

> 왜 자바스크립트를 사용해야 하지?  
> 첫 번째는 선택의 여지가 없다는 것이다.   
> 웹은 애플리케이션 개발에 있어 중요한 플랫폼이며, 자바스크립트는 모든 브라우저에서 사용할 수 있는 유일한 언어이다.  
> 두 번째는 자바스크립트는 매우 경량화 돼 있으며 표현적(expressive)이다. (함수형 프로그래밍)

#### 03 | 예제 테스트를 위한 간단한 준비
---------------------------
웹 브라우저와 텍스트 에디터만 있으면 자바스크립트 프로그램을 실행시킬 모든 준비가 끝난 것이다.  

1. 먼저 다음 내용을 program.html 파일로 저장한다.  

		<html>
			<body>
				<pre>
					<script src="program.js">
					</script>
				<pr>
			</body>
		</html>

2. 같은 폴더에 다음의 내용을 program.js 파일로 저장 한다.
		
		document.writeln('Hello, World!');

3. 이제 결과를 보기 위해 program.html 파일을 브라우저로 불러와서 결과를 확인한다.

### 2. 자바스크립트의 좋은 문법들
=========================
이번 장에서는 자바스크립트의 좋은 점들(good parts)에 해당하는 문법을 살펴본다.

#### 01 | 공백(whitespace)
---------------------------
var 와 that 사이에 있는 빈 칸은 제거 할 수 없다. 하지만 다른 빈 칸들은 제거해도 상관 없다.  
주석은 가능한 /\* \*/를 사용하는 대신 // 사용할 것을 권한다.

	// 주석 : 공백
	var that = this;

#### 02 | 이름(Names)
---------------------------
이름(Name)은 하나의 문자나 그 뒤를 이어서 하나 이상의 `문자`, `숫자`, `_`가 붙는 문자열  
`문장`, `변수`, `매개변수`, `속성명`, `연산자`, `라벨`등에 사용한다.

다음에 나오는 예약어들은 이름(Name)이 될 수 없다.
	
	A: abstract
	B: boolean, break,	byte
	C: case, catch, char, class, const, continue
	D: debugger, default, delete, do, double
	E: else, enum, export, extends
	F: false, final, finally, float, for, function
	G: goto
	I: if, implement, import, in, instanceof, int, interface
	L: long
	N: natvie, new, null
	P: package, private, protected, public
	R: return
	S: short, static, super, switch, synchronized
	T: this, throw, throws, transient, true, try, typeof
	V: var, volatile, void
	W: while, with


#### 03 | 숫자(Numbers)
---------------------------
자바스크립트는 숫자형이 하나만 있다. 내부적으로 **숫자**는 `64비트 부동 소수점 형식`을 지닌다.  
이는 자바의 double 형과 같고 정수와 실수의 구분이 없다.  
즉 1과 1.0은 같은 값이다.

`NaN`은 수치 연산을 해서 정상적인 값을 얻지 못 할때의 값이다. 또한 그 자신을 포함해서 어떤 값하고도 같지 않다.  
그러므로 `NaN`인지 확인하려면 비교 구문이 아니라 `isNaN()`이라는 함수를 사용한다.


#### 04 | 문자열(Strings)
---------------------------
문자열은 작은 따옴표(') 나 큰 따옴표(")로 묶어서 나타낸다.  
백슬러시(\)는 이스케이프 문자이다. (이를 이용 일반 문자가 아닌 특별한 문자를 문자열에 삽입 가능)  
자바스크립트 내의 모든 문자는 16비트 유니코드 이다.

문자열은 `length` 라는 속성이 있다. ("seven".length 의 값은 5이다.)

문자열을 "+" 연산자로 연결하여 새로운 문자열을 만들 수 있다.

	// true
	'c' + 'a' + 't' === 'cat'
	
문자열은 메소드가 있다. (8장 참조)

	'cat'.toUpperCase() ==== 'CAT'
	


### 3. 객체

### 4. 함수

### 5. 상속

### 6. 배열

### 7. 정규 표현식

### 8. 메소드

### 9. 스타일

### 10. 아름다운 속성에 대한 단상

### 부록 A | 나쁘지만 사용해야 하는 부분들(Awfull parts)

### 부록 B | 나쁜 점들

### 부록 C | JSLint

### 부록 D | 구문 다이어그램

### 부록 E | JSON