# 함수

## 함수란?

수학의 함수는 "입력(input)"을 받아 "출력(output)"을 내보내는 일련의 과정을 정의한 것이다.

<img src="https://poiemaweb.com/assets/fs-images/12-1.png" alt="img" style="zoom: 33%;" />

**프로그래밍 언어의 함수도 수학의 함수와 같은 개념이다. 함수 f(x,y) = x + y 를 자바스크립트의 함수로 표현하면,**

```javascript
// f(x,y) = x + y
function add(x,y){
    return x + y;
}

add(2,5); // 7
```

프로그래밍 언어의 함수는 **일련의 과정을 문(statement)으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정리한 것이다.**

- 이때 함수 내부로 입력을 전달 받는 변수를 **매개변수(parameter)**
- 입력은 **인수(argument)**
- 출력은 **반환 값(return value)**

<img src="https://poiemaweb.com/assets/fs-images/12-2.png" alt="img" style="zoom:50%;" />

### 함수 정의(function definition)

```javascript
// 함수 정의
function add(x,y){
    return x + y;
}
```

- 위에 함수는 함수 선언문을 통해 선언한 함수이다.

### 함수 호출(function call/invoke)

- 인수를 매개변수를 통해 함수에 전달하면서 함수의 실행을 명시적으로 지시해야 하는데 이것을 **함수 호출**이라 부른다.
- 다음은 함수 호출 예시이다.

```javascript
// 함수 호출
var result = add(2,5);

// 함수 add에 인수 2,5를 전달하면서 호출하면 반환값 7을 반환한다.
console.log(result); // 7
```



## 함수의 사용 이유

### 코드의 재사용

- 동일한 작업을 반복적으로 수행해야 한다면 같은 코드를 중복해서 여러 번 작성하는 것이 아니라 미리 정의된 함수를 재사용하는 것이 효율적이다.

### 유지보수와 신뢰성

- 같은 코드를 여러 번 작성하면 그 코드를 수정해야 할 때 중복된 횟수만큼 코드를 수정해야 한다.
- 또한 실수할 가능성 또한 높아진다.
- **함수는 유지보수의 편의성을 높이고 실수를 줄여 코드의 신뢰성을 높이는 효과가 있다**



## 함수 리터럴

자바스크립트의 함수는 객체 타입의 값이다. 따라서 숫자, 객체 리터럴처럼 함수도 **함수 리터럴로 생성할 수 있다**

- 함수 리터럴은 function 키워드, 함수 이름, 매개변수 목록, 함수 몸체로 구성된다.

```javascript
// 변수에 함수 리터럴을 할당
var f = function add(x,y){
    return x + y;
};
```

### 함수 이름

- 함수 이름은 식별자다. 따라서 식별자 네이밍 규칙을 준수해야 한다.
- 함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자이다.
- 함수 이름은 생략할 수 있다. 이름 있는 함수는 **기명 함수(named function)**, 이름이 없는 함수를 **익명함수(anonymous function)**이라 한다.

### 매개변수 목록

- 0개 이상의 매개 변수를 소괄호로 감싸고 쉼표로 구분한다.
- 각 매개 변수에는 함수를 호출할 떄 지정한 인수가 순서대로 할당된다.
- 매개 변수는 함수 몸체 내에서 변수와 동일하게 취급된다.

### 함수 몸체

- 함수가 호출되었을 때 일괄적으로 실행될 문들을 하나의 실행 단위로 정의한 코드 블록이다.
- 함수 몸체는 호출에 의해 실행된다.



## 함수 정의

함수를 정의하는 방법에는 4가지가 있다.

- ### 함수 선언문(function declaration/ function statement)

```javascript
function add(x , y){
    return x + y;
}
```

- ### 함수 표현식(function expression)

```javascript
var add = function(x,y){
    return x + y;
};
```

- ### Function 생성자 함수(Function constructor)

```javascript
var add = new Function('x', 'y', 'return x + y');
```

- ### 화살표 함수(arrow function): ES6

```javascript
var add = (x,y) => x + y;
```

### 선언 vs 정의

변수는 '선언' 한다고 하지만 함수는 '정의' 한다고 한다.
**함수 선언문이 평가되면 식별자가 암묵적으로 생성되고 함수 객체가 할당된다** 따라서 ECMAScript 사양에서도 변수에는 선언, 함수에는 정의(function definition)라고 표현한다.



## 함수 선언문

```javascript
// 함수 선언문은 함수 이름을 생략할 수 없다.
function (x,y){
    return x + y;
}
// SyntaxError : Function statements require a function name
```

**함수 선언문은 표현식이 아닌 문이다.** 표현식이 아닌 문은 변수에 할당 할 수 었다.
하지만 다음 예제를 보면 함수 선언문이 변수에 할당되는 것처럼 보인다.

```javascript
var add = function add(x,y){
    return x + y;
};

console.log(add(2,5));// 7
```

- 자바스크립트 엔진은 코드의 문맥에 따라 동일한 함수 리터럴을 표현식이 아닌 문인 함수 선언문으로 해석하는 경우와 표현식인 문인 함수 리터럴 표현식으로 해석하는 경우가 있다.

```javascript
// 기명 함수 리터럴을 단독으로 사용하면 함수 선언문으로 해석된다.
function foo(){ console.log('foo'); }
foo(); //foo

// 함수 리터럴에는 함수 이름을 생략할 수 있다.
(function bar(){ console.log('bar'); });
bar(); // ReferenceError: bar is not defined
```

**함수는 함수 이름으로 호출하는 것이 아니라 함수 객체를 가리키는 식별자로 호출한다.**
즉, 함수 선언문으로 생성한 함수를 호출하는 것은 함수 이름이 아니라 자바스크립트 엔진이 암묵적으로 생성한 식별자 add인 것이다.

<img src="https://poiemaweb.com/assets/fs-images/12-7.png" alt="img" style="zoom:50%;" />

## 함수 표현식

자바스크립트의 함수는 객체 타입의 값이다. 자바스크립트의 함수는 값처럼 변수에 할당할 수도 있고 프로퍼티 값이 될 수 도 있으며 배열의 요소가 될 수도있다.

- 이처럼 값의 성질을 갖는 객체를 **일급 객체(first-class object)**라 한다.
- 일급 객체라는 것은 함수를 값처럼 자유롭게 사용할 수 있다는 의미이다.

```javascript
// 함수 표현식
var add = function foo (x,y){
    return x + y;
};

// 함수 객체를 가리키는 식별자로 호출
console.log(add(2,5)); // 7

// 함수 이름으로 호출하면 ReferenceError가 발생한다.
console.log(foo(2,5)); // ReferenceError : foo is not defined



```



## 함수 생성 시점과 함수 호이스팅

```javascript
// 함수 참조
console.dir(add); // ƒ add(x, y)
console.dir(sub); // undefined

// 함수 호출
console.log(add(2, 5)); // 7
console.log(sub(2, 5)); // TypeError: sub is not a function

// 함수 선언문
function add(x, y) {
  return x + y;
}

// 함수 표현식
var sub = function (x, y) {
  return x - y;
};
```

**함수 선언문으로 정의한 함수와 함수 표현식으로 정의한 함수의 생성 시점이 다르다**

모든 선언문이 그렇듯 함수 선언문도 코드가 한 줄씩 순차적으로 실행되는 runtime 이전에 자바스크립트 엔진에 의해 먼저 실행된다. 즉, 코드가 한 줄씩 순차적으로 실행되기 시작하는 런타임에는 이미 함수 객체가 생성되어 있고 함수 이름과 동일한 식별자에 할당까지 완료한다.
**함수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 것을 함수 호이스팅(function hoisting)이라 한다**



### 함수 호이스팅 vs 변수 호이스팅

- var 키워드를 사용한 변수 선언문과 함수 선언문은 런타임 이전에 자바스크립트 엔진에 의해 먼저 실행되어 식별자를 생성한다는 점에서 동일하다.

- 하지만 var 키워드로 선언된 변수는 undefined로 초기화되고, 함수 선언문을 통해 암묵적으로 생성된 식별자는 함수 객체로 초기화된다.

- 변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현식의 함수 리터럴도 할당문이 실행되는 시점에 평가되어 함수 객체가 된다.
- 따라서 **함수 표현식으로 함수를 정의하면 함수 호이스팅이 아니라 변수 호이스팅이 발생한다**

![img](https://poiemaweb.com/assets/fs-images/12-8.png)



## Function 생성자 함수

자바스크립트가 기본 제공하느 빌트인 함수 Function 생성자 함수에 매개변수 목록과 함수 몸체를 문자열로 전달하면서 new 연산자와 함께 호출하면 함수 객체를 생성해서 반환한다.

```javascript
var add = new Function('x','y','return x + y');

console.log(add(2,5)); // 7
```

- Function 생성자 함수로 생성한 함수는 클로저(closure)를 생성하지 않는 등, 함수 선언 문이나 함수 표현식으로 생성한 함수와 다르게 동작한다.



## 화살표 함수

ES6에서 새롭게 도입된 화살표 함수(arrow function)는 function 키워드 대신 화살표 (=>,fat arrow)를 사용해 좀 더 간략하게 사용할 수 있고 **화살표 함수는 항상 익명 함수로 정의한다**.

```javascript
const add = (x,y) => x +y;
console.log(add(2,5)); // 7
```

화살표 함수는 생성자 함수로 사용할 수 없으며 기존의 함수와 this 바인딩 방식이 다르고, prototype 프로퍼티가 없으며 arguments 객체를 생성하지 않는다.



## 매개변수와 인수

함수 내부에서는 매개변수(parameter, 인자)를 통해 인수(arguments)를 전달한다.
인수는 값으로 평가될 수 있는 표현식이어야 한다.

```javascript
function add(x,y){
    return x + y;
}

// 함수 호출
// 인수 1과 2는 매개변수 x와 y에 순서대로 할당되고 함수 몸체의 문들이 실행된다.

var result = add(1,2);
```

<img src="https://poiemaweb.com/assets/fs-images/12-9.png" alt="img" style="zoom:50%;" />

```javascript
function add(x,y){
    return x + y;
}

console.log(add(2,5,10)); // 7

function add(x, y) {
  console.log(arguments);
  // Arguments(3) [2, 5, 10, callee: ƒ, Symbol(Symbol.iterator): ƒ]

  return x + y;
}

add(2, 5, 10);
```

초과된 인수는 버려지는 것처럼 보이지만 암묵적으로 arguments 객체의 프로퍼티로 보관된다.



## 인수확인

- 자바스크립트 함수는 매개변수와 인수의 개수가 일치하는지 확인하지 않는다.
- 자바스크립트는 동적 타입 언어다. 따라서 자바스크립트 함수는 매개변수 타입을 사전에 지정할 수 없다.

```javascript
function add(x, y) {
  if (typeof x !== 'number' || typeof y !== 'number') {
    // 매개변수를 통해 전달된 인수의 타입이 부적절한 경우 에러를 발생시킨다.
    throw new TypeError('인수는 모두 숫자 값이어야 합니다.');
  }

  return x + y;
}

console.log(add(2));        // TypeError: 인수는 모두 숫자 값이어야 합니다.
console.log(add('a', 'b')); // TypeError: 인수는 모두 숫자 값이어야 합니다.
```



## 반환문

함수는 return 키워드와 표현식으로 이뤄진 반환문을 사용해 실행 결과를 함수 외부로 반환할 수 있다.

```javascript
function multiply(x,y){
    return x * y; // 반환문
}
```

- 반환문은 함수의 실행을 중단하고 함수 몸체를 빠져나간다. 반환문 이후에 다른 문이 존재하면 그 문은 실행되지 않는다.
- 반환문은 return 키워드 뒤에 오는 표현식을 평가해 반환한다. 명시하지 않는다면 undefined가 반환된다.

```javascript
function multiply(x, y){
    return x * y;
    // 반환문 이후에 다른 문이 존재하며 그 문은 실행되지 않고 무시된다.
    console.log('실행되지 않는다.');
}
console.log(multiply(3,5)); // 15
```

```javascript
function foo(){
    return;
}

console.log(foo()); // undefined
```



## 참조에 의한 전달과 외부 상태의 변경
