# 데이터 타입(data type)

**자바스크립트(ES6)는 7개의 데이터 타입을 제공한다.**

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

ECMAScript 사양에 따르면 숫자 타입의 값은 배정밀도 64비트 **부동소수점 형식(double precision 64-bit floating-point format)**을 따른다. <span style=color:pink>모든 수를 실수로 처리하고, 정수만 표현하기 위한 데이터 타입이 별도로 존재하지 않는다!</span>

```javascript
var integer = 10; // 정수
var double = 10.12 // 실수
var negative = -29; // 음의 정수
```

자바스크립트의 숫자 타입은 정수만을 위한 타입이 없고 모든 수를 실수로 처리한다고 한다. 이는 정수로 표시된다 해도 실수라는 것을 의미한다.

```javascript
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

문자열은 0개 이상의 <span style=color:pink>16비트 유니코드 문자(UTF-16)</span>들의 집합으로 전 세계 대부분의 문자를 표현할 수 있다.
일반적으로 <span style=color:pink>작은 따옴표</span>를 사용한다.
자바스크립트의 문자열은 원시 타입이고 변경 불가능한 값(immutable value)이다.

**문자열을 따옴표로 감싸는 이유&#10067; **

키워드나 식별자 같은 토큰과 구분하기 위해서고 따옴표로 문자열 을 감싸지 않는다면 스페이스와 같은 공백 문자도 포함시킬 수 없다. 

```javascript
var str = '작은 따옴표로 감싼 문자열 내의 \'큰따옴표\'는 문자열로 인식된다.';
```



## 템플릿 리터럴

ES6부터 Template Literal 이라고 하는 *문자열 표기법*이 도입되었다.

1. 멀티라인 문자열(multi-line string)
2. 표현식 삽입(expression interpolation)
3. 태그드 템플릿(tagged template) 등을 처리한다.

**템플릿 리터럴은 런타임에 일반 문자열로 변환되어 처리된다. 백틱(``)을 사용해 표현됨**

```javascript
var template = `Template literal`;
```



## 멀티라인 문자열

일반 문자열 내에서는 개행이 허용되지 않는다.
따라서 일반 문자열 내에서 줄바꿈 등의 공백(white space)을 표현하려면 백슬래시로 시작하는 <span style=color:pink>이스케이프 시퀀스</span>를 사용해야 한다.

```javascript
var template = `<ul>
	<li><a href='#'>Home</a></li>
</ul>`;
// 템플릿 리터럴에서는 개행처리를 해준다
```



## 표현식 삽입

문자열은 문자열 연산자 +를 사용해 연결할 수 있다.

**템플릿 리터럴 **내에서는 표현식 삽입을 통해 간단히 문자열을 삽입할 수 있다.

```javascript
var first = 'Jae yeon';
var last = 'Cho';

console.log(`My name is ${first} ${last}.`); // My name is Jae yeon Cho.
```



## null 타입

null 타입은 값은 null이 유일하다. 자바스크립트는 대소문자를 구별하므로 null은 NULL과 다르다.
**프로그래밍 언어에서 null은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용한다**



## symbol 타입

symbol은 ES6에서 추가된 타입으로 변경 불가능한 원시 타입의 값이다. 심벌 값은 다른 값과 중복되지 않는 유일무이한 값이다.

**symbol은 Symbol() 함수를 호출해 생성한다**

```javascript
var key = Symbol('key');
console.log(typeof key); //symbol


var obj = {}; // 객체 생성

obj[key] = 'value';
console.log(obj[key]); //value
```



## 데이터 타입에 의한 메모리 공간의 확보와 참조

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

자바스크립트는 변수 선언이 아닌 할당에 의해 타입이 결정된다. 그리고 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다. 이러한 특징을 **동적 타이핑(dynamic typing)**이라 하며, 자바스크립트를 정적 타입 언어와 구별하기 위해 **동적 타입(dynamic/weak type)** 언어라 한다.



## 변수 사용의 주의 사항

1. 변수는 꼭 필요한 경우에 한해 제한적으로 사용한다. 변수값은 재할당에 의해 언제든지 변경될 수 있기 때문에 오류가 발생할 가능성이 크다.
2. 변수의 유효 범위(스코프)는 최대한 좁게 만들어 변수의 부작용을 억제해야 한다.
3. 전역 변수는 최대한 사용하지 않도록 한다. 어디서든지 참조/변경 가능한 전역 변수는 의도치 않게 값이 변경될 가능성이 높고 다른 코드에 영향을 줄 가능성도 높다.
4. 변수보다는 상수를 사용해 값의 변경을 억제한다.
5. 변수의 이름은 변수의 목적이나 의미를 파악할 수 있도록 네이밍한다.
