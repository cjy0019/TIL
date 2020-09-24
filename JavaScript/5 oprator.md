

# 연산자(operator)

- 연산자(operator)는 하나 이상의 <u>표현식</u>을 대상으로 산술, 할당, 비교, 논리, 타입, 지수 연산 등을 수행해 하나의 값을 만든다.
- 연산의 대상을 피연산자(operand)라 한다. 피연산자는 값으로 평가될 수 있는 표현식이어야 한다.

```javascript
// 산술 연산자
5 * 4 // 20

// 문자열 연결 연산자 
'My name is ' + 'Lee' // My name is Lee

// 할당 연산자
color = 'red' // 'red'

// 비교 연산자
3 > 5 // false

// 논리 연산자
true && false // false

// 타입 연산자
typeof 'Hi' // 'string'
```

- 피연산자가 '값'이라는 명사의 역할을 한다면 연산자는 '피연산자를 연산하여 새로운 값을 만든다'라는 동사의 역할을 한다고 볼 수 있다.
- 다시 말해, 피연산자는 연산의 대상이 되어야 하므로 값으로 평가할 수 있어야 한다.



## 1. 산술 연산자(arithmetic operator)

- 피연산자를 대상으로 **수학적 계산**을 수행해 새로운 값을 만든다.
- 산술 연산이 불가능한 경우 NaN을 반환한다.



### 이항(binary) 산술 연산자

2개의 피연산자를 산술 연산하여 숫자 값을 만든다. 모든 이항 산술 연산자는 피연산자의 값을 변경하는 부수 효과(side effect)가 없다. 다시 말해, 어떤 산술 연산자를 연산해도 피연산자의 값이 바뀌는 경우는 없고 언제나 새로운 값을 만든다.

```javascript
5 + 2; // -> 7
5 - 2; // -> 3
5 * 2; // -> 10
5 / 2; // -> 2.5
5 % 2; // -> 1
```



### 단항(unary) 산술 연산자

1개의 피연산자를 산술 연산하여 숫자 값을 만든다. 주의할 점은 이항 산술 연산자와는 달리 **증가/감소(++/--) 연산자는 피연산자의 값을 변경하는 부수 효과가 있다는 것이다**. 다시 말해, 증가/감소 연산을 하면 피연산자의 값을 변경하는 암묵적 할당이 이뤄진다.

```javascript
var x = 1;

x++;
console.log(x); // 2

x--;
console.log(x); // 1
```



#### 전위 증가/감소 vs 후위 증가/감소

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

후위 증가 : x = 5 라는 할당문이 먼저 실행되고 그 이후에 ++가 실행된다.
전위 증가 : 먼저 ++를 실행하고 할당문이 실행된다.



### +단항 연산자 , -단항 연산자

`+`단항 연산자는 피연산자에 어떠한 효과도 없다. 음수를 양수로 반전하지도 않는다.

```javascript
+10; // 10

+(-10) // -10
```

그러나 숫자 타입이 아닌 피연산자에 `+`단항 연산자를 사용하면 피연산자를 숫자타입으로 변환하여 반환한다. 이 때 피연산자를 변경하는 것은 아니고 숫자 타입으로 변환한 값을 생성해서 반환한다.

```javascript
+'10' // -> 10
+true; // -> 1
+false; // -> 0
+'Hello' // -> NaN
```

```javascript
var x = '1';

// 문자열을 숫자로 타입 변환한다.
console.log(+x); // 1
// 부수효과는 없다.
console.log(x); // "1"

// 불리언 값을 숫자로 타입 변환한다.
x = true;
console.log(+x); // 1
// 부수 효과는 없다.
console.log(x); // true

// 문자열을 숫자로 타입 변환할 수 없으므로 NaN을 반환한다.
x = 'Hello';
console.log(+x); // NaN
// 부수 효과는 없다.
console.log(x); // "Hello"
```

- `-`단항 연산자는 피연산자의 부호를 반전한 값을 반환한다. 
- `+`단항 연산자와 마찬가지로 숫자 타입이 아닌 피연산자에 사용하면 피연산자를 숫자 타입으로 변환하여 반환한다.
- 이 때 피연산자를 변경하는 것은 아니고 부호를 반전한 값을 생성해 반환한다. 따라서 부수 효과는 없다.

```javascript
// 부호를 반전한다.
console.log(-(-10)); // 10

// 문자열을 숫자로 타입 변환한다.
console.log(-"10"); // -10

// 불리언 값을 숫자로 타입 변환한다.
console.log(-true); // -1

// 문자열은 숫자로 타입 변환할 수 없으므로 NaN을 반환한다.
console.log(-"Hello"); // NaN

```



### 문자열 연결 연산자

- **`+` 연산자는 피연산자 중 하나 이상이 문자열인 경우 문자열 연결 연산자로 동작한다.**
- 그 외의 경우에는 산술 연산자로 동작한다.

```javascript
// 문자열 연결 연산자
console.log("1" + 2); // 12
console.log(1 + "2"); // 12

// 산술 연산자
console.log(1 + 2); // 3

// true는 1로 타입 변환된다.
console.log(1 + true); // 2

// false는 0으로 타입 변환된다.
console.log(1 + false); // 1

// null은 0으로 타입 변환된다.
console.log(1 + null); // 1

// undefined는 숫자로 변환되지 않는다.
console.log(+undefined); // NaN
console.log(1 + undefined); // NaN

```

**----- 주의할 점------**

- 개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다는 것이다.
- `1+true`를 연산하여 자바스크립트 엔진은 암묵적으로 불리언 타입의 값인 `true`를 숫자 타입인 1로 강제 변환한 후 연산을 수행한다.
- 이를 **암묵적 타입 변환(implicit coercion)** 또는 **타입 강제 변환(type coercion)**이라고 한다.



## 할당 연산자

할당 연산자(assignment operator)는 우항에 있는 피연산자의 평가 결과를 좌항에 있는 변수에 할당한다.

할당 연산자는 좌항의 변수에 값을 할당하므로 변수 값이 변하는 부수 효과가 있다.

```javascript
var x;

x = 10;
console.log(x); // 10

x += 5;
console.log(x); // 15

x -= 5;
console.log(x); // 10

x *= 5;
console.log(x); // 50

x /= 5;
console.log(x); // 10

x %= 5;
console.log(x); // 0

var str = "My name is ";

str += "Lee";
console.log(str);

```

```javascript
var x;

// 할당문은 표현식인 문이다.
console.log(x = 10); // 10
```

- 할당문은 변수에 값을 할당하는 부수 효과만 있을 뿐 값으로 평가되지 않을 것처럼 보인다.
- 하지만 **할당문은 값으로 평가되는 표현식인 문으로서 할당된 값으로 평가된다.**위 예제의 할당문 `x=10`은 x에 할당된 숫자 값 10으로 평가된다.

```javascript
var a,b,c;

// 연쇄 할당. 오른쪽에서 왼쪽으로 진행
// 1. c = 0 : 0 으로 평가된다.
// 2. b = 0 : 0 으로 평가된다.
// 3. a = 0 : 0 으로 평가된다.
a = b = c = 0;

console.log(a,b,c); // 0 0 0
```



## 비교 연산자

비교 연산자(comparison operator)는 좌항과 우항의 피연산자를 비교한 다음 그 결과를 <u>불리언 값을 반환한다.</u>
주로 `if` 문이나 `for` 문과 같은 제어문의 조건식에서 사용된다.



### 동등(loose equality) / 일치 비교 연산자(strict equality)

| 비교 연산자 |    의미     |           설명           | 부수 효과 |
| :---------: | :---------: | :----------------------: | :-------: |
|     ==      |  동등 비교  |    x와 y의 값이 같음     |     x     |
|     ===     |  일치 비교  | x와 y의 값과 타입이 같음 |     x     |
|     !=      | 부동등 비교 |    x와 y의 값이 다름     |     x     |
|     !==     | 불일치 비교 | x와 y의 값과 타입이 다름 |     x     |

&#10071; **동등 비교(==) 연산자는 좌항과 우항의 피연산자를 비교할 때 먼저 암묵적 타입 변환을 통해 타입을 일치시킨 후, 같은 값인지 비교한다.**

```javascript
// 동등 비교
5 == 5; // true
// 타입은 다르지만 암묵적 타입 변환을 통해 타입을 일치시키면 동등하다.
5 == '5'; // true


5 === '5' // false
NaN === NaN; // false 자신과 일치하지 않는 유일한 값이다
isNaN(NaN); // true 숫자가 NaN인지 조사하려면 isNaN을 사용한다.
```

- 동등 비교(==) 연산자는 예측하기 어려운 결과를 만들어내기 때문에 동등 비교 연산자는 사용하지 않는 편이 좋다. 대신 `일치 비교(===)`연산자를 사용한다.
- **일치 비교(`===`) 연산자는 좌항과 우항의 피연산자가 타입도 같고 값도 같은 경우에 한하여 `true`를 반환한다.**

```javascript
// 일치 비교
5 === 5; // true

// 암묵적 타입 변환을 하지 않고 값을 비교한다.
// 즉, 값과 타입이 모두 같은 경우만 true를 반환한다.
5 === '5'; // false

// -----------------주의--------------------
// NaN은 자신과 일치하지 않는 유일한 값이다.
NaN === NaN; // false
```



## isNaN 함수

`NaN`은 일치 비교 연산자로 확인할 수 없기 때문에 빌트인 함수 `isNaN`을 사용한다.

```javascript
// isNaN 함수는 지정한 값이 NaN인지 확인하고 그 결과를 불리언 값으로 반환한다.
isNaN(NaN); // -> true
isNaN(10);  // -> false
isNaN(1 + undefined); // -> true
```

0도 주의해야 한다.

```javascript
// 양의 0과 음의 0의 비교. 일치 비교/동등 비교 모두 결과는 true이다.
0 === -0; // -> true
0 == -0;  // -> true
```



## Object.is 메서드

- `+0`과 `-0`을 동일하다고 평가한다.
- ES6에서 도입된 `Object.is`메서드는 다음과 같이 예측 가능한 정확한 비교를 반환한다.

```javascript
-0 === +0; // true
console.log(Object.is(-0, +0)); // false

NaN === NaN; // false
console.log(Object.is(NaN, NaN)); // true

```

### 대소 관계 비교 연산자

대소 관계 비교 연산자는 피연산자의 크기를 비교하여 불리언 값을 반환한다.

```javascript
// 대소 관계 비교
5 > 0; // true
5 > 5; // false
5 >= 5; // true
5 <= 5; // true
```



## 삼항 조건 연산자

삼항 조건 연산자(tenary operator)는 조건식의 평가 결과에 따라 반환할 값을 결정한다.

```pseudocode
조건식 ? 조건식이 true일 때 반환할 값 : 조건식이 false 일때 반환할 값
```

- 삼항 조건 연산자는 첫 번째 피연산자가 `true`로 평가되면 두 번째 피연산자를 반환하고, 첫 번째 피연산자가 `false`로 평가되면 세 번째 피연산자를 반환한다.
- 물음표(?) 앞의 첫 번째 피연산자는 조건식, 즉 불리언 타입의 값으로 평가될 표현식이다. 만약 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 암묵적으로 타입 변환된다.

```javascript
var x = 2;

// 2 % 2는 0이고 0은 false로 암묵적 타입 변환된다.
var result = x % 2 ? '홀수' : '짝수';
console.log(result); //짝수
```

**삼항 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다**

삼항 조건 연산자 표현식은 `if...else`문으로 대체할 수 있지만 차이가 있다. 삼항 조건 연산자 표현식은 값처럼 사용할 수 있지만 `if...else`문은 값처럼 사용할 수 없다.

즉 `if...else`문은 표현식이 아닌 문이다.

```javascript
var x = 10;

var result = if(x%2){result = '홀수';} else {result = '짝수';};
// SyntaxError: Unexpected token if
```

**삼항 조건 연산자 표현식은 값으로 평가할 수 있는 표현식인 문이다.**

```javascript
var x = 10;

var result = x % 2 ? '홀수' : '짝수';
console.log(result); // 짝수
```



## 논리 연산자

```javascript
//논리부정(!)
// 암묵적 타입 변환

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

//논리 부정(!)
!true; // false
!false; // true
```

### 논리합 또는 논리곱 연산자 표현식의 평가 결과는 불리언이 아닐 수도 있다. 논리합 또는 논리곱은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다.

```javascript
//단축평가
'Cat' && 'Dog'; 

// Cat이라는 문자열은 true로 암묵적 타입변환이 일어난다
// 즉 'Dog'가 표현식 전체의 값을 결정하게 되기 떄문에 'Dog'가 그대로 출력된다
```



## typeof 연산자

typeof 연산자는 피연산자의 데이터 타입을 문자열로 반환한다. typeof 연산자는 7가지 문자열 `'string', 'number', 'boolean', 'undefined', 'symbol', 'object', 'function'` 중 하나를 반환함

```javascript
typeof ''              // -> "string"
typeof 1               // -> "number"
typeof NaN             // -> "number"
typeof true            // -> "boolean"
typeof undefined       // -> "undefined"
typeof Symbol()        // -> "symbol"
typeof null            // -> "object"
typeof []              // -> "object"
typeof {}              // -> "object"
typeof new Date()      // -> "object"
typeof /test/gi        // -> "object"
typeof function () {}  // ->"function"
```

```javascript
var foo = null

typeof foo === null; //false
foo == null; //true

//값이 null 타입인지 확인할 때는 typeof 연산자 말고 일치 연산자(===)를 사용하자
```

**------------주의-------------**

선언하지 않은 식별자를 `typeof`연산자로 연산해 보면 `ReferenceError`가 발생하지 않고 `undefined`를 반환한다.

```javascript
// undeclared 식별자를 선언한 적이 없다.
typeof undeclared; // -> undefined
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
