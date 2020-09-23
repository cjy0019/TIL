# 데이터 타입(data type)

**자바스크립트의 모든 값은 데이터 타입을 갖는데 자바스크립트(ES6)는 7개의 데이터 타입을 제공한다.**

## 원시 타입(primitive type) - immutable value

- 숫자(number) 타입 : 숫자로 정수와 실수 구분 없이 하나의 숫자 타입만 존재
- 문자열(string) 타입 : 문자열
- 불리언(boolean) 타입 : 논리적 참(true) 과 거짓(false)
- undefined 타입 : var 키워드로 선언된 변수에 암묵적으로 할당되는 값
- null 타입 : 값이 없다는 것을 의도적으로 명시할 때 사용하는 값
- 심벌(symbol) 타입 : ES6에 추가된 7번째 타입

## 객체 타입(object/ reference type)  - mutable value

- 객체 
- 함수
- 배열



## 숫자 타입

C나 자바의 경우, 정수(소수점 이하가 없는 숫자)와 실수(소수점 이하가 있는 숫자를 구분해서) `int, long, float, double`등과 같은 다양한 숫자 타입을 제공한다. 그러나 자바스크립트는 하나의 숫자 타입만 존재한다.

ECMAScript 사양에 따르면 숫자 타입의 값은 배정밀도 64비트 **부동소수점 형식(double precision 64-bit floating-point format)**을 따른다. <span style=color:red>모든 수를 실수로 처리하고, 정수만 표현하기 위한 데이터 타입이 별도로 존재하지 않는다!</span>

```javascript
var integer = 10; // 정수
var double = 10.12 // 실수
var negative = -29; // 음의 정수
```

자바스크립트의 숫자 타입은 정수만을 위한 타입이 없고 모든 수를 실수로 처리한다고 한다. 이는 정수로 표시된다 해도 실수라는 것을 의미한다.

자바스크립트는 2진수, 8진수, 16진수를 표현하기 위한 데이터 타입을 제공하지 않기 때문에 이들 값을 참조하면 모두 10진수로 해석된다.

```javascript
var binary = 0b01000001; // 2진수
var octal = 0o101;       // 8진수
var hex = 0x41;          // 16진수

// 표기법만 다를 뿐 모두 같은 값이다.
console.log(binary); // 65
console.log(octal);  // 65
console.log(hex);    // 65
console.log(binary === octal); // true
console.log(octal === hex);    // true
```



```javascript
// 숫자 타입은 모두 실수로 처리된다.
console.log(1 === 1.0); //true
console.log(4/2); // 2
console.log(3/2); //1.5
```

숫자 타입은 세가지 특별한 값도 나타낼 수 있다.

```javascript
console.log(10 / 0); // Infinity
console.log(10 / -0); //-Infinity
console.log(1 * 'String') // NaN
```

**데이터 타입은 값이 가지고 있다 따라서 변수는 타입을 가지고 있지 않다. 하지만 변수에 값이 할당되는 시점에 값에 의해 변수의 타입이 결정된다**



## 문자열 타입

문자열(string)은 0개 이상의 <span style=color:red>16비트 유니코드 문자(UTF-16)</span>들의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.
일반적으로 <span style=color:red>작은 따옴표(' '), 큰따옴표(" "), 백틱(``)</span>, 를 사용한다.
자바스크립트의 문자열은 원시 타입이고 변경 불가능한 값(immutable value)이다.

```javascript
// 문자열 타입
var string;
string = '문자열';
string = "문자열";
string = `문자열`; 

string = '작은따옴표로 감싼 문자열 내의 "큰따옴표"는 문자열로 인식된다.';
string = "큰따옴표로 감싼 문자열 내의 '작은따옴표'는 문자열로 인식된다.";
```



**문자열을 따옴표로 감싸는 이유&#10067; **

키워드나 **식별자 같은 토큰과 구분하기 위해서고** 따옴표로 문자열 을 감싸지 않는다면 스페이스와 같은 공백 문자도 포함시킬 수 없다. 

```javascript
// 따옴표로 감싸지 않은 hello를 식별자로 인식한다.
var string = hello; // ReferenceError: hello is not defined
```

```javascript
var str = '작은 따옴표로 감싼 문자열 내의 \'큰따옴표\'는 문자열로 인식된다.';
```



- C는 문자열 타입을 제공하지 않고 문자의 배열로 문자열을 표현하고, 자바는 문자열을 객체로 표현한다.
- **그러나 자바스크립트의 문자열은 원시 타입이며, 변경 불가능한 값(immutable value)**이다.
- 이것은 문자열이 생성되면 그 문자열을 변경할 수 없다는 것을 의미한다.
- C나 Java와 같은 언어와는 다르게 자바스크립트의 문자열은 원시 타입이며 변경 불가능한 값(immutable value)이다.



## 템플릿 리터럴

ES6부터 템플릿 리터럴(Template Literal) 이라고 하는 *문자열 표기법*이 도입되었다.

1. 멀티라인 문자열(multi-line string)
2. 표현식 삽입(expression interpolation)
3. 태그드 템플릿(tagged template) 등을 처리한다.

**템플릿 리터럴은 런타임에 일반 문자열로 변환되어 처리된다. 백틱(``)을 사용해 표현됨**

```javascript
var template = `Template literal`;
console.log(template); // Template literal
```



## 멀티라인 문자열

- 일반 문자열 내에서는 개행이 허용되지 않는다.
  따라서 일반 문자열 내에서 줄바꿈 등의 공백(white space)을 표현하려면 백슬래시(`\`)로 시작하는 <span style=color:red>이스케이프 시퀀스</span>(escape sequence)를 사용해야 한다.

```javascript
var str = 'Hello
world.';
// SyntaxError: Invalid or unexpected token
```

```javascript
var template = `<ul>
	<li><a href='#'>Home</a></li>
</ul>`;

console.log(template);
/*
<ul>
  <li><a href="#">Home</a></li>
</ul>
*/
// 템플릿 리터럴에서는 개행처리를 해준다
```



## 표현식 삽입

문자열은 문자열 연산자 +를 사용해 연결할 수 있다. `+`연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다.

**템플릿 리터럴 **내에서는 표현식 삽입을 통해 간단히 문자열을 삽입할 수 있다.

- 표현식을 삽입하려면 `${}`으로 표현식을 감싼다.
- 이 때 표현식의 평가 결과가 문자열이 아니더라도 문자열로 타입이 강제로 변환되어 삽입된다.

```javascript
var first = 'Jae yeon';
var last = 'Cho';

console.log(`My name is ${first} ${last}.`); // My name is Jae yeon Cho.
```



## 불리언 타입

불리언 타입의 값은 논리적 참, 거짓을 나타내는 `true`와 `false` 뿐이다.

```javascript
var foo = true;
console.log(foo); // true

foo = false;
console.log(foo); // false
```



## undefined 타입

- `undefined`타입의 값은 `undefined`가 유일하다.
- `var`키워드로 선언한 변수는 암묵적으로  `undefined`로 초기화된다.

```javascript
var foo;
console.log(foo); // undefined
```

- 이처럼 ` undefined`는 개발자가 의도적으로 할당하기 위한 값이 아니라 자바스크립트 엔진이 변수를 초기화할 때 사용하는 값이다.
- 변수를 참조했을 때 `undefined`가 반환된다면 참조한 변수가 선언 이후 값이 할당된 적이 없는 , 초기화되지 않은 변수라는 것을  간파할 수 있다.
- 먄약 변수에 값이 없다는 것을 명시하고 싶을 때는 `undefined`가 아니라 `null`을 할당한다.



## null 타입

null 타입은 값은 null이 유일하다. 자바스크립트는 대소문자를 구별(case-sensitive하므로 null은 NULL과 다르다.
**프로그래밍 언어에서 null은 변수에 값이 없다는 것을 의도적으로 명시(의도적 부재. intentional absence)할 때 사용한다**

- 변수에 `null`을 할당하는 것은 변수가 이전에 참조하던 값을 더이상 참조하지 않겠다는 의미이다.

```javascript
var foo = 'Lee';

// 이전에 할당되어 있던 값에 대한 참조를 제거. foo 변수는 더 이상 'Lee'를 참조하지 않는다.
// 유용해 보이지는 않는다. 변수의 스코프를 좁게 만들어 변수 자체를 재빨리 소멸시키는 편이 낫다.
foo = null;
```



## symbol 타입

symbol은 ES6에서 추가된 타입으로 변경 불가능한 원시 타입의 값이다. 심벌 값은 다른 값과 중복되지 않는 유일무이한 값이다.

**symbol은 Symbol() 함수를 호출해 생성한다**

```javascript
// 심벌 값 생성
var key = Symbol('key');
console.log(typeof key); //symbol


var obj = {}; // 객체 생성
// 이름이 충돌할 위험이 없는 유일무이한 값인 심벌을 프로퍼티 키로 사용한다.
obj[key] = 'value';
console.log(obj[key]); //value
```



## 객체 타입

- 자바스크립트의 데이터 타입은 크게 원시 타입과 객체 타입으로 분류한다고 했다.
- 둘을 구분한 이유는 근본적으로 다르다는 의미일 것이다.
- 중요한 것은**자바스크립트는 객체 기반의 언어이며, 자바스크립트를 이루고 있는 거의 모든 것이 객체**라는 것이다.



## 데이터 타입의 필요성

### 데이터 타입에 의한 메모리 공간의 확보와 참조

값은 메모리에 저장하고 참조할 수 있어야 한다. 몇 바이트의 메모리 공간을 사용해야 낭비와 손실없이 값을 저장할 수 있는지를 알아야 한다. 

```javascript
var score = 100;
```

위 코드가 실행되면 컴퓨터는 숫자 값 100을 저장하기 위해 메모리 공간을 확보한 다음, 확보된 메모리에 숫자 100을 2진수로 저장한다. 이 때 자바스크립트 엔진은 데이터 타입, 값의 종류에 따라 정해진 크기의 메모리 공간을 확보한다.

​                                                                 <img src="https://poiemaweb.com/assets/fs-images/6-1.png" style="zoom: 50%;" />

### 참조        

식별자 score를 통해 숫자 타입의 값 100이 저장되어 있는 메모리 공간의 선두 메모리 셀의 주소를 찾아갈 수 있다.
값을 참조하려면 한 번에 읽어 들여야 할 바이트 수를 알아야 한다. score 변수의 경우 숫자 타입이므로 8바이트 단위로 읽어 들여야 한다.

- 값을 저장할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해
- 값을 참조할 때 한번에 읽어 들여야 할 메모리 공간의 크기를 결정하기 위해
- 메모리에서 읽어들인 2진수를 어떻게 해석할지 결정하기 위해 데이터 타입이 필요하다.



## 동적 타이핑

### 동적 타입 언어와 정적 타입 언어

변수는 데이터 타입을 가질까?

#### 정적 타입

- C나 자바 같은 **정적 타입(static/strong type)** 언어는 변수를 선언할 때 변수에 할당할 수 있는 값의 종류, 즉 데이터 타입을 사전에 선언한다.
- 이를 **명시적 타입 선언(explicit type declaration)**이라 한다.

```c
// c 변수에는 1바이트 정수 타입의 값(-128 ~ 127)만을 할당할 수 있다.
char c;

// num 변수에는 4바이트 정수 타입의 값(-2,124,483,648 ~ 2,124,483,647)만을 할당할 수 있다.
int num;
```

- 정적 타입 언어는 변수의 타입을 변경할 수 없으며, 변수에 선언한 타입에 맞는 값만 할당할 수 있다.
- 정적 타입 언어는 **컴파일 시점에 타입 체크(선언한 데이터 타입에 맞는 값을 할당했는지 검사하는 처리)를 수행한다.**
- 만약 타입 체크를 통과하지 못하면 에러를 발생시키고 프로그램의 실행 자체를 막는다.



#### 동적 타입

- 반면 자바스크립트는 변수를 선언할 때 타입을 선언하지 않는다. `var, let, const`키워드를 사용할 뿐이다.
- 자바스크립트의 변수는 정적 타입 언어와 같이 미리 선언한 데이터 타입의 값만 할당할 수 있는 것이 아니다. 어떠한 데이터 타입의 값이라도 자유롭게 할당할 수 있다.

```javascript
var foo;
console.log(typeof foo); // undefined

foo = 3;
console.log(typeof foo); // number

foo = 'Hello';
console.log(typeof foo); // string

foo = true;
console.log(typeof foo); // boolean

foo = null;
console.log(typeof foo); // object

foo = Symbol();
console.log(typeof foo); // symbol

foo = {};
console.log(typeof foo); // object

foo = [];
console.log(typeof foo); // object

foo = function(){};
console.log(typeof foo); // number
```

- `typeof`연산자로 변수를 연산하면 변수의 데이터 타입을 반환한다. 정확히는 변수에 할당된 값의 데이터 타입을 반환한다.

- **정적 타입 언어는 변수 선언 시점에 변수의 타입이 결정되고 변수의 타입을 변경할 수 없지만 자바스크립트에서는 값을 할당하는 시점에 변수의 타입이 동적으로 결정되고 변수의 타입을 언제든지 자유롭게 변경할 수 있다.**

**결론 : 자바스크립트 변수는 선언이 아닌 할당에 의해 타입이 결정(타입 추론. type inference)된다. 그리고 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다.** 이러한 특징을 **동적 타이핑(dynamic typing)**이라 하며, 자바스크립트를 정적 타입 언어와 구별하기 위해 **동적 타입(dynamic/weak type) 언어**라 한다.



## 동적 타입 언어와 변수

동적 타입 언어는 변수에 어떤 데이터 타입의 값이라도 자유롭게 할당할 수 있다. 모든 소프트웨어 아키텍처에는 **트레이드오프(trade-off)**가 존재하듯 자바스크립트의 이러한 특성에도 구조적인 단점이 있다.

### 단점

- 변수 값은 언제든지 변경될 수 있기 때문에 복잡한 프로그램에서는 변화하는 변수 값을 추적하기 어렵다.
- 변수 타입이 고정되어 있지 않고 동적으로 변하는 동적 타입 언어의 변수는 값의 변경에 의해 타입도 언제든지 변경될 수 있다. 즉, **동적 타입 언어의 변수는 값을 확인하기 전에는 타입을 확신할 수없다.**
- 자바스크립트는 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 변환되기도 한다. 즉 이러한 특성 때문에 잘못된 예측이 생겨날 수 있고 이는 결국 **유연성은 높지만 신뢰성은 떨어진다는 말을 뜻하게 된다.**



## 변수 사용의 주의 사항

1. 변수는 꼭 필요한 경우에 한해 제한적으로 사용한다. 변수값은 재할당에 의해 언제든지 변경될 수 있기 때문에 오류가 발생할 가능성이 크다.
2. 변수의 유효 범위(스코프)는 최대한 좁게 만들어 변수의 부작용을 억제해야 한다.
3. 전역 변수는 최대한 사용하지 않도록 한다. 어디서든지 참조/변경 가능한 전역 변수는 의도치 않게 값이 변경될 가능성이 높고 다른 코드에 영향을 줄 가능성도 높다.
4. 변수보다는 상수를 사용해 값의 변경을 억제한다.
5. 변수의 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍한다.

