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
  
자바스크립트의 함수는 어휘적 유효 범위를 가진 **[일급 객체 (first-class object)](http:://en.wikipedia.org/wiki/First-class_object)** 이다.  
	
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

> 리터럴 표기법 이란? 그냥 열거하는 거다.

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
이름(Name)은 하나의 문자나 그 뒤를 이어서 하나 이상의 `문자`, `숫자`, `_`가 붙는 `문자열`,  
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
백슬러시(\\)는 이스케이프 문자이다. (이를 이용 일반 문자가 아닌 특별한 문자를 문자열에 삽입 가능)  
자바스크립트 내의 모든 문자는 16비트 유니코드 이다.

문자열은 `length` 라는 속성이 있다. ("seven".length 의 값은 5이다.)

문자열을 "+" 연산자로 연결하여 새로운 문자열을 만들 수 있다.

	// true
	'c' + 'a' + 't' === 'cat'
	
문자열은 메소드가 있다. (8장 참조)

	// true
	'cat'.toUpperCase() ==== 'CAT'
	
#### 05 | 문장(Statements)
---------------------------
웹 브라우저에서 각각의 \<script\> 태그는 컴파일되어 즉시 실행되는 하나의 컴파일 단위이다.  

링커(linker)가 없기 때문에 자바스크립트는 모든 문장을 공통적인 "**전역 이름 공간(namespace)**"에 한 데 몰아 넣는 다.

var 문은 "함수 내부"에서 사용될 때 함수의 private 변수를 정의한다.

조건문의 블록은 중괄호({..})로 둘러 쌓인 문장들의 집합이다.  
다른 언어들과 달리 자바스크립트에서 블록 ({..})은 새로운 유효범의(scope)를 생성하지 않기 때문에  
변수는 블록 안에서가 아니라 함수의 첫 부분에서 정의해야 한다.

##### if 문은 표현식의 값에 따라 프로그램의 흐름을 변경 한다.  
다음은 if문과 표현식의 참과 거짓에 해당하는 값들 이다.
	
	if (표현식) {
		문장들
	}
	else if (표현식){
		문장들
	}
	else {
		문장들
	}
	
	// 표현식 : 거짓
	* flase
	* null
	* undefined
	* 빈 문자열 ''
	* 숫자 0
	* NaN

	// 표현식 : 참
	* 거짓 외의 모든 값

##### switch 문은 다중 분기를 수행한다.
표현식의 결과값은 `숫자`일수도 있고 `문자열`일 수도 있다.

	swithc (표현식) {
		case 표현식: 
			문장들
			break;
		default:
			문장들
			break;
	}

##### while 문은 단순한 반복 수행 문자이다.
표현식이 참인 동안은 블록을 반복해서 실행하며, 거짓이면 반복 수행은 끝난다.

	while (표현식) {
		문장들
	}

##### for 문은 두 가지 형식으로 사용한다.
1. 초기화, 조건, 증가 라는 세가지 절로 제어 하는 구조.

		// 조건 부분이 생략 되면 '참'
		// 조건 부분이 검사 결과가 '거짓' 이면 반복 종료 
		for (초기화; 조건; 증가 ) {
			문장들
		}


2. 객체의 속성 이름(또는 키)을 열거하는 구조. (for in)  

		// 각각의 반복 실행마다 객체에 있는 각각의 속성 이름을 변수에 할당
		for (변수 in 객체 ) {
			문장들
		}

	`for in` 형식은 보통 다음과 같이 `object.hasOwnProperty(변수)` 메소드로 속성 이름이 실제로 객체의 속성인지   
	아니면 `프로토타입 체인(prototype chain)` 상에 있는 것인지를 확인하는 것이 필요하다.

		var myvar;

		for (myvar in obj) {
			if (obj.hasOwnProperty(myvar)) {
				문장들
			}
		}
		
##### do 문은 표현식이 블록을 실행한 후에 검사된다.
`do` 문은 적어도 한번은 실행 된다.

		do {
			문장들
		} while (표현식);

##### try 문은 블록을 실행하면서 블록 내에서 발생하는 예외 상황을 포착한다.
`catch` 절은 예외 객체를 받는 새로운 변수를 정의 한다.

		try {
			문장들
		}
		catch (변수) {
			문장들
		}
		
##### throw 문은 예외를 발생 시킨다.
표현식 부분은 보통 `name`과 `message`라는 속성이 있는 객체 리터럴 이다.

		try {
			if (typeof a !== 'number') {
				throw {
					name: 'TypeError',
					message: 'add needs numbers'
				};
			}
		}
		catch (e) {
			consloe.log(e.name + ": " + e.message);
		}

만약 `throw` 문이 `try` 블록 안에 있으면 실행의 제어는 `catch` 절로 이동한다.  

		try {
			문장들	
			throw 표현식;
		}
		catch (e) {
			throw에 의한 실행의 제어
		}

만약 `throw` 문이 일반적인 함수 내에 있다면 함수 호출은 중단되고 함수를 호출한 `try` 문의 `catch` 절로 실행 흐름이 이동한다.

		try {
			문장들
			함수();
		}
		catch (e) {
			throw에 의한 실행의 제어
		}
		
		function test () {
			문장들
			// 실행 중단
			throw 표현식;
			문장들
		};

##### return 문은 함수가 호출한 곳으로 되돌아가는 역할을 한다.
return 문은 표현식으로 반환값을 지정하고 지정되지 않으면 `undefined`를 반환한다. 

		return 표현식;
		
##### break 문은 반복문이나 switch 문에서 흐름을 벗어나게 하는 역할을 한다.
break 문은 라벨을 취할 수 있는 데 라벨이 주어지면 라벨이 붙은 문장의 끝으로 이동한다.

		// 라벨 취소 가능
		break;
		
		// 라벨 사용
		break 라벨;		


#### 06 | 표현식(Expressions)
**********************************
가장 간단한 표현식

* 리터럴 값 (문자열이나 숫자)
* 변수
* 내장값들 (true, false, null, undefined, NaN, Infinity 등)
* new 키워드에 의한 호출 표현식
* delete 키워드 다음에 오는 세부지정 표현식
* 괄호로 쌓인 표현식
* 전치 연산자 다음에 이어지는 표현식
* 이항 연산자의 표현식
* ? 삼항 연산자의 표현식 (ex : a === 0 ? true : false )
* 호출
* 세부지정 (. 또는 [])

연산자 우선 순위

연산자         					| 설명
-----							| -----			
., [], ()      					| 세부지정이나 호출
delete, new, typeof, +, -, ! 	| 단항 연산자
*, /, %							| 곱하기, 나누기, 나머지
+, -							| 더하기/연결, 빼기
<=, >=, >, <					| 같지 않음 비교
===, !==						| 동등
&&, \|\|						| 논리적 and, or
? :								| 삼항 연산자

##### typeof 연산자의 결과값에는 `number`, `string`, `boolean`, `undefined`, `function`, `object` 등이 있다.  
피연산자가 배열이나 null이면 결과는 모두 object 인데 이는 약간 문제가 있다.  
( 이 문제를 포함하여 typeof 연산자에 대한 자세한 부분은 6장과 부록 A에서 살펴본다.)

##### 호출은 함수를 실행 한다.
호출 연산자는 함수 이름 뒤에 이어지는 한 쌍의 괄호이다.  
괄호 내에는 함수에 전달하는 인수를 포함 할 수 있다.

	function () {
		문장들
	}(); // 호출

##### 세부지정은 객체의 속성이나 배열의 구성요소를 지정할 때 사용한다.

	// 객체
	var test_object = {
		'name': 'test',
		'addr': 'korea'
	};
	
	// . 세부 지정
	console.log(test_object.name);				// 'test'
	// [] 세부 지정
	console.log(test_object['addr']);			// 'korea'
	
	
	// 배열
	var numbers = [
		'zero', 'one', 'two'
	];
	
	// [] 세부 지정
	console.log(numbers[1]);					// 'one'
	console.log(numbers.length);				// 3

#### 07 | 리터럴 (Literals)
****************************
리터럴의 종류

* 숫자 리터럴
* 문자열 리터럴
* 객체 리터럴
* 배열 리터럴
* 함수
* 정규 표현식 리터럴

#### 08 | 함수 (Functions)
*****************
함수 리터럴은 함수값을 정의 한다.  
함수 리터럴은 이름을 가질 수 있는 데 이 이름은 `재귀적으로 호출` 할 때 사용 할 수 있다.

매개변수는 함수 호출 시 넘어온 인수로 초기화 되며 함수에서 사용 되는 변수 이다.
	
	// 이름은 생략 가능
	function 이름 (매개변수) {
		var 문
		문자들
	}

### 3. 객체
===========
자바스크립트에서 단순한 데이터 타입은 `숫자`, `문자열`, `불리언 (true/false)`, `null`, `undefined` 가 있다.  

`숫자`, `문자열`, `불리언`은 메소드가 있기 때문에 유사 객체라고 할 수 있다.
(그러나 값이 한번 정해 지면 변경 불가)

자바스크립트에서는 `배열`, `함수`, `정규 표현식` 등과 `객체` 모두가 객체이다.

객체는 이름과 값이 있는 속성들을 포함하는 컨테이너라고 할 수 있으며, 속성의 값은 undefined를 제외한 자바스크립트의 모든 값이 사용될 수 있다.

자바스크립트의 객체는 클래스가 필요 없다.(class-free)  
객체 하나는 다른 객체를 포함할 수 있기 때문에, 그래프나 트리 같은 자료구조를 쉽게 표현할 수 있다.

	자바스크립트에는 객체 하나에 있는 속성들을 다른 객체에 상속하게 해주는 프로토타입(prototype) 연결 특성이 있다.   
	이 특성을 잘 활용하면, 객체를 초기화 하는 시간과 메모리 사용을 줄 일 수 있다.  


#### 01 | 객체 리터럴
이 표기법은 아무것도 없거나 하나 이상의 이름/값 쌍들을 둘러싸는 중괄호 이다.

	var empty_object = {};
	
	var stooge = {
		"first-name": "Jerome",
		"last-name": "Howard"
	};
	
	var 객체명 = {
		속성 이름(property): 속성 값 || 표현식	// 속성 이름은 예약어가 이닐 경우 (") 삭제 가능
	};
	
속성의 값은 어떠한 표현식도 가능하다. (다음의 예처럼 객체 리터럴도 가능. 중첩된 객체.)

	var flight = {
		airline: "Oceanic",
		number: 515,
		departure: {
			IATA: "SYD",
			time: "2014-09-22 14:55",
			city: "Sydney"
		},
		arrival: {
			IATA: "LAX",
			time: "2015-09-22 14:55",
			city: "Los Angeles"
		}
	};
	
#### 02 | 속성값 읽기
******
객체에 속한 속성의 값은 `속성 이름(property)`에 대괄호 또는 . 을 이용하여 읽을 수 있다.

	stooge['first-name']			// "Jerome"
	flight.departure.IATA			// "SYD" 
	
객체에 존재하지 않는 속성을 읽으려 하면 `undefined` 를 반환 한다.
	
	stooge['middle-name']			// undefined
	flight.status					// undefined
	
|| 연산자를 사용하여 기본값 지정
	
	var middle = stooge['middle-name'] || '(none)';
	var status = flight.status || 'unknown'; 

존재 하지 않는 속성, 즉 `undefined` 의 속성을 참조하려 할 때 `TypeError` 예외가 발생 한다.  
이런 상황을 방지하기 위해서 다음과 같이 && 연산자를 사용 할 수 있다.

	flight.equipment				                   // undefined
	flight.equipment.model						       // throw 'TypeError'
	flight.equipment && flight.equipment.model	       // undefined
		
#### 03 | 속성 값의 갱신 및 속성 추가	
****
속성의 이름이 이미 존재 하면 속성의 값만 교체.
	
	stooge['first-name'] = "Eric";
	
속성이 객체 내에 존재 하지 않으면 속성을 객체에 추가.
	
	stooge['middle-name'] = 'Lester';
	stooge.nickname = 'Curly';
	flight.equipment = {
		model: 'Boeing 777'
	};
	flight.status = 'overdue';
	
	console.log(stooge.nickname);				//'Curly'
	
#### 04 | 참조
****
객체는 참조 방식으로 전달 된다. 절대 복사 되지 않는 다. (C 의 메모리 주소 넘기는 것 처럼)

	var x = stooge;
	x.nickname = 'Curly';
	var nick = stooge.nickname;
	
	console.log(nick);
	
	// x 와 stooge가 모두 같은 객체를 참조하기 때문에,
	// 변수 nick의 값은 'Curly'.
	
#### 05 | 프로토타입(Prototype)
****
모든 객체는 속성을 상송하는 프로토타입 객체에 연결되어 있다.  
객체 리터럴로 생성되는 모든 객체는 자바스크립트의 표준 객체인 `Object` 의 속성 인 `prototype 객체 (Object.prototype)` 에 연결 된다.

객체를 생성할 때는 해당 객체의 프로토타입이 될 객체를 선택할 수 있다.

	// Object 객체에 create 라는 메소드를 추가하고 	
	// create 는 넘겨받은 객체를 prototype 으로 하는 새로운 객체를 생성한다.
	 
	if (typeof Object.create !== 'function') {
		Object.create = function (o) {
			var F = function () {};
			F.prototype = o;
			return new F();
		};
	}
	
	var another_stooge = Object.create(stooge);

프로토타입 연결은 오로지 객체의 속성을 읽을 때만 사용한다.  
해당 속성이 객체에 없는 경우 자바스크립트는 이 속성을 프로토타입 객체에서 찾으려고 한다.  
이러한 시도는 프로토타입 체인(prototype chain)의 가장 마지막에 있는 `Object.prototype` 까지 계속 해서 이어 진다.
 
프로토타입 관계는 동적 관계이다. 만약 프로토타입에 새로운 속성이 추가되면, 해당 프로토타입을 근간으로 하는 객체들에는 즉각적으로 이 속성이 나타난다.

	stooge.profession = 'actor';
	console.log(another_stooge.profession); 	// 'actor'
	
#### 06 | 리플렉션 (reflection)
****
typeof 연산자는 속성의 타입을 살펴 보는 데 유용하다.

	typeof flight.number						// 'number'
	typeof flight.status						// 'string'
	typeof flight.arrival						// 'object'
	typeof flight.manifest						// 'undefined'

때때로 해당 객체의 속성이 아니라 프로토타입 체인 상에 있는 속성을 반환 할 수 있기 때문에 주의가 필요하다.

	typeof flight.toString						// 'function'
	typeof flight.constructor					// 'function'
	
리플렉션을 할 때 원하지 않는 속성을 배제 하기 위한 두 가지 방법.

1. 함수값을 배체 하는 방법.
		
		if (typeof a !== 'function') {
			// operation
		}
		else {
			// skip
		}

2. 객체에 특성 속성이 있는지를 확인하여 true/false 값을 반환하는 `hasOwnProperty' 메소드를 사용하는 방법.  
(hasOwnProperty 메소드는 프로토타입 체인을 바라 보지 않는다.)  
	
		flight.hasOwnProperty('number');		// true
		flight.hasownProperty('constructor');	// true
		
#### 07 | 열거 (Enumeration)
****
for in 구분을 사용하면 객체에 있는 모든 속성의 이름을 열거 할 수 있다.  
원하지 않는 속성을 걸러낼 때 가장 일반적인 필터링 방법은 hasOwnProperty 메소드와 함수를 배제 하기 위해 typeof 를 사용 한다.
	
	// (주의) 속성들이 이름순으로 나온다는 보장 없음.
	var name;
	for (name in another_stooge) {
		if (typeof another_stooge[name] !== 'function') {
			console.log(name + ': ' + another_stooge[name]);
		}
	}
	
만약 특정 순으로 속성 이름들이 열거되기를 원한 다면 for in 구문을 사용하지 말고 아래와 같이 사용해라.

	var i;
	
	// 원하는 순서를 특정 배열로 지정
	var properties = [
		'first-name',
		'middle-name',
		'last-name',
		'profession'
	];
	
	// 원하는 손서대로 속성들을 리플렉션
	for (i = 0; i < properties.length; i += 1) {
		console.log(proerties[i] + ': ' + another_stooge[properties[i]]);
	}

#### 08 | 삭제
delete 연산자를 사용하면 객체의 속성을 삭제 할 수 있다. (프로토타입 연결 상에 있는 객체들은 접근 하지 않는다.)

객체에서 특정 속성을 삭제했는 데 같은 이름의 속성이 프로토타입 체인에 있는 경우 프로토타입의 속성이 나타난다.

	another_stooge.nickname						// 'Moe'
	
	// another_stooge 에서 nickname 을 제거 하면
	// 프로토타입에 있는 nickname 이 나타남.
	delete another_stooge.nickname;
	
	another_stooge.nickname						// 'Curly'
													
#### 09 | 최소한의 전역 변수 사용
전역 변수는 프로그램의 유연성을 약화하기 때문에 가능하면 피해라.

**전역 변수 사용을 최소화 하는 방법은
애플리케이션에서 전역 변수 사용을 위해 다음과 같이 전역 변수 하나를 만드는 것이다.**

	// 전역 변수를 위한 컨테이너 선언
	var MYAPP = {};
	
	MYAPP.stooge = {
		'first-name': 'Joe',
		'last-name': 'Howard'
	};
	
	MYAPP.flight = {
		airline: 'Oceanic',
		number: 815,
		departure: {
			IATA: 'SYD',
			time: '2014-09-22 14:55',
			city: 'Sydney'
		},
		arrival: {
			IATA: 'LAX',
			time: '2014-09-23 10:42',
			city: 'Los Angeles'
		}
	};
	
이러한 방법으로 애플리케이션에 필요한 전역변수를 이름 하나로 관리 하면 다른 애플리케이션이나 위젯 또는 라이브러리들과 연동 할 때 발생하는 문제점을 최소화 할 수 있다.

### 4. 함수
===========
함수는 실행 문장들의 집합을 감싸고 있다. 함수는 자바스크립트에서 모듈화의 근간이다.  
함수는 코드의 재사용이나 정보의 구성 및 은닉 등에 사용하고, 객체의 행위를 지정하는 데도 사용한다.

#### 01 | 함수 객체
****
자바스크립트에서 함수는 객체다.  
##### 객체는 프로토타입 객체로 숨겨진 연결을 갖는 이름/값 쌍들의 집합체다.
객체 중에서 객체 리터럴로 생성되는 객체는 `Object.prototype`에 연결된다.  
반면에 함수 객체는 `Function.prototype`에 연결된다. (Function은 Object.prototype 에 연결된다.)

모든 함수는 숨겨져 있는 두 개의 추가적인 속성이 있는데, 이 속성들은 함수의 문맥(context)과 함수의 행위를 구현하는 코드 (code) 다.

모든 함수 객체는 `prototype` 이라는 속성이 있다.   
이 속성의 값은 함수 자체를 값으로 갖는 `constructor`라는 속성이 있는 객체이며, 이는 Function.prototype으로 숨겨진 연결과는 구분된다.

	// 함수의 prototype 속성의 값을 객체 리터럴로 나타내면 다음과 같다.
	{
		constructor: this
	}

함수는 객체이기 때문에 `함수`는 `변수`나 `객체`, `배열` 등에 저장되며, 다른 함수에 전달하는 `인수`로도 사용하고, 함수의 `반환값` 으로도 사용된다.
함수를 다른 객체와 구분 짓는 특징은 `호출 할 수 있다`는 것이다.

#### 02 | 함수 리터럴
함수 객체는 함수 리터럴로 생성할 수 있다.

	// add 라는 변수를 생성하고 두 수를 더하는 함수를
	// 이 변수에 저장.
	var add = function (a, b) {
		return a + b;
	};

함수 리터럴에는 4가지 부분이 있다.

1. function 이라는 예약어
2. 함수의 이름 (함수를 재귀적으로 호출할 때 사용되며, 디버거나 개발 툴에서 함수를 구분 할때도 사용 된다.)
3. 괄호로 둘서싸인 함수의 매개변수 집합 (매개변수들은 함수내에서 변수로 정의한다.)
4. 중괄호로 둘써싸인 문장들의 집합

함수 리터럴은 표현식이 나올 수 있는 곳이면 어디든지 위치할 수 있다.
함수 리터럴로 생성한 함수 객체는 외부 문맥으로의 연결이 있는 데 이를 클로저(closure)라고 한다.

#### 03 | 호출
****
함수를 호출하면 제어를 매개변수와 함께 호출한 함수로 넘기며,<br>
모든 함수는 명시되어 있는 매개변수에 더해서 `this`와 `arguments`라는 추가적인 매개변수 두 개를 받게 된다.

자바스크립트의 함수 호출 패턴

1. 메소드 호출 패턴
2. 함수 호출 패턴
3. 생성자 호출 패턴
4. apply 호출 패턴

각각의 패턴에 따라 `this`라는 추가적인 매개변수를 다르게 초기화 한다.

함수를 호출할 때 넘기는 인수의 개수와 매개변수의 개수가 일치하지 않아도 실행시간 오류는 발생하지 않는다.<br>

* 인수가 더 많을 경우 매개변수 수보다 초과하는 인수는 무시한다.
* 인수가 더 적을 경우 남는 매개변수에 undefined를 할당한다.

##### 메소드 호출 패턴
****
함수를 객체의 속성에 저장하는 경우 이 함수를 메소드라고 한다.<br>
메소드를 호출 할때, `this`는 메소드를 포함하고 있는 객체에 바인딩된다. (즉, this는 객체 자체가 된다.)

	// value와 increment 메소드가 있는 myObject 생성.
	// increment 메소드의 매개변수는 선택적.
	// 인수가 숫자가 아니면 1이 기본값으로 사용됨.

	var myObject = {
		value: 0,
		increment: function (inc) {
			this.value += typeof inc === 'number' ? inc : 1;
		}, 
		getValue: function () {
			return this.value;
		}
	};

	myObject.increment();
	console.log(myObject.value); 					// 1

	myObject.increment(2);
	console.log(myObject.value);					// 3

`this`와 객체의 바인딩은 호출 시에 일어나며, `this`를 사용해 객체의 값을 읽거나 변경 할 수 있다.<br>
자신의 객체 문맥을 `this`로 얻는 메소드를 퍼블릭(public) 메소드라고 한다.

##### 함수 호출 패턴
****
함수가 객체의 속성이 아닌 경우에는 함수로 호출 한다.

	var sum = add(3, 4); 							// 7

함수 호출 패넌을 호출 할때 `this`는 전역객체에 바인딩된다.

> 이런 특성은 언어 설계 단계에서의 실수이다.<br>
> 만약 언어를 바르게 설계 했다면, 내부 함수를 호출 할때 이 함수의 this는 외부 함수의 this 변수에 바인딩 되어야 한다.<br>
> 이러한 오류의 결과는 메소드가 내부 함수를 사용하여 자신의 작업을 돕지 못한다는 것이다.<br>
> 왜냐하면, 내부 함수는 메소드가 객체 접근을 위해 사용하는 this에, 자신의 this를 바인딩하지 않고 엉뚱한 값(전역객체)에 연결하기 때문이다.<br>
> 이런 문제애 대한 대안은 메소드에서 변수를 정의한 후 여기에 this를 할당하고, 내부 함수는 이 변수를 통해서 메소드의 this에 접근하는 방법이 있다<br>.
> 관례상 이 변수의 이름을 that 이라고 하면 다음의 예와 같이 구현 할 수 있다.

	// 위 myObject 에 double 메소드를 추가
	myObject.double = function () {
		var that = this;							// 대안

		var helper = function () {
			that.value = add(that.value, that.value);
		};

		helper();									// helper를 함수로 호출
	};

	// double을 메소드로 호출
	myObject.double();
	console.log(myObject.getValue());				// 6

##### 생성자 호출 패턴
****
자바스크립트는 클래스가 없으며, 프로토타입에 의해서 상속이 이루어지는 언어이다.<br>
이 말은 객체가 자신의 속성들을 다른 객체에 바로 상속할 수 있다는 뜻이다.

프로토타입에 의한 상속은 매우 표현적이지만 널리 알려져 있지 않다.

자바스크립트는 클래스 기반의 언어들을 생각나게 하는 객체 생성 문법을 제공하나, 이는 자바스크립트의 진정한 프로토타입적 속성을 애매하게 만들었다. (프로토타입적 상속 사용을 저해 한다.)

함수를 `new`라는 전치 연산자와 함께 호출하면, 호출한 함수의 `prototype` 속성의 값에 연결되는 (숨겨진) 링크를 갖는 객체가 생성되고, 이 새로운 객체는 `this`에 바인딩 된다.

`new`라는 전치 연산자는 `return` 문장의 동작을 변경한다. (이 내용은 뒤에서 더 자세히 살펴 본다.) 

	// Quo라는 생성자 함수를 생성.
	// 이 함수는 status 라는 속성을 가진 객체를 생성함.
	var Quo = function (string) {
		this.status = string;
	};

	// Quo의 모든 인스턴스에 get_status라는 public 메소드를 줌.
	Quo.prototype.get_status = function () {
		return this.status;
	};

	// Quo의 인스턴스 생성
	var myQuo = new Quo('confused');
	console.log(myQuo.get_status());				// confused

`new`라는 전치 연산자와 함께 사용하도록 만든 함수를 `생성자(constructor)`라고 한다.

> 일반적으로 생성자는 이니셜을 대문자로 표기하여 이름을 지정한다.<br>
> 생성자를 new 없이 호출하면 컴파일 시간이나 실행시간에 어떠한 경고도 없어서 알 수없는 결과를 초래 한다.<br>
> 그러므로 대문자 표기법을 사용하여 해당 함수가 생성자라고 구분하는 것은 매우 중요하다.

**`생성자 함수를 사용하는 스타일은 권장 사항이 아니다.`**

##### apply 호출 패턴
****
자바스크립트는 `함수형 객체지향 언어`이기 때문에, `함수`는 `메소드`를 가질 수 있다.

apply 메소드는 함수를 호출할 때 사용할 인수들의 배열을 받아들인다.<br>
또한 이 메소드는 `this`의 값을 선택할 수 있도록 해준다.

apply 메소드에는 매개변수 두개가 있다.

1. this 에 묶이게 될 값
2. 매개변수들의 배열

예제

	// 숫자 두 개를 가진 배열을 만들고 이를 더함.
	var array = [3, 4];
	var sum = add.apply(null, array);
	// 합은 7

	// status 라는 속성을 가진 객체를 만듦.
	var statusObject = {
		status: 'A-OK'
	};

	// statusObject 는 Quo.prototype 을 상속받지 않지만
	// Quo 에 있는 get_status 메소드가 statusObject 를 대상으로 생행되도록 호출할 수 있음.

	var status = Quo.prototype.get_status.apply(statusObject);
	// status 는 'A-OK'

#### 04 | 인수 배열 (arguments)
****
함수를 호출할 때 추가적인 매개변수로 `arguments` 라는 `배열`을 사용할 수 있다.<br>
이 배열을 함수를 호출할 때 전달된 모든 인수를 접근할 수 있게 한다.

	// 여러 작업을 수행하는 함수를 만듦.
	// 함수 내부에 있는 sum 이라는 변수는
	// 외부에 있는 sum 변수에 영향을 미치지 않는 것에 주목.
	// 함수는 오로지 내부의 sum 에만 영향을 미침.
	var sum = function () {
		var i, sum = 0;
		for (i = 0; i < arguments.length; i += 1) {
			sum += arguments[i];
		}
		return sum;
	};

	console.log(sum(4, 8, 15, 16, 23, 42));					// 108

> 설계상의 문제로 `arguments` 는 실제 `배열은 아니다`. <br>
> `arguments` 는 `배열 같은 객체`이다.<br>
> 왜냐하면 `arguments` 는 `length` 라는 속성이 있지만 모든 배열이 가지는 메소드들은 없다.

#### 05 | 반환
****
반환값이 지정되지 않은 경우에는 undefined 가 반환된다.<br>
함수를 new 라는 전치 연산자와 함께 실행하고 반환값이 객체가 아닌 경우 반환값은 `this (새로운 객체)`가 된다.

#### 06 | 예외
****
비정상적인 사고가 발생하면 프로그램은 예외를 발생한다.

	var add = function (a, b) {
		if (typeof a !== 'number' || typeof b !== 'number') {
			throw {
				name: 'TypeError',
				message: 'add needs numbers'
			};
		}

		return a + b;
	}

throw 문은 함수의 실행을 중단한다.<br>
throw 문은 어떤 예외인지 알 수 있게 해주는 name, message 속성을 가진 객체를 반환해야 한다.<br>
(물론 속성를 더 추가 할 수 있다.)

	// 새로운 add 함수를 `잘못된 방법으로 호출`하는 try_it 함수 작성
	var try_it = function () {
		try {
			add('seven');								// 위 add 의 매개변수는 number
		}
		catch (e) {
			console.log(e.name + ': ' + e.message);
		}
	}

	try_it();

#### 07 | 기본 타입에 기능 추가
****
자바스크립트는 언어의 기본 타입에 기능을 추가하는 것을 허용한다.<br>
앞선 3장에서 Object.prototype 에 메소드를 추가하여 모든 객체에서 이 메소드를 사용 가능하게 하는 것을 보았다.<br>
이러한 작업은 `함수`, `배열`, `문자열`, `숫자`, `정규 표현식`, `불리언`에 모두 유효하다.

	// Function.prototype 에 method 를 추가하여 모든 함수에서 이 메소드를 사용 할 수 있게 함.
	Function.prototype.method = function (name, func) {
		this.prototype[name] = func;
		return this;
	};

위와 같이 메소드를 추가 하면 Function.prototype에 메소드를 추가할 때 (.prototype) 부분 없이 깔끔하게 사용 할 수 있다.

	Number.method('integer', function () {
		return Math[this < 0 ? 'ceiling' : 'floor'](this);
	});

	console.log((-10 / 3).integer());					// -3

문자열의 양 끝에 있는 빈칸을 지우는 메소드 추가.

	String.method('trim', function () {
		return this.replace(/^\s+|\s+$/g, '');
	});

	console.log('"' + "      neat    ".trim() + '"');	// 문자열에서 바로 사용 가능 하다.

이러한 프로토타입에 의한 상속은 해당값이 새로운 메소드가 추가되기 전에 생성됐더라도 관계없이 적용된다.

	// 조건에 따라 메소드를 추가.
	// 존재하지 않는 메소드만 추가.
	Function.prototype.method = function (name, func) {
		if (!this.prototype[name]) {
			this.prototype[name] = func;
		}
	};

#### 08 | 재귀적 호출
****
일반적으로 재귀 함수는 하위 문제를 처리하기 위해 자신을 호출한다.

	// 하노이 탑
	var hanoi = function (disc, src, aux, dst) {
		if (disc > 0) {
			hanoi(disc - 1, src, dst, aux);
			console.log('Move disc ' + disc + ' from ' + src + ' to ' + dst);
			hanoi(disc - 1, aux, src, dst);
		}
	};

	hanoi(3, 'Src', 'Aux', 'Dst');

재귀 함수는 웹 브라우저의 DOM(Document Object Model) 같은 트리 구조를 다루는 데 매우 효과적이다.<br>
즉 각각의 재귀적 호출이 트리 구조의 항목 하나에 대해 작동하면 효율적인 트리 구조를 다룰 수 있다.

	// 주어진 노드부터 HTML 소스 순으로 DOM 트리의
	// 모든 노드를 방문하는 walk_the_DOM 함수 정의.
	// 이 함수는 차례로 각각의 노드를 넘기면서 함수를 호출.
	// walk_the_DOM은 각각의 자식 노드들을 처리하기 위해서 자신을 호출함.

	var walk_the_DOM = function walk(node, func) {
		func(node);
		node = node.firstChild;
		while (node) {
			walk(node, func);
			node = node.nextSibling;
		}
	};

	// getElementsByAttribute 함수 정의.
	// 이 함수는 어트리뷰트 이름(att)과 일치하는 값(value, 이 값은 넘기지 않아도 되는 옵션임)을 인수로 받음.
	// 이 함수는 노드에서 어트리뷰트 이름을 찾는 함수를 전달하면서
	// walk_the_DOM 을 호출.
	// 일치하는 노드는 results 배열에 저장됨.

	var getElementsByAttribute = function (att, value) {
		var result = [];

		walk_the_DOM(document.body, function (node) {
			var actual = node.nodeType === 1 && node.getAttribue(att);
			if (typeof actual === 'string' &&
					(actual === value || typeof value !== 'string')) {
				results.push(node);
			}
		});

		return results;
	};

아래는 tail recursion 방식으로 자바스크립트에서는 반환 스택의 과다 사용으로 제대로 실행 안될 수 있다.<br>
(자신을 매우 깊은 단계까지 호출 할 경우)

	// tail 재귀를 하는 계승(factorial) 함수를 만듦.
	// 호출 자체의 결과를 반환하기 때문에 tail 재귀임.

	// 현재 자바스크립트는 이러한 유형에 대해 최적화를 제공하지 않음.
	var factorial = function factorial(i, a) {
		a = a || 1;
		if (i < 2) {
			return a;
		}
		return factorial(i-1, a * i);
	};

	console.writeln(factorial(4));						// 24	

#### 09 | 유효범위(Scope)
****
프로그래밍 언어에서 유효범위는 변수와 매개변수의 접근성과 생존 기간을 제어한다.<br>
(이름들이 충돌하는 문제를 덜어주고 자동으로 메모리를 관리한다.)

	var foo = function () {
		var a = 3, b = 5;
		var bar function () {
			var b = 7, c = 11;

			// 이 시점에서 a는 3, b는 7, c는 11
			a += b + c;

			// 이 시점에서 a는 21, b는 7, c는 11
		};

		// 이 시점에서 a는 3, b는 5, c는 정의되지 않음.
		bar();

		// 이 시점에서 a는 21, b는 5
	};

C 에서는 블록내에서 정의된 변수는 블록의 실행이 끝나면 해제 된다.<br>
그러나<br>
자바스크립트에서는 지원하는 듯 보이나 블록 구조를 지원하지 않는 다.<br>

자바스크립트는 함수 유효범위가 있으며, 함수에서 사용하는 모든 변수는 함수의 첫 부분에 선어하는 게 좋다.

	// C 예제
	#include <stdio.h>

	int main() {
		int a = 0;

		// 블록
		{
			int b = 1;
			printf ("%d\n", a + b);
		}

		return 0;
	}


#### 10 | 클로저(closure)
****
유효범위에 관한 좋은 소식 하나는 내부 함수에서 자신을 포함하고 있는 외부 함수의 매개변수와 변수들을 접근할 수 있다는 것이다. (this 와 arguments는 예외)

	// results 라는 변수를 walk_the_DOM 의 인수로 넘긴 (내부) 함수에서 접근하고 있다.
	var getElementsByAttribute = function (att, value) {
		var result = [];

		walk_the_DOM(document.body, function (node) {
			var actual = node.nodeType === 1 && node.getAttribue(att);
			if (typeof actual === 'string' &&
					(actual === value || typeof value !== 'string')) {
				results.push(node);
			}
		});

		return results;
	};

아래 예제의 경우는 myObject 객체에서 허락되지 않은 경우에는 value 속성의 값을 변경 할 수 없도록 한다.
(유효 범위 때문에 value 라는 변수는 메소드에 의해서만 접근 가능하다.)

	var myObject = function () {
		var value = 0;

		// 객체 리터럴을 반환한다. (메소드 2개를 가진 객체 반환)
		return {
			increment: function (inc) {
				value += typeof inc === 'number' ? inc : 1;
			},
			getValue: function () {
				return value;
			}
		};
	}(); 	// 함수를 호출한 결과를 할당 하고 있다. (함수를 할당 하는 게 아님)

아래 quo 함수는 new 키워드 없이 사용하게 설계됐다. <br>
quo를 호출하면 get_status 메소드가 있는 객체를 반환한다.<br>
이 객체에 대한 참조는 myQuo에 저장된다.<br>
get_status 메소드는 quo가 이미 반환된 뒤에서 quo의 status에 접근할 수 있는 권한을 가지게 된다.<br>

get_status 는 status 매개변수의 복사본에 접근할 수 있는 권한을 갖는 것이 아니라<br>
매개변수 그 자체에 대한 접근 권한을 갖는다.<br>

이러한 것이 가능한 것은 함수가 자신이 생성된 함수, 즉 자신을 내포하는 함수의 문백(context)네 접근할 수 있기 때문이다.

### 이것을 클로저(closure)라고 부른다.

	// quo 라는 함수를 생성.
	// 이 함수는 get_status 라는 메소드와
	// status 라는 private 속성을 가진 객체를 반환.
	var quo = function (status) {
		return {
			get_status: function () {
				return status;
			}
		};
	};

	// quo 의 인스턴스를 생성.
	var myQuo = quo('amazed');
	
	console.log(myQuo.get_status());

유용한 예제

	// DOM 노드의 색을 노란색으로 지정하고 흰색으로 사라지게 하는 함수 정의.
	var fase = function (node) {
		var level = 1;
		var step = function () {
			var hex = level.toString(16);

			node.style.backgroundColor = '#FFFF' + hex + hex;
			if ( level < 15) {
				level += 1;
				setTimeout(step, 100);
			}
		};
		setTimeout(step, 100);
	};

	fade(document.body);

1. document.body (html 태그)를 넘기면서 fade를 호출
2. fade 는 level 의 값을 1로 설정, step 이라는 함수 정의
3. fade 는 setTimeout을 호출 후 종료
4. 1/10 초 뒤 step 함수 호출
5. step 은 level 값을 16진수로 변경
6. step 은 level 값이 15 보다 작으면 level 값을 증가 시킨 후 setTimeout 으로 같은 작업 반복
7. 1/10 초 뒤 step 에서 참조 하는 값은 level = 2 가 된다.

fade 함수는 이미 반환 됐지만 함수 안의 변수는 이를 필요로 하는 내부 함수가<br>
하나 이상 존재 하는 경우 계속 유지 된다.

내부 함수가 외부 함수에 있는 변수의 복사본이 아니라 실제 변수에
접근한다는 것을 이해해야 한다. 그렇지 않으면 다음과 같은 문제가 발생 할 수 있다.

add_the_handlers 함수는 각각의 핸들러에 유일한 번호(i)를 전달하도록 고안됐다.<br>
하지만 이러한 의도대로 동작하지 않는 데 그 이유는 핸들러 함수가 받는 i 가 함수가 만들어지는 시점의 i가 아니라 그냥 변수 i에 연결되기 때문이다.

	// 나쁜 예제

	// 잘못된 방법으로 노드 배열에 이벤트 핸들러 함수를 할당하는 함수 정의.
	// 노드를 클릭하면 해당 노드가 몇 번째 노드인지를 경고창으로 알려 주는 것이
	// 함수의 목적.
	// 하지만 항상 전체 노드의 수만을 보여줌.
	var add_the_handlers = function (nodes) {
		var i;
		for (i = 0; i < nodes.length; i += 1) {
			nodes[i].onclick = function (e) {				// onclick 에 함수 할당
				alert(i);									// for loop 이후 마지막 i 값이 리턴됨.
			};
		}
	};

	// 나쁜 예제 끝

	// 더 나은 예제

	// 올바른 방법으로 노드 배열에 이벤트 핸들러 함수를 할당하는 함수 정의.
	// 노드를 클릭하면 해당 노드가 몇 번째 노드인지를 경고창으로 알려줌.
	var add_the_handlers = function (nodes) {
		var i;
		for (i = 0; i < nodes.length; i += 1) {
			nodes[i].onclick = function (i) {				// onclick 에 새로운 함수를 정의하면서 곧 바로 실행
				return function (e) {
					alert(i);
				};
			}(i);
		}
	};


#### 11 | 콜백
****
함수는 비연속적인 이벤트를 다루는 것을 좀 더 쉽게 할 수 있는 방법을 제공한다.

	// 동기식 (비추천)
	// 서버의 응답이 올 때까지 기다린다.
	request = prepare_the_request();
	response = send_request_synchronously(request);
	display(response);


	// 비동기식 (추천)
	// 서버의 응답을 기다리지 않고 그 즉시 반환된다.
	// 응답이 왔을 때만 콜백 함수를 실행 한다.
	request = prepare_the_request();
	send_request_asynchronously(request, function (response) {
		display(reponse);
	});

> 보통 Ajax 의 XmlHttpRequest를 사용하여 비동기적으로 서버에 요청 하는 예가 있다.

	var req = new XMLHttpRequest();
	req.open('GET', 'http://www.mozilla.org/', true);
	req.onreadystatechange = function (aEvt) {
		if (req.readyState == 4) {
			if(req.status == 200)
				dump(req.responseText);
			else
				dump("Error loading page\n");
		}
	};
	req.send(null);

#### 12 | 모듈
****
함수와 클로저를 사용해서 모듈을 만들 수 있다.<br>
모듈을 만들기 위해서 함수를 사용하면 전역변수 사용을 거의 대부분 제거할 수 있기 때문에 결국 자바스크립트의 최대 약점 중 하나를 보완할 수 있다.

> 모듈이란? 내부의 상태나 구현 내용은 숨기고 인터페이스만 제공하는 함수나 객체이다.

문자열에서 HTML 엔티티들을 찾고 이들을 그에 상응하는 문자로 대체 하는 모듈의 예제

	String.method('deentityify', function() {
		var entity = {
			quot: '"',
			lt: '<',
			qt: '>'
		};

		// deentityify 메소드 반환.
		return function () {
			// 여기가 deentityify 메소드
			// 문자열의 replace 메소드를 호출하여 &로 시작하고 ;로 끝나는
			// 부분을 찾고 &와 ; 사이의 문자열이 엔티티 테이블에 있으면
			// 해당 문자로 엔티티를 대체. 정규 표현식 사용 (7장 참조).

			return this.replace(/&([^&;]+);/g, function (a,b) {
	
				console.log('a = [' + a + '], b = [' + b + ']');

				var r = entity[b];
				return typeof r === 'string' ? r : a;
			});
		};
	}());									// 함수를 바로 호출 한다.
											// 이 호출로 deentityify 메소드가 되는 
											// 함수를 생성해서 반환한다.

	document.writeln('&lt;&quot;&qt;'.deentityify());	// <"> 
.
	a = [&lt;], b = [lt]
	a = [&quot;], b = [quot]
	a = [&qt;], b = [qt]

모듈 패턴은 바인딩과 private 을 위해 함수의 유효범위와 클로저를 이용한다.<br>
이 예제에서는 deentityify 메소드만이 엔티티들을 담고 있는 데이터 구조인 entity 객체에 접근 할 수 있다.

> string.replace(regexp, replacement) <br>
> reqexp : 교체할 패턴을 지정하는 RegExp 객체이다.<br>
> replacement : 기존 문자열을 대체할 텍스트 문자열이거나 대체할 텍스트를 반환하는 함수이다.<br>
> 반환값 : regexp의 첫 번째 매치 혹은 모든 매치를 replacement로 교체한 새 문자열<br>
> replacement 가 문자열이면 각 매치는 주어진 문자열로 교체 된다.<br>
> replacement 가 함수이면 첫번째 인자는 패턴에 매치된 문자열, 두번째 인자는 패턴표현식에 매치된 문자열들이다.<br>

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
