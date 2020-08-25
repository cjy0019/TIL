

# 연산자(operator)

- 연산자(operator)는 하나 이상의 표현식을 대상으로 산술, 할당, 비교, 논리, 타입, 지수 연산 등을 수행해 하나의 값을 만든다.
- 연산의 대상을 피연산자(operand)라 한다.



## 1. 산술 연산자

- 피연산자를 대상으로 **수학적 계산**을 수행해 새로운 값을 만든다.
- 산술 연산이 불가능한 경우 NaN을 반환한다.

### 이항 산술 연산자

2개의 피연산자를 산술 연산하여 숫자 값을 만든다.

```javascript
5 + 2; // -> 7
5 - 2; // -> 3
5 * 2; // -> 10
5 / 2; // -> 2.5
5 % 2; // -> 1
```

### 단항 산술 연산자

1개의 피연산자를 산술 연산하여 숫자 값을 만든다.

```javascript
var x = 1;

x++;
console.log(x); // 2

x--;
console.log(x); // 1
```

#### 전위 증가/감소 vs 후위 증가/감소

후위 증가 : x = 5 라는 할당문이 먼저 실행되고 그 이후에 ++가 실행된다.
전위 증가 : 먼저 ++를 실행하고 할당문이 실행된다.

```javascript
var x = 5, result;

result = x++;
console.log(result, x); //5 6

result = ++x;
console.log(result, x) // 7 7

result = x--;
console.log(result, x); // 7 6

result = --x;
console.log(result, x); // 5 5
```

### +단항 연산자 , -단항 연산자

숫자 타입이 아닌 피연산자에 사용하면 피연산자를 숫자 타입으로 변환하여 반환한다.

```javascript
+'10' // -> 10
+true; // -> 1
+false; // -> 0
+'Hello' // -> NaN
```

```javascript
var x;

// 할당문은 표현식인 문이다
console.log(x = 10); //10
```

```javascript
var a,b,c;

//연쇄 할당, 오른쪽에서 왼쪽으로 진행

a = b = c = 0;

console.log(a,b,c); // 0 0 0
```



## 비교 연산자

비교 연산자(comparison operator)는 좌항과 우항의 피연산자를 비교한 다음 그 결과를 불리언 값을 반환한다.
주로 if 문이나 for 문과 같은 제어문의 조건식에서 사용된다.

### 동등/ 일치 비교 연산자

| 비교 연산자 |    의미     |           설명           | 부수 효과 |
| :---------: | :---------: | :----------------------: | :-------: |
|     ==      |  동등 비교  |    x와 y의 값이 같음     |     x     |
|     ===     |  일치 비교  | x와 y의 값과 타입이 같음 |     x     |
|     !=      | 부동등 비교 |    x와 y의 값이 다름     |     x     |
|     !==     | 불일치 비교 | x와 y의 값과 타입이 다름 |     x     |

&#10071; 동등 비교(==) 연산자는 좌항과 우항의 피연산자를 비교할 때 먼저 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교한다.

```javascript
5 == 5; // true
5 == '5'; // true
5 === '5' // false
NaN === NaN; // false 자신과 일치하지 않는 유일한 값이다
isNaN(NaN); // true 숫자가 NaN인지 조사하려면 isNaN을 사용한다.
```

## object.is 메서드

```javascript
-0 === +0; //true
object.is(-0, +0); //false

NaN === NaN; //false
object.is(NaN, NaN); //true
```



## 삼항 조건 연산자

삼항 조건 연산자는 조건식의 평가 결과에 따라 반환할 값을 결정한다.

```pseudocode
조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false 일때 반환할 값
```

```javascript
var x = 2;

var result = x % 2 ? '홀수' : '짝수';
console.log(result); //짝수
```

**삼한 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다**



## 논리 연산자

```javascript
//논리부정(!)
!0;  // true
!'Hello' // false

//논리합(||)
true || true; //true
true || false; //true
false || true; //true
false || false; //false

//논리곱(&&)
true && true; //true
true && false; //false
false && true; //false
false && false; //false

//단축평가
'Cat' && 'Dog'; // Cat이라는 문자열은 true로 암묵적 타입변환이 일어난다
			   // 즉 'Dog'가 표현식 전체의 값을 결정하게 되기 떄문에 'Dog'가 그대로 출력된다

//논리 부정(!)
!true; // false
!false; // true
```

### 논리합 또는 논리곱 연산자 표현식의 평가 결과는 불리언이 아닐 수도 있다. 논리합 또는 논리곱은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.



## typeof 연산자

typeof 연산자는 피연산자의 데이터 타입을 문자열로 반환한다. typeof 연산자는 7가지 문자열 'string', 'number', 'boolean', 'undefined', 'symbol', 'object', 'function' 중 하나를 반환함

```javascript
var foo = nulll
typeof foo === null; //false
foo == null; //true

//값이 null 타입인지 확인할 때는 typeof 연산자 말고 일치 연산자(===)를 사용하자
```



## 쉼표 연산자

```javascript
var x, y, z;

x=1, y=2, z=3; // 3 쉼표 연산자도 표현식인 문으로 값으로 평가되는데 마지막 피연산자의 결과를 반환한다.
```



## 지수 연산자

*ES7*에서 도입된 지수 연산자는 좌항의 피연산자를 밑으로, 우항의 피연산자를 지수로 거듭 제곱하여 숫자 값을 반환한다.

```javascript
2 ** 2; // 4
2 ** 2.5; //5.65685424949238
2 ** 0; // 1
2 ** -2 // 0.25

Math.pow(2, 2.5); //지수 연산자가 도입되기 이전에는 math.pow 메서드를 사용했다

(-5) ** 2; // 25
```

**음수를 거듭제곱의 밑으로 사용하려면 괄호로 묶어야 함**

> 지수 연산자는 이항 연산자 중에서 우선순위가 가장 높다



