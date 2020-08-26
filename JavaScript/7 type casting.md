# 타입 변환(type casting)과 단축 평가


<u>개발자가 의도적으로 값의 타입을 변환하는 것을 **명시적 타입 변환(explicit coercion)** 또는 **타입 캐스팅(type casting)**이라 한다.</u>

```javascript
var x = 10;

//명시적 타입 변환
var str = x.toString(); 
console.log(typeof str, str); //string 10

console.log(typeof x, x); // number 10
```

개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되는 것을 **암묵적 타입 변환(implicit coercion)** 또는 **타입 강제 변환(type coercion)**이라고 한다.

```javascript
var x = 10;

// 암묵적 타입 변환
var str = x + '';
console.log(typeof str, str); // string 10

console.log(typeof x, x); // number 10
```

명시적 타입 변환이나 암묵적 타입 변환이 기존 원시 값을 직접 변경하는 것은 아니다. 기존 원시 값을 이용해 다른 타입의 새로운 원시 값을 생성하는 것이다.



## 암묵적 타입 변환

```javascript
'10' + 2 // -> '102'

5 * '10' // -> '50'

// 피연산자 또는 표현식이 불리언 타입이어야 하는 문맥
!0 // true
if(1) {}
```



## 문자열 타입으로 변환

자바스크립트 엔진은 문자열 연결 연산자 표현식을 평가하기 위해 문자열 연결 연산자의 피연산자 중에서 문자열 타입이 아닌 피연산자를 문자열로 **암묵적 변환**한다.

```javascript
`1 + 1 = ${1 + 1}` // "1 + 1 = 2"
```

```javascript
0 + '' // "0"
-0 + '' // "0"
NaN + '' // "NaN"

true + '' // "true"

null + '' // "null"

undefined + '' // "undefined"

(Symbol()) + '' // TypeError : Cannot convert a Symbol value to a String

({}) + '' // "[object Object]"
Math + '' // "[object Math]"
[] + '' // ""
```



## Boolean 타입으로 변환

<span style=color:pink>아래 값들은 false로 평가되는 Falsy 값이다</span>

- false
- undefined
- null
- 0, -0
- NaN
- "(빈 문자열)



## 명시적 변환하는 여러 가지 방법

### 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메서드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법

```javascript
// 1번
String(1); // "1"
String(NaN); // "NaN"

// 2번
(1).toString(); // "1"
(Infinity).toString(); // "Infinity"

// 3번
1 + ''; // "1"
Infinity + ''; // "Infinity"
```



### 숫자 타입으로 변환

1. Number 생성자 함수를 호출
2. parseInt, parseFloat 함수를 사용하는 법
3. 단항 산술 연산자를 사용
4. '*' 산술 연산자를 이용하는 방법

```javascript
// 1번
Number('0'); // 0
Number('10.53') // 10.53

// 2번
parseInt('0'); // 0
parseFloat('10.53') // 10.53

// 3번
+'0'; // 0
+'10.53'; // 10.53

// 4번
'0' * 1; // 0
true * 1; // 1
```



### 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
2. ! 부정 논리 연산자를 두 번 사용하는 방법

```javascript
// 1번
Boolean('x'); // true
Boolean('false'); // true
Boolean({}); // true

// 2번
!!'x'; // true
!!''; // false
!!null; //false
```



## 단축 평가

```javascript
'Cat' && 'Dog' // "Dog"
```

논리곱 연산자는 두 개의 피연산자가 모두 true로 평가될 때 true를 반환한다.

**즉, 앞의 'Cat' 이 true 일 때 뒤에 'Dog'에 의해 연산결과가 결정되므로 'Dog'를 반환한다.**