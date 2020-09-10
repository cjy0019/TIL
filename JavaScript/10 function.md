# 함수

## 함수란?

수학의 함수는 "입력(input)"을 받아 "출력(output)"을 내보내는 일련의 과정을 정의한 것이다.
함수는 자바스크립트의 강력함과 `표현성(*expressiveness*)`의 근간이 된다.

`expressiveness` : 프로그래밍 언어가 표현적이라는 말은 코드만 봐도 어떤 의도인지 쉽게 알 수 있다는 뜻에서 주로 사용한다.

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

- 함수는 `함수 정의`를 통해서 생성되는데 자바스크립트의 함수는 다양한 방법으로 정의할 수 있다.

```javascript
// 함수 정의
function add(x,y){
    return x + y;
}
```

- 위에 함수는 함수 선언문을 통해 선언한 함수이다.



### 함수 호출(function call/invoke)

- 함수 정의만으로는 함수를 실행할 수는 없다.
- 미리 정의된 일련의 과정을 실행하기 위해 필요한 입력, 즉 인수를 매개변수(parameter)를 통해 함수에 전달하면서 함수의 실행을 명시적으로 지시해야 하는데 이것을 **함수 호출**(function call/ invoke)이라 부른다.
- 다음은 함수 호출 예시이다.

```javascript
// 함수 호출
var result = add(2,5);

// 함수 add에 인수 2,5를 전달하면서 호출하면 반환값 7을 반환한다.
console.log(result); // 7
```

<blockquote>호출한다(`call, invoke`)와 실행한다(`execute,run`)는 섞어 써도 된다. 컨텍스트와  언어에 따라 이들 용어 사이에 미묘한 차이가 있을 수 있지만 일반적으로는 같다.</blockquote>



## 함수의 사용 이유

- 함수는 필요할 떄 여러번 호출할 수 있다. 실행 시점을 개발자가 결정할 수 있고 몇 번이든 재사용이 가능하다.

### 코드의 재사용

- 동일한 작업을 반복적으로 수행해야 한다면 같은 코드를 중복해서 여러 번 작성하는 것이 아니라 미리 정의된 함수를 재사용하는 것이 효율적이다.

### 유지보수와 신뢰성

- 같은 코드를 여러번 작성한다면 코드길이가 길어지게 되고 수정해야 할 때 그 양도 늘어나게 된다.
- 또한 '사람'이기 때문에 코드 작성에 있어서 실수할 가능성이 현저히 높아진다.
- **즉, 함수는 유지보수의 편의성을 높이고 실수를 줄여 코드의 신뢰성을 높이는 효과가 있다**.
- 함수는 객체 타입의 값이므로 식별자를 붙일 수 있고, 함수 자신의 역할을 잘 설명해주는 식별자를 붙여야 가독성이 향상된다.



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
- 함수 이름은 생략할 수 있다. 이름 있는 함수는 **기명 함수(named function)**, 이름이 없는 함수를 **익명 함수(anonymous function)**이라 한다.

### 매개변수 목록

- <span style=color:red>0개</span> 이상의 매개 변수를 소괄호로 감싸고 쉼표로 구분한다.
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

- 함수 선언문은 함수 리터럴과 형태가 동일하다. 단, 함수 리터럴을 함수 이름을 생략할 수 있으나 선언문은 그럴 수 없다.

**함수 선언문은 표현식이 아닌 문이다.** 표현식이 아닌 문은 변수에 할당 할 수 없다.
하지만 다음 예제를 보면 함수 선언문이 변수에 할당되는 것처럼 보인다.

```javascript
var add = function add(x,y){
    return x + y;
};

console.log(add(2,5));// 7
```

- 자바스크립트 엔진은 코드의 문맥에 따라 동일한 함수 리터럴을 표현식이 아닌 문인 함수 선언문으로 해석하는 경우와 표현식인 문인 함수 리터럴 표현식으로 해석하는 경우가 있다.
- 함수 선언문은 함수 이름을 생략할 수 없다는 점을 제외하면 함수 리터럴과 형태가 동일하다.
- 예를 들어, `{}`은 블록문일 수도 있고 객체 리터럴일 수도 있다.

<blockquote>기명 함수도 리터럴도 중의적인 코드다. 코드의 문맥에 따라 해석이 달라진다. 자바스크립트 엔진은 함수 이름이 있는 함수 리터럴을 단독으로  사용(값으로 평가되어야 하는 문맥에서 함수 리터럴을 사용하지 않는 경우, 다시 말해 함수 리터럴을 피연산자로 사용하지 않는 경우)하면 **함수 선언문으로 해석하고** 함수 리터럴이 값으로 평가되어야 하는 문맥, 예를 들어 함수 리터럴을 변수에 할당하거나 피연산자로 사용하면 함수 리터럴 표현식으로 해석한다.</blockquote>

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

자바스크립트의 함수는 객체 타입의 값이다. 자바스크립트의 함수는 값처럼 변수에 할당할 수도 있고 프로퍼티 값이 될 수 도 있으며 배열의 요소가 될 수도 있다.

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

- 함수 리터럴은 함수 이름을 생략할 수 있다.
- 익명함수라고 하는데 **함수 표현식의 함수 리터럴은 함수 이름을 생략하는게 일반적이다.**



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

- 모든 선언문이 그렇듯 함수 선언문도 코드가 한 줄씩 순차적으로 실행되는 runtime 이전에 자바스크립트 엔진에 의해 먼저 실행된다. 즉, 코드가 한 줄씩 순차적으로 실행되기 시작하는 런타임에는 이미 함수 객체가 생성되어 있고 함수 이름과 동일한 식별자에 할당까지 완료한다.
- **함수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 것을 함수 호이스팅(function hoisting)이라 한다**



### 함수 호이스팅 vs 변수 호이스팅

- var 키워드를 사용한 변수 선언문과 함수 선언문은 런타임 이전에 자바스크립트 엔진에 의해 먼저 실행되어 식별자를 생성한다는 점에서 동일하다.

- 하지만 var 키워드로 선언된 변수는 undefined로 초기화되고, 함수 선언문을 통해 암묵적으로 생성된 식별자는 함수 객체로 초기화된다.

- 변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현식의 함수 리터럴도 할당문이 실행되는 시점에 평가되어 함수 객체가 된다.
- 따라서 **함수 표현식으로 함수를 정의하면 함수 호이스팅이 아니라 변수 호이스팅이 발생한다**

![img](https://poiemaweb.com/assets/fs-images/12-8.png)

<blockquote>함수 호이스팅은 함수를 호출하기 전에 반드시 함수를 선언해야 한다는 당연한 규칙을 무시한다. 이 같은 문제 때문에 함수 선언문 대신 함수 표현식을 사용할 것을 권장한다. <i>- Douglas Crockford -</i> </blockquote>



## Function 생성자 함수

자바스크립트가 기본 제공하는 빌트인 함수 Function 생성자 함수에 매개변수 목록과 함수 몸체를 문자열로 전달하면서 new 연산자와 함께 호출하면 함수 객체를 생성해서 반환한다.

```javascript
var add = new Function('x','y','return x + y');

console.log(add(2,5)); // 7
```

- Function 생성자 함수로 생성한 함수는 클로저(closure)를 생성하지 않는 등, 함수 선언 문이나 함수 표현식으로 생성한 함수와 다르게 동작한다.
- 일반적이지 않은 방식이고, <i>클로저를 생성하지 않는 등, 함수 선언문이나 함수 표현식으로 생성한 함수와 다르게 동작한다.</i>



## 화살표 함수

ES6에서 새롭게 도입된 화살표 함수(arrow function)는 function 키워드 대신 화살표 (=>,fat arrow)를 사용해 좀 더 간략하게 사용할 수 있고 **화살표 함수는 항상 익명 함수로 정의한다**.

```javascript
const add = (x,y) => x +y;
console.log(add(2,5)); // 7
```

화살표 함수는 생성자 함수로 사용할 수 없으며 기존의 함수와 this 바인딩 방식이 다르고, prototype 프로퍼티가 없으며 arguments 객체를 생성하지 않는다.



## 매개변수와 인수

함수를 실행하기 위해 필요한 값을 함수 외부에서 함수 내부로 전달할 필요가 있는 경우, 매개변수(parameter, 인자)를 통해 인수(arguments)를 전달한다.
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
    console.log(x,y); //2 5
    return x + y;
}

add(2, 5);

//add 함수의 매개변수 x,y 는 함수 몸체 내부에서만 참조할 수 있음.
console.log(x,y); // ReferenceError: x is not defined
```

- 함수는 매개변수의 개수와 인수의 개수가 일치하는지 체크하지 않는다.
- **인수가 부족해서 인수가 할당되지 않은 매개변수의 값은 `Undefined`이다.

```javascript
function add(x,y){
    return x + y;
}

console.log(add(2)); // NaN
```

- 위 예제의 `parameter`에는 `argument`에는 인수 2가 전달되지만 매개변수 y에는 전달할 인수가 없다.
- 따라서 매개변수 y는 `undefined`로 초기화된 상태 그대로다.
- `x+y`는 `2+undefined`와 같으므로 `NaN`이 반환된다.

```javascript
function add(x,y){
    return x+y;
}
console.log(add(2,5,10)); // 7
```

- 초과된 인수는 그냥 버려지지 않고 암묵적으로 `arguments 객체`의 프로퍼티로 보관된다.



## 인수 확인

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

- `타입스크립트(TypeScript)`와 같은 정적 타입을 선언할 수 있는 자바스크립트의 상위 확장을 도입해서 컴파일 시점에 부적절한 호출을 방지할 수 있게 하는 것도 하나의 방법이다.



```javascript
function add(a=0, b=0, c=0){
    return a+b+c;
}

console.log(add(1,2,3)); //6
console.log(add(1,2)); // 3
console.log(add(1)); // 1
console.log(add()); // 0
```

- `ES6`에서 도입된 매개변수 기본 값을 사용하면 함수 내에서 수행하던 인수 체크 및 초기화를 간소화할 수 있다.
- 단 매개변수 기본 값은 매개변수에 인수를 전달하지 않았을 경우와 `undefined`를 전달한 경우에만 유효하다.





## 반환문

- 함수는 return 키워드와 표현식으로 이뤄진  반환문을 이용해 실행 결과를 함수 외부로 반환할 수 있다.

```javascript
function multiply(x,y){
    return x * y; // 반환문
}

var result = multiply(3,5);
console.log(result); // 15
```



#### 반환 값

- 함수 호출도 표현식이고, 우리가 이미 알고 있듯 표현식은 값이 된다.
- 함수 호출의 값은 바로 **반환 값이다.**
- 함수 바디 안에 `return`키워드를 사용하면 함수를 *즉시 종료하고 값을 반환한다.*
- `return`을 명시적으로 호출하지 않으면 반환 값은 `undefined`가 된다.

함수는`return` 키워드와 표현식으로 이뤄진 반환문을 사용해 실행 결과를 함수 외부로 반환할 수 있다.



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



- **반환문은 생략할 수 있다. 이때 함수는 함수 몸체의 마지막 문까지 실행한 후 암묵적으로 undefined를 반환한다.**
- 반환문은 함수 몸체 내부에서만 사용할 수 있다.

```javascript
function foo(){
    // 반환문을 생략하면 암묵적으로 undefined 반환된다.
}

console.log(foo());
```



## 참조에 의한 전달과 외부 상태의 변경

