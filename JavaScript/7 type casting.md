# 타입 변환(type casting)과 단축 평가



## 타입 변환이란?

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

- 명시적 타입 변환이나 암묵적 타입 변환이 기존 원시 값을 직접 변경하는 것은 아니다. 기존 원시 값을 이용해 다른 타입의 새로운 원시 값을 생성하는 것이다.
- 원시값은 *변경 불가능한 값(immutable value)*이므로 변경할 수 없다는 사실을 다시 한번 알 수 있다.

- 위 예제의 경우 자바스크립트 엔진은 표현식 `x + ''`을 평가하기 위해 x 변수의  숫자값을 바탕으로 새로운 문자열 '10'을 생성하고 이것을 표현식 `'10' + ''`를 평가한다.
- 이 때 암묵적으로 생성된 문자열 `'10'`은 x 변수에 재할당되지 않는다.
- 즉 문자열 '10'은 표현식의 평가가 끝나면 아무도 참조하지 않으므로 가비지 콜렉터에 의해 메모리에서 해제된다.
- **암묵적 타입 변환은 기존 변수 값을 재할당하여 변경하는 것이 아니다. 자바스크립트 엔진은 표현식을 에러 없이 평가하기 위해 피연산자의 값을 암묵적 타입 변환해 새로운 타입의 값을 만들어 단 한 번 사용하고 버린다.**
- 때로는 명시적 타입 변환보다 암묵적 타입 변환이 가독성 측면에서 더 좋을 수도 있기 때문에 명시적 타입 변환만 사용하는것은 옳지 않다.
- `(10).toString()`보다 `10 + ''`이 더욱 간결하다.



## 암묵적 타입 변환

자바스크립트 엔진은 표현식을 평가할 때 개발자의 의도와는 상관없이 코드의 문맥을 고려해 암묵적으로 데이터 타입을 강제 변환할 때가 있다.

```javascript
// 피연산자가 모두 문자열 타입이어야하는 문맥
'10' + 2 // -> '102'

// 피연산자가 모두 숫자 타입이어야 하는 문맥
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
// 숫자 타입
0 + '' // "0"
-0 + '' // "0"
1 + '' // "1"
-1 + '' // "-1"
NaN + '' // "NaN"
Infinity + '' // "Infinity"
-Infinity + '' // "-Infinity"

// 불리언 타입
true + '' // "true"
false + '' // "false"

// null 타입
null + '' // "null"

// undefined 타입
undefined + '' // "undefined"

// 심벌 타입
(Symbol()) + '' // TypeError : Cannot convert a Symbol value to a String

// 객체 타입
({}) + '' // "[object Object]"
Math + '' // "[object Math]"
[] + '' // ""
[10,20] + '' // "10, 20"
(function(){}) + '' // "function(){}"
Array + ''    // function Array() { [native code] }
```



## 숫자 타입으로 변환

```javascript
1 - '1'; // 0
1 * '10'; // 10
1 / 'one'; // NaN
```

- 위 예제에서 사용한 연산자는 모두 산술 연산자이다. 산술 연산자의 역할은 숫자 값을 만드는 것이다.
- 따라서 산술 연산자의 모든 피연산자 코드 문맥 상 모두 숫자 타입이어야 한다.
- **이 때 피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 표현식의 평가 결과는 `NaN`이 된다.**

```javascript
'1' > 0 // true
```

- 비교 연산자의 역할은 불리언 값을 만드는 것이다.
- `>` 비교 연산자는 피연산자의 크기를 비교하므로 모든 피연산자는 코드의 문맥상 숫자여야한다.

```javascript
// 문자열 타입
+'' // 0
+'0' // 0
+'1' // 1
+'string' // NaN

// 불리언 타입
+true // 1
+false // 0

// null 타입
+null // 0

// undefined 타입
+undefined // NaN

// 심벌 타입
+Symbol() // -> ypeError: Cannot convert a Symbol value to a number

// 객체 타입
+{}             // -> NaN
+[]             // -> 0
+[10, 20]       // -> NaN
+(function(){}) // -> NaN

```

**-------주의--------**

- 빈 문자열(‘’), 빈 배열([]), null, false는 0으로, true는 1로 변환된다. 
- 객체와 빈 배열이 아닌 배열, `undefined`는 변환되지 않아 NaN이 된다는 것에 주의하자.



## Boolean 타입으로 변환

<span style=color:red>**아래 값들은 false로 평가되는 Falsy 값이다**</span>

- **false**
- **undefined**
- **null**
- **0, -0**
- **NaN**
- **`"`(빈 문자열)**

<span style=color:red>**`Falsy`값 외의 모든 값은 `true`로 평가되는 `Truthy`값이다.**</span>

```javascript
if ('')    console.log('1');
if (true)  console.log('2');
if (0)     console.log('3');
if ('str') console.log('4');
if (null)  console.log('5');

// 2 4
```

아래의 조건문은 모두 코드 블록을 실행한다.

```javascript
if (!false)     console.log(false + ' is falsy value');
if (!undefined) console.log(undefined + ' is falsy value');
if (!null)      console.log(null + ' is falsy value');
if (!0)         console.log(0 + ' is falsy value');
if (!NaN)       console.log(NaN + ' is falsy value');
if (!'')        console.log('' + ' is falsy value');
```

예시) Truthy / Falsy 값을 판별하는 함수

```javascript
// 전달받은 인수가 Falsy 값이면 true, Truthy 값이면 false를 반환한다.
function isFalsy(v){
    return !v;
}
// 전달받은 인수가 Truthy 값이면 true, Falsy 값이면 false를 반환한다.
function isTruthy(v) {
  return !!v;
}

// 모두 true를 반환한다.
isFalsy(false);
isFalsy(undefined);
isFalsy(null);
isFalsy(0);
isFalsy(NaN);
isFalsy('');

// 모두 true를 반환한다.
isTruthy(true);
isTruthy('0'); // 빈 문자열이 아닌 문자열은 Truthy 값이다.
isTruthy({});
isTruthy([]);
```



## 명시적 변환하는 여러 가지 방법

### 문자열 타입으로 변환

1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메서드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법

```javascript
// 1. String 생성자 함수를 new 연산자 없이 호출하는 방법
// 숫자 타입 => 문자열 타입
String(1); // "1"
String(NaN); // "NaN"
String(Infinity); // "Infinity"
// 불리언 타입 => 문자열 타입
String(true); // 'true'
String(false); // 'false'

// 2. object.prototype.toString 메서드를 사용하는 방법
// 숫자 타입 => 문자열 타입
(1).toString(); // "1"
(NaN).toString(); // "NaN"
(Infinity).toString(); // "Infinity"
// 불리언 타입 => 문자열 타입
(true).toString();     // -> "true"
(false).toString();    // -> "false"

// 3. 문자열 연결 연산자를 이용하는 방법
// 숫자 타입 => 문자열 타입
1 + ''; // "1"
NaN + '';      // -> "NaN"
Infinity + ''; // "Infinity"

// 불리언 타입 => 문자열 타입
true + '';     // -> "true"
false + '';    // -> "false"
```



### 숫자 타입으로 변환

1. `Number` 생성자 함수를 `new`없이 호출
2. `parseInt, parseFloat` 함수를 사용하는 법
3. `+` 단항 산술 연산자를 사용
4. `*`산술 연산자를 이용하는 방법

```javascript
// 1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
Number('0'); // 0
Number('-1');    // -1
Number('10.53') // 10.53
// 불리언 타입 => 숫자 타입
Number(true) // 1
Number(false) // 0

// 2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
// 문자열 타입 => 숫자 타입
parseInt('0'); // 0
parseFloat('10.53') // 10.53

// 3. + 단항 산술 연산자를 이용하는 방법
+'0'; // 0
+'-1'; // -1
+'10.53'; // 10.53
// 불리언 타입 => 숫자 타입
+true; // 1
+false; // 0

// 4. * 산술 연산자를 이용하는 방법
// 문자열 타입 => 숫자 타입
'0' * 1; // 0
'-1' * 1; // -1
'10.53' * 1; // 10.53

// 불리언 타입 => 숫자 타입
true * 1; // 1
false * 1; // 0
```



### 불리언 타입으로 변환

1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
2. ! 부정 논리 연산자를 두 번 사용하는 방법

```javascript
// 1. Boolean 생성자 함수를 new 연산자 없이 호출하는 방법
// 문자열 타입 => 불리언 타입
Boolean('x'); // true
Boolean('false'); // true
Boolean(''); // false
// 숫자 타입 => 불리언 타입
Boolean(0); // false
Boolean(1); // true
Boolean(NaN); // false
Boolean(Infinity); // true
// null 타입 => 불리언 타입
Boolean(null); // false
// undefined 타입 => 불리언 타입
Boolean(undefined); // false
// 객체 타입 => 불리언 타입
Boolean({}); // true
Boolean([]); // true

// 2. ! 부정 논리 연산자를 두번 사용하는 방법
// 문자열 타입 => 불리언 타입
!!'x'; // true
!!''; // false
!!'false'; //true

// 숫자 타입 => 불리언 타입
!!0; // false
!!1; // true
!!NaN; // false
!!Infinity; // true

// null 타입 => 불리언 타입
!!null; // false

// undefined 타입 => 불리언 타입
!!undefined; // false

// 객체 타입 => 불리언 타입
!!{}; // true
!![]; // true

```



## 단축 평가

### 논리 연산자를 사용한 단축 평가

- 논리합(`||`) 연산자와 논리곱(`&&`) 연산자 표현식의 평가 결과는 불리언 값이 아닐 수도 있다.
- 논리합(`||`) 또는 논리곱(`&&`)연산자의 표현식은 언제나 2개의 피연산자 중 어느 한쪽으로 평가된다는 것이다.

```javascript
'Cat' && 'Dog' // "Dog"
```

- 논리곱(`&&`) 연산자는 두 개의 피연산자가 모두 `true`로 평가될 때 `true`를 반환한다. 그리고 논리곱 연산자는 좌항에서 우항으로 평가가 진행된다.
- 첫 번째 피연산자 'Cat'은 `Truthy`값이므로 `true`로 평가된다. 하지만 이 시점까지는 위 표현식을 평가할 수 없다.
- 즉, **논리곱 연산자는 논리 연산의 결과를 결정하는 두 번째 피연산자, 즉 문자열 'Dog'를 그대로 반환한다.**

```javascript
'Cat' || 'Dog' // "Cat"
```

- 논리합 연산자도 논리곱 연산자와 비슷하게 동작한다.
- 첫 번째 피연산자 'Cat'은 `Truthy`값이므로 `true`로 평가된다. 이 시점에 두번째 피연산자까지 평가해보지 않아도 위 표현식을 평가할 수 있다.
- **논리합 연산자는 논리 연산의 결과를 결정한 첫번째 피연산자, 즉  문자열 'Cat'을 그대로 반환한다.**

논리곱 연산자와 논리합 연산자는 이처럼 **논리 연산의 결과를 결정하는 피연산자를 타입 변환하지 않고 그대로 반환한다. 이를 단축 평가(short-circuit evaluation)라 한다. 단축 평가는 표현식을 평가하는 도중에 결과가 확정된 경우 나머지 평가 과정을 생략하는 것을 말한다.**

```javascript
// 논리합(||) 연산자
'Cat' || 'Dog'  // -> "Cat"
false || 'Dog'  // -> "Dog"
'Cat' || false  // -> "Cat"

// 논리곱(&&) 연산자
'Cat' && 'Dog'  // -> "Dog"
false && 'Dog'  // -> false
'Cat' && false  // -> false
```

단축 평가를 사용하면 if 문을 대체할 수 있다.

```javascript
var done = true;
var message = '';

// 주어진 조건이 true 일 때
if(done) message = '완료';

//if 문은 단축 평가로 대체 가능하다.
//done이 true라면 message에 '완료'를 할당
message = done && '완료';
console.log(message); // 완료
```

```javascript
var done = false;
var message = '';

// 주어진 조건이 false 일 때
if(!done) message = '미완료';

message = done || '미완료';
console.log(message); // 미완료
```

삼항 조건 연산자는 `if...else`를 대체할 수 있다.

```javascript
var done = true;
var message = '';

// if...else 문
if (done) message = '완료';
else      message = '미완료';
console.log(message); // 완료

// if...else 문은 삼항 조건 연산자로 대체 가능하다.
message = done ? '완료' : '미완료';
console.log(message); // 완료
```

- 단축 평가가 유용하게 사용되는 때
  1. 객체를 가리키기를 기대하는 변수가 `null`또는 `undefined`이 아닌지 확인하고 프로퍼티를 참조할 때
     * 객체는 키(key) 와 값(value)으로 구성된 프로퍼티(property)들의 집합이다. 만약 객체를 가리키기를 기대하는 변수의 값이 객체가 아니라 `null`또는 `undefined`인 경우 객체의 프로퍼티를 참조하면 타입 에러가 발생한다. 에러가 발생하면 프로그램이 강제 종료된다.

```javascript
var elem = null;
var value = elem.value; // TypeError: Cannot read property 'value' of null
```

이 때 단축 평가를 사용하면 에러를 발생시키지 않는다.

```javascript
var elem = null;
// elem이 null이나 undefined와 같은 Falsy 값이면 elem으로 평가되고
// elem이 Truthy 값이면 elem.value로 평가된다.
var value = elem && elem.value; // -> null
```



2. 함수 매개변수에 기본값을 설정할 때
   - 함수를 호출할 때 인수를 전달하지 않으면 매개변수는 `undefined`를 갖는다. 이 때 단축 평가를 사용하여 매개변수의 기본값을 설정하면 `undefined`로 인해 발생할 수 있는 에러를 방지할 수 있다.

```javascript
// 단축 평가를 사용한 매개변수의 기본값 설정
function getStringLength(str) {
  str = str || '';
  return str.length;
}

getStringLength();     // -> 0
getStringLength('hi'); // -> 2
```



## 옵셔널 체이닝 연산자

ES11에서 도입된 옵셔널 체이닝(optional chainig) 연산자 `?.`는 좌항의 피연산자가 `null`또는 `undefined`인 경우 `undefined`를 반환하고 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.

```javascript
var elem = null;

// elem이 null 또는 undefined이면 undefined를 반환하고, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.
var value = elem?.value;
console.log(value); // undefined
```

옵셔널 체이닝 연산자 `?.`가 도입되기 이전에는 논리 연산자 `&&`를 사용한 단축 평가를 통해 변수가 `null`인지 `undefined`인지 확인했다.

- 논리 연산자 `&&`는 좌항 피연산자가 `false`로 평가되는 `Falsy` 값(`false, undefined, null, 0, -0, NaN, ''`)이면 좌항 피연산자를 그대로 반환한다.
- 하지만 0이나 `''`은 객체로 평가될 때도 있다.

```javascript
var str = '';

var length = str && str.length;

console.log(length); // ''
```

- 하지만 옵셔널 체이닝 연산자 `?.`는 좌항 피연산자가 `false`로 평가되는 `Falsy`값 (`false, undefined, null, 0, -0, NaN,''`)이라도 `null`또는 `undefined`가 아니면 우항의 프로퍼티 참조를 이어간다.

```javascript
var str = '';

// 문자열의 길이(length)를 참조한다. 이때 좌항 피연산자가 false로 평가되는 Falsy 값이라도
// null 또는 undefined가 아니면 우항의 프로퍼티 참조를 이어간다.
var length = str?.length;
console.log(length); // 0
```



## null 병합 연산자

ES11에서 도입된 null 병합(nullish coalescing) 연산자 `??`는 좌항의 피연산자가 `null`또는 `undefined`인 경우 우항의 피연산자를 반환하고 그렇지 않으면 좌항의 피연산자를 반환한다.

```javascript
// 좌항의 피연산자가 null 또는 undefined이면 우항의 피연산자를 반환하고, 그렇지 않으면 좌항의 피연산자를 반환한다.
var foo = null ?? 'default string';
console.log(foo); // "default string"
```

- `null`병합 연산자 `??`는 변수에 기본값을 설정할 때 유용하다.
- `??`가 도입되기 이전에는 논리 연산자 `||`를 사용해 기본값을 설정했다.

```javascript
// Falsy 값인 0이나 ''도 기본값으로서 유효하다면 예기치 않은 동작이 발생할 수 있다.
var foo = '' || 'default string';
console.log(foo); // "default string"
```

- 하지만 null 병합 연산자 `??`는 좌항의 피연산자가 false로 평가되는 Falsy 값(false, undefined, null, 0, -0, NaN, ‘‘)이라도 null 또는 undefined가 아니면 좌항의 피연산자를 그대로 반환한다.

```javascript
// 좌항의 피연산자가 Falsy 값이라도 null 또는 undefined이 아니면 좌항의 피연산자를 반환한다.
var foo = '' ?? 'default string';
console.log(foo); // ""
```

