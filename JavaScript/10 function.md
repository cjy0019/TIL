# 함수

함수는 자바스크립트에서 가장 중요한 핵심 개념이다. 또 다른 자바스크립트의 핵심 개념인 스코프, 실행 컨텍스트, 클로저, 생성자 함수에 의한 객체 생성, 메서드, this 프로토타입, 모듈화 등이 모두 함수와 관련이 깊기 때문이다.

함수는 자바스크립트의 강력함과 **표현성(expressiveness)**의 근간이 된다. 

**expressiveness** : 프로그래밍 언어가 표현적이라는 말은 코드만 봐도 어떤 의도인지 쉽게 알 수 있다는 뜻에서 주로 사용한다.

## 함수란?

수학의 함수는 "입력(input)"을 받아 "출력(output)"을 내보내는 일련의 과정을 정의한 것이다. 예를 들면 `f(x,y) = x + y`라는 함수를 정의하고 이 함수에 두 개의 입력 2,5를 전달하면 함수는 정의된 일련의 과정을 거쳐 7을 출력한다.





미리 정의해 둔 함수를 실행하는 것을 수식으로 표현하면 f(2, 5) = 7이다. 이때 함수의 x, y는 함수 내부로 입력을 받아들이는 변수(아직 결정되지 않은 임의의 값을 나타내는 기호)이고 2, 5는 함수에서 정의된 일련의 과정을 실행하기 위해 필요한 입력이며, 7은 함수의 실행 결과인 출력이다.

이때 함수를 실행하기 위해 필요한 입력인 2, 5는 입력을 받아 들이는 변수 x, y를 통해 함수 외부에서 함수 내부로 전달된다. 그리고 함수의 실행 결과인 출력은 함수 외부로 반환된다.

**프로그래밍 언어의 함수도 수학의 함수와 같은 개념이다. 함수 f(x,y) = x + y 를 자바스크립트의 함수로 표현하면,**

```javascript
// f(x,y) = x + y
function add(x, y) {
  return x + y;
}

// f(2,5) = 7
console.log(add(2, 5)); // 7
```

프로그래밍 언어의 함수는 **일련의 과정을 문(statement)으로 구현하고 코드 블록으로 감싸서 하나의 실행 단위로 정리한 것이다.**

프로그래밍 언어의 함수도 입력을 받아서 출력을 내보낸다. 

- 이때 함수 내부로 입력을 전달 받는 변수를 **매개변수(parameter)**
- 입력을 **인수(argument)**
- 출력을 **반환값(return value)**
- 또한 함수는 값이고 여러 개 존재할 수 있기 때문에 특정 함수를 구별하기 위해 식별자인 함수 이름을 사용한다.





### 함수 정의(function definition)

- 함수는 **함수 정의(function definition)**를 통해서 생성되는데 자바스크립트의 함수는 다양한 방법으로 정의할 수 있다.

```javascript
// 함수 정의
function add(x,y){
    return x + y;
}
```

- 위의 예시는 **함수 선언문**을 통해 선언한 함수이다.



### 함수 호출(function call/invoke)

- 함수 정의만으로는 함수를 실행할 수는 없다.
- 수학의 함수처럼 미리 정의된 일련의 과정을 실행하기 위해 필요한 입력, 즉 인수(argument)를 매개 변수를 통해 함수에 전달하면서 함수의 실행을 명시적으로 지시해야 한다. 이를 **함수 호출(function call/invoke)**이라 한다.
- 함수 호출을 하면 코드 블록에 담긴 문들이 일괄적으로 실행되고, 실행 결과, 즉 반환값을 반환한다.
- 다음은 함수 호출 예시이다.

```javascript
// 함수 호출
var result = add(2,5);

// 함수 add에 인수 2,5를 전달하면서 호출하면 반환값 7을 반환한다.
console.log(result); // 7
```

<blockquote>호출한다(`call, invoke`)와 실행한다(`execute, run`)는 섞어 써도 된다. 컨텍스트와  언어에 따라 이들 용어 사이에 미묘한 차이가 있을 수 있지만 일반적으로는 같다.</blockquote> 



## 함수의 사용 이유

- 함수는 필요할 떄 여러 번 호출할 수 있다. 실행 시점을 개발자가 결정할 수 있고 몇 번이든 재사용이 가능하다.

### 코드의 재사용

- 동일한 작업을 반복적으로 수행해야 한다면 같은 코드를 중복해서 여러 번 작성하는 것이 아니라 미리 정의된 함수를 재사용하는 것이 효율적이다.



### 유지보수와 신뢰성

- 같은 코드를 여러 번 작성한다면 코드의 길이가 길어지게 되고 수정해야 할 때 그 양도 늘어나게 된다.
- 또한 '사람'이기 때문에 코드 작성에 있어서 실수할 가능성이 현저히 높아진다.
- **즉, 함수는 유지보수의 편의성을 높이고 실수를 줄여 코드의 신뢰성을 높이는 효과가 있다**.
- **함수는 객체 타입의 값이므로** 식별자를 붙일 수 있고, 함수 자신의 역할을 잘 설명해주는 식별자를 붙여야 가독성이 향상된다.

코드는 동작하는 것만이 존재 목적은 아니다. 코드는 개발자를 위한 문서이기도 하다. 따라서 사람이 이해할 수 있는 코드, 즉 가독성이 좋은 코드가 좋은 코드다.



## 함수 리터럴

자바스크립트의 함수는 객체 타입의 값이다. 따라서 숫자, 객체 리터럴처럼 함수도 **함수 리터럴로 생성할 수 있다. **함수 리터럴은 **function 키워드, 함수 이름, 매개변수 목록, 함수 몸체**로 구성된다.

```javascript
// 변수에 함수 리터럴을 할당
var f = function add(x,y){
    return x + y;
};
```

함수 리터럴의 구성 요소는 다음과 같다.

### 함수 이름

- 함수 이름은 식별자다. **따라서 식별자 네이밍 규칙을 준수해야 한다.**
- 함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자이다.
- 함수 이름은 생략할 수 있다. 이름 있는 함수는 **기명 함수(named function)**, 이름이 없는 함수를 **익명 함수(anonymous function)**이라 한다.

### 매개변수 목록

- <span style=color:red>0개</span> 이상의 매개 변수를 소괄호로 감싸고 쉼표로 구분한다.
- 각 매개변수에는 함수를 호출할 때 지정한 인수가 순서대로 할당된다.
- 매개 변수는 함수 몸체 내에서 변수와 동일하게 취급된다. 따라서 매개변수도 변수와 마찬가지로 식별자 네이밍 규칙을 준수해야 한다.

### 함수 몸체

- 함수가 호출되었을 때 일괄적으로 실행될 문들을 하나의 실행 단위로 정의한 **코드 블록이다.**
- 함수 몸체는 호출에 의해 실행된다.

위 예제를 보면 함수 리터럴을 변수에 할당하고 있다. 리터럴은 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 표기 방식(notation)을 말한다. 즉, 리터럴은 값을 생성하기 위한 표기법이다.

즉, 리터럴은 값을 생성하기 위한 표기법이다. 따라서 함수 리터럴도 평가되어 값을 생성하며, 이 값은 객체다. 즉, **함수는 객체다**.

함수는 객체지만 일반 객체와는 다르다. 
**일반 객체는 호출할 수 없지만 함수는 호출할 수 있다. 그리고 일반 객체에는 없는 함수 객체만의 고유한 프로퍼티를 갖는다.**

함수가 객체라는 사실은 다른 프로그래밍 언어와 구별되는 자바스크립트의 중요한 특징이다.



## 함수 정의

함수 정의란 함수를 호출하기 이전에 인수를 전달 받을 매개변수와 실행할 문들, 그리고 반환할 값을 지정하는 것을 말한다. 정의된 함수는 자바스크립트 엔진에 의해 평가되어 **함수 객체**가 된다.

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



### 변수 선언 vs 함수 정의

변수는 '선언(declaration)' 한다고 하지만 함수는 '정의(definition)' 한다고 한다.
**함수 선언문이 평가되면 식별자가 암묵적으로 생성되고 함수 객체가 할당된다** 따라서 ECMAScript 사양에서도 변수에는 선언(variable declaration), 함수에는 정의(function definition)라고 표현한다.



## 함수 선언문

```javascript
// 함수 선언문
function add(x, y) {
  return x + y;
}

// 함수 참조
// console.dir은 console.log와는 달리 함수 객체의 프로퍼티까지 출력한다.
// 단 Node.js환경에서는 console.log와 같은 결과가 출력된다.
console.dir(add); // ƒ add(x, y)

// 함수 호출
console.log(add(2, 5)); // 7
```

함수 선언문은 함수 리터럴과 형태가 동일하다. 단, 함수 리터럴은 함수 이름을 생략할 수 있으나 **함수 선언문은 함수 이름을 생략할 수 없다.**

```javascript
// 함수 선언문은 함수 이름을 생략할 수 없다.
function (x, y){
  return x + y;
}

// SyntaxError: Function statements require a function name
```

**함수 선언문은 표현식이 아닌 문이다.**

즉, 크롬 개발자 도구의 콘솔에서 함수 선언문을 실행하면 완료 값(completion value) `undefined`가 출력된다. 표현식이 아닌 문은 변수에 할당 할 수 없다. 함수 선언문이 만약 표현식인 문이라면 완료 값 `undefined`대신 표현식이 평가되어 생성된 함수가 출력되어야 한다.



하지만 다음 예제를  실행해보면 함수 선언문이 변수에 할당되는 것처럼 보인다.

```javascript
// 함수 선언문은 표현식이 아닌 문이므로 변수에 할당할 수 없다.
// 하지만 함수 선언문이 변수에 할당되는 것처럼 보인다.
var add = function add(x, y) {
  return x + y;
};

// 함수 호출
console.log(add(2, 5));
```

이렇게 동작하는 이유는 자바스크립트 엔진인 코드의 문맥에 따라 동일한 **함수 리터럴**을 표현식이 아닌 문인 **함수 선언문**으로 해석하는 경우와 표현식인 문인 **함수 리터럴 표현식**으로 해석하는 경우가 있기 때문이다.

함수 선언문은 함수 이름을 생략할 수 없다는 점을 제외하면 함수 리터럴과 형태가 동일하다. 이는 함수 이름이 있는 기명함수 리터럴은 함수 선언문 또는 함수 리터럴 표현식으로 해석될 가능성이 있음을 의미한다.

- 예를 들면, `{}`은 블록문일 수도 있고 객체 리터럴일 수도 있다. 즉, `{}`은 중의적 표현(하나의 문장이 둘 이상의 의미로 해석될 수 있는 표현)이다. `{}`처럼 중의적인 코드는 코드의 문맥에 따라 해석이 달라진다. `{}`이 단독으로 존재하면 자바스크립트 엔진은 `{}`을 블록문으로 해석한다. 하지만 **`{}`이 값으로 평가되어야 할 문맥(할당 연산자의 우변)**에서 피연산자로 사용되면 자바스크립트 엔진은 `{}`을 객체 리터럴로 해석한다.
- 기명 함수 리터럴도 중의적인 코드다. 따라서 코드의 문맥에 따라 해석이 달라질 수 있다. 자바스크립트 엔진은 **함수 이름이 있는 리터럴을 단독으로 사용**(값으로 평가되어야 하는 문맥에서 함수 리터럴을 사용하지 않는 경우, 다시 말해 함수 리터럴을 피연산자로 사용하지 않는 경우)**하면 함수 선언문으로 해석하고**, 함수 리터럴이 값으로 평가되어야 하는 문맥, 예를 들어 함수 리터럴을 변수에 할당하거나 피연산자로 사용하면 함수 리터럴 표현식으로 해석한다. 이 때 함수 선언문이든 함수 리터럴 표현식이든 함수가 생성되는 것은 동일하다.

```javascript
// 기명 함수 리터럴을 단독으로 사용하면 함수 선언문으로 해석된다.
// 함수 선언문에서는 함수 이름을 생략할 수 없다.

function foo() {
  console.log("foo");
}
foo(); // foo

// 함수 리터럴을 피연산자로 사용하면 함수 선언문이 아니라 함수 리터럴 표현식으로 해석된다.
// 함수 리터럴에서는 함수 이름을 생략할 수 있다.
(function bar() {
  console.log("bar");
});
bar(); // ReferenceError : bar is not defined
```

- 위 예제에서 단독으로 사용된 함수 리터럴(foo)은 함수 선언문을 해석된다.
- 하지만 그룹 연산자`()`내에 있는 함수 리터럴(bar)은 함수 선언문으로 해석되지 않고 함수 리터럴 표현식으로 해석된다. 그룹 연산자의 피연산자는 값으로 평가될 수 있는 표현식이어야 한다. 따라서 표현식이 아닌 문인 함수 선언문은 피연산자로 사용할 수 없다.

- 함수 선언문과 함수 리터럴 표현식은 함수 객체를 생성한다는 점에서 동일하지만 호출에 차이가 있다.
- 위 예제에서 함수 선언문으로 생성된 foo는 호출할 수 있으나 함수 리터럴 표현식으로 생성된 bar는 호출할 수 없다.
- 함수 리터럴의 함수 이름은 함수 몸체 내에서만 참조할 수 있는 식별자라고 했다. 이는 함수 몸체 외부에서는 함수 이름으로 함수를 참조할 수 없으므로 함수 몸체 외부에서는 함수 이름으로 함수를 호출할 수 없다는 의미이다. 즉, 함수를 가리키는 식별자가 없다는 것과 마찬가지이다. 



- 그러나 위 에제에서 함수 선언문으로 정의된 함수 foo라는 이름으로 호출할 수 있었다.
- foo는 함수 몸체 내부에서만 유효한 식별자인 함수 이름이므로 foo로 함수를 호출할 수 없어야 한다. foo라는 이름으로 호출하려면 foo는 함수 이름이 아니라 함수 객체를 가리키는 식별자여야 한다.
- 식별자를 선언한적 없지만 가능한 이유는 foo는 **자바스크립트 엔진**이 암묵적으로 생성한 식별자이다.



자바스크립트 엔진은 함수 선언문을 해석해 함수 객체를 생성한다. 이 때 함수 이름은 함수 몸체 내부에서만 유효한 식별자이므로 함수 이름과는 별도로 생성된 함수 객체를 가리키는 식별자가 필요하다. 함수 객체를 가리키는 식별자가 없으면 생성된 함수 객체를 참조할 수 없으므로 호출할 수도 없다.

따라서 **자바스크립트 엔진은 생성된 함수를 호출하기 위해 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하고, 거기에 생성된 함수 객체를 할당한다.**

정리해보면, 다음과 같은 수도(pseudo)코드로 나타낼 수 있다.

```javascript
var add = function add(x,y){
    return x + y;
};

console.log(add(2,5)); // 7
```

**함수는 함수 이름으로 호출하는 것이 아니라 함수 객체를 가리키는 식별자로 호출한다.** 즉, 함수 선언문으로 생성한 함수를 호출한 것은 함수 이름 `add`가 아니라 자바스크립트 엔진이 암묵적으로 생성한 식별자 `add`인 것이다. 



**결론적으로 자바스크립트 엔진은 함수 선언문을 함수 표현식으로 변환해 함수 객체를 생성한다고 생각할 수 있다. 단, 함수 선언문과 함수 표현식이 정확하게 동일하게 동작하지는 않는다.**



## 함수 표현식

자바스크립트의 함수는 객체 타입의 값이다. 자바스크립트의 함수는 값처럼 변수에 할당할 수도 있고 프로퍼티 값이 될 수 도 있으며 배열의 요소가 될 수도 있다.

- 이처럼 값의 성질을 갖는 객체를 **일급 객체(first-class object)**라 한다.
- 일급 객체라는 것은 함수를 값처럼 자유롭게 사용할 수 있다는 의미이다.
- 함수는 일급 객체이므로 함수 리터럴로 생성한 함수 객체를 변수에 할당할 수 있다. 이러한 함수 정의 방식을 함수 표현식(function expression)이라 한다.

```javascript
// 함수 표현식
var add = function(x,y){
    return x + y;
};

console.log(add(2,5)); // 7
```

- 함수 리터럴은 함수 이름을 생략할 수 있다. 이러한 함수를 *익명 함수(anonymous function)*이라 한다.
- **함수 표현식의 함수 리터럴은 함수 이름을 생략하는게 일반적이다.**
- 함수를 호출할 때는 함수 이름이 아니라 함수 객체를 가리키는 식별자를 사용해야 한다. 함수 이름은 함수 몸체 내부에서만 유효한 식별자이므로 함수 이름으로 함수를 호출할 수 없다.

```javascript
// 기명 함수 표현식
var add = function foo(x,y){
  return x + y;
};
// 함수 객체를 가리키는 식별자로 호출
console.log(add(2,5));

// 함수 이름으로 호출하면 ReferenceError가 발생한다.
// 함수 이름은 함수 몸체 내부에서만 유효한 식별자다.
console.log(foo(2,5)); // ReferenceError: foo is not defined
```

- 자바스크립트 엔진은 함수 선언문의 함수 이름으로 식별자를 암묵적으로 생성하고 생성된 함수 객체를 할당하므로 함수 표현식과 유사하게 동작하는 것처럼 보인다.
- 함수 선언문은 "표현식이 아닌 문"이고 함수 표현식은 "표현식인 문"이다.



## 함수 생성 시점과 함수 호이스팅

```javascript
// 함수 참조
console.dir(add); // ƒ add(x, y)
console.dir(sub); // undefined

//함수 호출
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

- 위 예제와 같이 함수 선언문으로 정의한 함수는 함수 선언문 이전에 호출할 수 있다. 그러나 함수 표현식으로 정의한 함수는 함수 표현식 이전에 호출할 수 없다.
- 이는 **함수 선언문으로 정의한 함수와 함수 표현식으로 정의한 함수의 생성 시점이 다르기 때문이다.**

- 모든 선언문이 그렇듯 함수 선언문도 코드가 한줄씩 순차적으로 실행되는 시점(runtime)이전에 자바스크립트 엔진에 의해 먼저 실행된다.  **다시 말해, 함수 선언문으로 함수를 정의하면 런타임 이전에 함수 객체가 먼저 생성된다.** 그리고 자바스크립트 엔진은 함수 이름과 동일한 이름의 식별자를 암묵적으로 생성하고 생성된 함수 객체를 할당한다.
- 즉, 코드가 한 줄씩 순차적으로 실행되기 시작하는 런타임에는 이미 함수 객체가 생성되어 있고 함수 이름과 동일한 식별자에 할당까지 완료된 상태이다. 따라서 함수 선언문 이전에 함수를 참조할 수 있으며 호출도 할 수 있다. **함수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트의 고유의 특징을 함수 호이스팅(function hoisting)이라 한다.**



### 함수 호이스팅 vs 변수 호이스팅

- `var` 키워드를 사용한 변수 선언문과 함수 선언문은 런타임 이전에 자바스크립트 엔진에 의해 먼저 실행되어 식별자를 생성한다는 점에서 동일하다.
- 하지만 `var` 키워드로 선언된 변수는 `undefined`로 초기화되고, **함수 선언문을 통해 암묵적으로 생성된 식별자는 함수 객체로 초기화된다.**
- 따라서 `var`키워드를 사용한 변수 선언문 이전에 변수를 참조하면 변수 호이스팅에 의해 `undefined`로 평가되지만 함수 선언문으로 정의한 함수를 함수 선언문 이전에 호출하면 함수 호이스팅에 의해 호출이 가능하다.
- 함수 표현식은 변수에 할당되는 값이 함수 리터럴인 문이다. 따라서 함수 표현식은 변수 선언문과 변수 할당문을 한번에 기술한 축약 표현과 동일하게 동작한다.
- 변수 선언은 런타임 이전에 실행되어 `undefined`로 초기화되지만 **변수 할당문의 값은 할당문이 실행되는 시점, 즉 런타임에 평가되므로 함수 표현식의 함수 리터럴도 할당문이 실행되는 시점에 평가되어 함수 객체가 된다.**
- 따라서 **함수 표현식으로 함수를 정의하면 함수 호이스팅이 아니라 변수 호이스팅이 발생한다**



**함수 표현식 이전에 함수를 참조하면 undefined로 평가된다. 따라서 이때 함수를 호출하면 undefined를 호출하는 것과 마찬가지이므로 타입 에러(TypeError)가 발생한다.**

<blockquote>함수 호이스팅은 함수를 호출하기 전에 반드시 함수를 선언해야 한다는 당연한 규칙을 무시한다. 이 같은 문제 때문에 함수 선언문 대신 함수 표현식을 사용할 것을 권장한다. <i>- Douglas Crockford -</i> </blockquote>



## Function 생성자 함수

자바스크립트가 기본 제공하는 빌트인 함수 `Function `생성자 함수에 매개변수 목록과 함수 몸체를 문자열로 전달하면서 new 연산자와 함께 호출하면 함수 객체를 생성해서 반환한다.

```javascript
var add = new Function('x','y','return x + y');

console.log(add(2,5)); // 7
```

- `Function` 생성자 함수로 생성한 함수는 클로저(closure)를 생성하지 않는 등, 함수 선언 문이나 함수 표현식으로 생성한 함수와 다르게 동작한다.
- 일반적이지 않은 방식이고, *클로저를 생성하지 않는 등, 함수 선언문이나 함수 표현식으로 생성한 함수와 다르게 동작한다.*

```javascript
var add1 = (function () {
  var a = 10;
  return function (x, y) {
    return x + y + a;
  };
}());

console.log(add1(1, 2)); // 13

var add2 = (function () {
  var a = 10;
  return new Function('x', 'y', 'return x + y + a;');
}());

console.log(add2(1, 2)); // ReferenceError: a is not defined
```

함수 선언문이나 함수 표현식으로 생성한 함수와 Function 생성자 함수로 생성한 함수가 동일하게 동작하지 않는다.



## 화살표 함수

ES6에서 새롭게 도입된 화살표 함수(arrow function)는 function 키워드 대신 화살표 (=>,fat arrow)를 사용해 좀 더 간략하게 사용할 수 있고 **화살표 함수는 항상 익명 함수로 정의한다**.

```javascript
// 화살표 함수
const add = (x,y) => x +y;
console.log(add(2,5)); // 7
```

화살표 함수는 생성자 함수로 사용할 수 없으며 기존의 함수와 `this` 바인딩 방식이 다르고, `prototype `프로퍼티가 없으며 `arguments` 객체를 생성하지 않는다.



## 함수 호출

- 함수는 함수를 가리키는 식별자와 한 쌍의 소괄호인 함수 호출 연산자를 호출한다. 함수 호출 연산자 내에는 0개 이상의 인수를 쉼표로 구분해서 나열한다. 함수를 호출하면 현재의 실행 흐름을 중단하고 호출된 함수로 실행 흐름을 옮긴다.
- 이 때 매개 변수에 인수가 순서대로 할당되고 함수 몸체의 문들이 시작된다.

## 매개변수와 인수

함수를 실행하기 위해 필요한 값을 함수 외부에서 함수 내부로 전달할 필요가 있는 경우, 매개변수(parameter, 인자)를 통해 인수(arguments)를 전달한다.
인수는 값으로 평가될 수 있는 표현식이어야 한다.

```javascript
// 함수 선언문
function add(x,y){
    return x + y;
}

// 함수 호출
// 인수 1과 2는 매개변수 x와 y에 순서대로 할당되고 함수 몸체의 문들이 실행된다.

var result = add(1,2);
```

매개변수는 함수를 정의할 때 선언하며 함수 몸체 내부에서 변수와 동일하게 취급된다. 즉 함수가 호출되면 함수 몸체 내에서 암묵적으로 매개 변수가 생성되고 일반 변수와 마찬가지로 `undefined`로 초기화된 이후 인수가 순서대로 할당된다.

**함수가 호출될 때마다 매개변수는 이와 같은 단계를 거친다.**



매개변수는 함수 몸체 내부에서만 참조할 수 있고 함수 몸체 외부에서는 참조할 수 없다. 즉, 매개변수의 스코프는 함수 내부이다.

```javascript
function add(x, y) {
  console.log(x, y); // 2 5
  return x + y;
}

add(2, 5);

// add 함수의 매개변수 x, y는 함수 몸체 내부에서만 참조할 수 있다.

console.log(x, y); // ReferenceError: x is not defined
```

함수는 매개변수의 개수와 인수의 개수가 일치하는지 체크하지 않는다. 즉, 함수를 호출할 때 매개변수의 개수만큼 인수를 전달하는 것이 일반적이지만 그렇지 않은 경우에도 에러를 발생시키지는 않는다.

인수가 부족해서 인수가 할당되지 않은 매개변수의 값은 `undefined`이다.

```javascript
function add(x,y){
    return x + y;
}

console.log(add(2)); // NaN
```

- 위 예제의 매개변수 x에는 인수 2가 전달되지만,  y 에는 전달할 인수가 없다. 따라서 매개변수 y는 `undefined`로 초기화된 상태 그대로다. 
- 따라서 함수 몸체의 문 `x+y`는 `2+undefined`와 같으므로 `NaN`이 반환된다.

```javascript
function add(x,y){
    return x+y;
}
console.log(add(2,5,10)); // 7
```

- 초과된 인수는 그냥 버려지지 않고 암묵적으로 `arguments 객체`의 프로퍼티로 보관된다.

```javascript
function add(x, y) {
  console.log(arguments);
// Arguments(3) [2, 5, 10, callee: ƒ, Symbol(Symbol.iterator): ƒ]
  return x + y;
}

add(2, 5, 10);
```

`arguments`객체는 함수를 정의할 때, 매개변수 개수를 확정할 수 없는 가변 인자 함수를 구현할 때 유용하게 사용된다.



## 인수 확인

```javascript
function add(x,y){
    return x + y;
}
```

위 함수를 정의한 개발자의 의도는 아마도 2개의 숫자 타입 인수를 전달받아 그 합계를 반환하려 했을 것이다. 그러나 코드상 어떤 타입의 인수를 전달해야 하는지, 어떤 타입의 값을 반환하는지 명확하지 않다.

```javascript
function add(x,y){
    return x + y;
}

console.log(add(2)); // NaN
console.log(add('a', 'b')); // 'ab'
```

이렇게 인수를 전달할 수도 있을 것이다. 이러한 상황이 발생한 이유는?

1. 자바스크립트 함수는 매개변수와 인수의 개수가 일치하는지 확인하지 않는다.
2. 자바스크립트는 동적 타입 언어다. 따라서 자바스크립트 함수는 매개변수의 타입을 사전에 지정할 수 없다.

```javascript
function add(x, y) {
  if (typeof x !== 'number' || typeof y !== 'number') {
    // 매개변수를 통해 전달된 인수의 타입이 부적절한 경우 에러를 발생시킨다.
    throw new TypeError('인수는 모두 숫자 값이어야 합니다.');
  }
  return x + y;
}

console.log(add(2)); // TypeError: 인수는 모두 숫자 값이어야 합니다.
console.log(add('a', 'b')); // TypeError: 인수는 모두 숫자 값이어야 합니다.
```

- `타입스크립트(TypeScript)`와 같은 정적 타입을 선언할 수 있는 자바스크립트의 상위 확장을 도입해서 컴파일 시점에 부적절한 호출을 방지할 수 있게 하는 것도 하나의 방법이다.

- 앞의 예제의 경우, 인수의 개수는 확인하고 있지 않지만 `arguments`객체를 통해 인수 개수를 확인할 수도 있다. 또는 인수가 전달되지 않은 경우 단축 평가를 사용해 매개변수에 기본 값을 할당하는 방법도 있다.

```javascript
function add(a, b, c) {
  a = a || 0;
  b = b || 0;
  c = c || 0;
  return a + b + c;
}

console.log(add(1, 2, 3)); // 6
console.log(add(1, 2)); // 3
console.log(add(1)); // 1
console.log(add()); // 0
```

- `ES6`에서 도입된 매개변수 기본 값을 사용하면 함수 내에서 수행하던 인수 체크 및 초기화를 간소화할 수 있다.
- 단 매개변수 기본 값은 매개변수에 인수를 전달하지 않았을 경우와 `undefined`를 전달한 경우에만 유효하다.

```javascript
function add(a = 0, b = 0, c = 0) {
  return a + b + c;
}

console.log(add(1, 2, 3)); // 6
console.log(add(1, 2)); // 3
console.log(add(1)); // 1
console.log(add()); // 0
```



## 매개변수의 최대 개수

매개변수는 순서에 의미가 있다. 따라서 매개변수가 많아지면 함수를 호출할 때 인자를 전달해야 할 인수의 순서를 고려해야 한다. 이는 함수의 사용법을 이해하기 어렵게 만들고 실수를 발생시킬 가능성을 높인다.

또한 매개변수의 개수나 순서가 변경되면 함수의 호출 방법도 바뀌므로 함수를 사용하는 코드 전체가 영향을 받는다. 즉 유지보수가 나빠진다.

함수의 매개변수는 코드를 이해하는 데 방해가 되는 요소이므로 이상적인 매개변수 개수는 0개이며 적을 수록 좋다. 매개변수의 개수가 많다는 것은 함수가 여러가지 일을 한다는 증거이므로 바람직하지 않다.

**이상적인 함수는 한 가지 일만해야 하며 가급적 작게 만들어야 한다. 매개 변수는 최대 3개 이상을 넘지 않는 것을 권장한다.**



## 반환문

- 함수는 return 키워드와 표현식으로 이뤄진  반환문을 이용해 실행 결과를 함수 외부로 반환할 수 있다.

```javascript
function multiply(x, y) {
  return x * y; // 반환문
}
// 함수 호출은 반환 값으로 평가된다.
var result = multiply(3, 5); 
console.log(result); // 15
```

- `multiply`함수는 두 개의 인수를 전달받아 곱한 결과값을 `return`키워드를 사용해 반환한다. 함수는 `return`키워드를 사용해 자바스크립트에서 사용 가능한 모든 값을 반환할 수 있다.
- **함수 호출은 표현식**이다. 함수 호출 표현식은 `return`키워드가 반환한 표현식의 평가 결과, 즉 반환값으로 평가된다.



반환문은 두 가지 역할을 한다.

1. 반환문은 함수의 실행을 중단하고 함수 몸체를 빠져나간다. 따라서 반환문 이후에 다른 문이 존재하면 그 문은 실행되지 않고 무시된다.

```javascript
function multiply(x, y) {
  return x * y; // 반환문
  // 반환문 이후에 다른 문이 존재하면 그 문은 실행되지 않고 무시된다.
  console.log('실행되지 않는다.');
}

console.log(multiply(3, 5)); // 15
```

2. 반환문은 `return`키워드 뒤에 오는 표현식을 평가해 반환한다. **`return`키워드 뒤에 반환값으로 사용할 표현식을 명시적으로 지정하지 않으면 `undefined`가 반환된다.**

```javascript
function foo () {
  return;
}

console.log(foo()); // undefined
```

반환문은 생략할 수 있다. 이 때 함수는 함수 몸체의 마지막 문까지 실행한 후 암묵적으로 `undefined`를 반환한다.

```javascript
function foo(){
    // 반환문을 생략하면 암묵적으로 undefined가 반환된다.
}

console.log(foo()); // undefined
```

`return`키워드와 반환값으로 사용할 표현식 사이에 줄바꿈이 있으면 세미콜론 자동 삽입 기능(ASI)에 의해 세미콜론이 추가되어 다음과 같이 의도치 않은 결과가 도출된다.

```javascript
function multiply(x, y) {
  // return 키워드와 반환값 사이에 줄바꿈이 있으면
  return // 세미콜론 자동 삽입 기능(ASI)에 의해 세미콜론이 추가됨
  x * y; // 무시된다.
}

console.log(multiply(3, 5)); // undefined
```

반환문은 함수 몸체 내부에서만 사용할 수 있다. 전역에서 반환문을 사용하면 문법 에러(SyntaxError: Illegal return statement)가 발생한다.

```html
<!DOCTYPE html>
<html>
<body>
  <script>
    return; // SyntaxError: Illegal return statement
  </script>
</body>
</html>
```



## 참조에 의한 전달과 외부 상태의 변경

- **원시 값**은 값에 의한 전달(pass by value) 방식으로 동작한다.
- **객체**는 참조에 의한 전달(pass by reference) 방식으로 동작한다.

매개변수도 함수 몸체 내부에서 변수와 동일하게 취급되므로 매개변수 또한 타입에 따라 값에 의한 전달, 참조에 의한 전달 방식을 그대로 따른다.

```javascript
// 매개변수 primitive는 원시값을 전달받고, 매개변수 obj는 객체를 전달받는다.
function changeVal(primitive, obj) {
  primitive += 100;
  obj.name = 'Kim';
}

// 외부 상태
var num = 100;
var person = {
  name: 'Lee'
};

console.log(num); // 100
console.log(person); // {name : 'Lee'}

// 원시값은 값 자체가 복사되어 전달되고 객체는 참조값이 복사되어 전달된다.
changeVal(num, person);

// 원시값은 훼손되지 않는다.
console.log(num); // 100

// 객체는 원본이 훼손된다.
console.log(person); {name : 'Kim'}
```

- `changeVal`함수는 매개변수를 통해 전달 받은 원시 타입 인수와 객체 타입 인수를 함수 몸체에서 변경한다. 엄밀히 말하면 원시 타입 인수를 전달받은 매개변수 `primitive`의 경우, 원시 값은 변경 불가능한 값이므로 직접 변경할 수 없기 때문에 재할당을 통해 할당된 원시값을 새로운 원시값으로 교체했고 객체 타입 인수를 전달 받은 매개 변수 obj의 경우, 객체는 변경 가능한 값이므로 직접 변경할 수 있기 때문에 재할당 없이 직접 할당된 객체를 변경했다.
- 이 때 원시 타입의 인수는 값 자체가 복사되어 매개 변수에 전달되기 때문에 함수 몸체에서 그 값을 변경해도 원본은 훼손되지 않는다. 다시 말해, 외부 상태, 즉 함수 외부에서 함수 몸체 내부로 전달한 원시값의 원본을 변경하는 어떠한 부수 효과도 발생하지 않는다.
- 하지만 객체 타입 인수는 참조값이 복사되어 매개변수에 전달되기 때문에 함수 몸체에서 참조값을 통해 객체를 변경할 경우 원본이 훼손된다. 다시 말해, 외부 상태, 즉 함수 외부에서 함수 몸체 내부로 전달한 참조값에 의해 원본 객체가 변경되는 부수 효과가 발생한다.





#### 참조에 의한 전달 방식의 단점

- 함수가 외부 상태(person 변수)를 변경하면 상태 변화를 추적하기 어려워진다.
- 여러 변수가 참조에 의한 전달 방식을 통해 참조 값을 공유하고 있다면 이 변수들은 언제든지 참조하고 있는 객체를 직접 변경할 수 있다.
- 이러한 문제의 해결 방법 중 하나는 **객체를 불변 객체(immutable object)**로 만들어 사용하는 것이다.
- 즉, 깊은 복사(deep copy)를 통해 새로운 객체를 생성하고 재할당을 통해 교체한다.
- 외부 상태를 변경하지 않고 외부 상태에 의존하지도 않는 함수를 **순수 함수**라 한다.



## 다양한 함수의 형태

### 즉시 실행 함수(Immediately Invoked Function Expression)

- 함수 정의와 동시에 즉시 호출되는 함수를 <u>즉시 실행 함수</u>라고 한다. 즉시 실행 함수는 단 한 번만 호출되면 다시 호출할 수 없다.

```javascript
// 익명 즉시 실행 함수
(function () {
  var a = 3;
  var b = 5;
  return a * b;
}());
```

- 즉시 실행 함수는 이름이 없는 익명 함수를 사용하는 것이 일반적이다.
- 함수 이름이 있는 기명 즉시 실행 함수도 사용할 수 있다. 하지만 그룹 연산자`(...)`내의 기명 함수는 함수 선언문이 아니라 함수 리터럴로 평가되며 함수 이름은 함수 몸체에서만 참조할 수 있는 식별자이므로 즉시 실행 함수를 다시 호출할 수는 없다.

```javascript
// 기명 즉시 실행 함수
(function foo() {
  var a = 3;
  var b = 5;
  return a * b;
}());

foo(); // ReferenceError: foo is not defined
```

- 즉시 실행 함수는 반드시 그룹 연산자 `(...)`로 감싸야 한다. 그렇지 않으면 다음과 같이 에러가 발생한다.

```javascript
function () {
  // SyntaxError: Function statements require a function name
  // ...
}();
```

- 위 예제에서 에러가 발생하는 이유는 함수 정의가 함수 선언문의 형식에 맞지 않기 때문이다. 함수 선언문은 함수 이름을 생략할 수 없다.

```javascript
function foo() {
  // ...
}(); // SyntaxError: Unexpected token ')'
```

- 위 예제에서도 에러가 발생한다. 
- 자바스크립트 엔진이 암묵적으로 수행하는 세미콜론 자동 삽입 기능(ASI)에 의해 함수 선언문이 끝나는 위치,  즉 함수 코드 블록의 닫는 중괄호 뒤에 "`;`"이 암묵적으로 추가되었기 때문이다.

```javascript
function foo(){}(); // function foo() {};();
```

- 따라서 함수 선언문 뒤의 `(...)`는 함수 호출 연산자가 아니라 그룹 연산자로 해석되고, 그룹 연산자에 피연산자가 없기 때문에 에러가 발생한다.
- 그룹 연산자의 피연산자는 값으로 평가되므로 기명 또는 무명 함수를 그룹 연산자로 감싸면 함수 리터럴로 평가되어 함수 객체가 된다.

```javascript
console.log(typeof(function f(){})); // function
console.log(typeof (function (){}));  // function
```

- 즉, 그룹 연산자로 함수를 묶은 이유는 먼저 함수 리터럴을 평가해서 함수 객체를 생성하기 위해서다.
- 따라서 먼저 함수 리터럴을 평가해서 함수 객체를 생성할 수 있다면 다음과 같이 그룹 연산자 이외의 연산자를 사용해도 괜찮다.

```javascript
(function () {
  // ...
}());

(function () {
  // ...
})();

!function () {
  // ...
}();

+function () {
  // ...
}();
```

즉시 실행 함수도 일반 함수처럼 값을 반환할 수 있고 인수를 전달할 수 있다.

```javascript
// 즉시 실행 함수도 일반 함수처럼 값을 반환할 수 있다.
var res = (function () {
  var a = 3;
  var b = 5;
  return a * b;
}());

console.log(res); // 15

// 즉시 실행 함수에도 일반 함수처럼 인수를 전달할 수 있다.
res = (function (a, b) {
  return a * b;
}(3, 5));

console.log(res); // 15
```

즉시 실행 함수 내에 코드를 모아 두면 혹시 있을 수도 있는 변수나 함수 이름의 충돌을 방지할 수 있다.



## 재귀 함수

- 함수가 자기 자신을 호출하는 것을 재귀 호출(recursive call) 이라 한다.

```javascript
function countdown(n) {
  for (var i = n; i >= 0; i--) {
    console.log(i);
  }
}
countdown(10);
```

이를 반복문 없이 구현한다면,

```javascript
function countdown(n) {
  if (n < 0) return;
  console.log(n);
  countdown(n - 1);
}

countdown(10);
```

이처럼 자기 자신을 호출하는 재귀 함수를 사용하면 반복되는 처리를 반복문 없이 구현할 수 있다. 예를 들어, 팩토리얼은 재귀 함수로 간단히 구현할 수 있다.

#### 팩토리얼 예제

```javascript
// 팩토리얼(게승)은 1부터 자신까지의 모든 양의 정수의 곱이다.
// n! = 1 * 2 * ... * (n-1) * n
function factorial(n){
    // 탈출 조건 : n이 1 이하일 때 재귀 호출을 멈춘다.
    if(n <= 1) return 1;
    return n * factorial(n-1);
}
console.log(factorial(0)); // 0! = 1
console.log(factorial(1)); // 1! = 1
console.log(factorial(2)); // 2! = 2 * 1 = 2
console.log(factorial(3)); // 3! = 3 * 2 * 1 = 6
console.log(factorial(4)); // 4! = 4 * 3 * 1 * 1 = 24
console.log(factorial(5)); // 5! = 5 * 4 * 3 * 2 * 1 = 120
```



`factorial`함수 내부에서 자기 자신을 호출할 때 사용한 식별자 `factorial`은 함수 이름이다. 함수 이름은 함수 몸체 내부에서만 유효하다. 따라서 함수 내부에서는 함수 이름을 사용해 자기 자신을 호출할 수 있다.

함수 표현식으로 정의한 함수 내부에서는 함수 이름은 물론 함수를 가리키는 식별자로도 자기 자신을 재귀 호출할 수 있다. 단, 함수 외부에서 함수를 호출할 때는 반드시 함수를 가리키는 식별자로 해야 한다.

```javascript
// 함수 표현식
var factorial = function foo(n) {
  // 탈출 조건: n이 1 이하일 때 재귀 호출을 멈춘다.
  if (n <= 1) return 1;
  // 함수를 가리키는 식별자로 자기 자신을 재귀 호출
  return n * factorial(n - 1);

  // 함수 이름으로 자기 자신을 재귀 호출할 수도 있다.
  // console.log(factorial === foo); // true
  // return n * foo(n - 1);
};
```

- 재귀 함수는 자신을 무한 재귀 호출한다. 따라서 재귀 함수 내에는 재귀 호출을 멈출 수 있는 **탈출 조건**을 반드시 만들어야 한다. 위 예제의 경우 인수가 1이하일 때 재귀 호출을 멈춘다. 탈출 조건이 없으면 함수가 무한 호출되어 스택 오버플로(stack overflow)에러가 발생한다.

```javascript
// 반복문으로 구현한 팩토리얼
function factorial(n){
  if(n<=1) return 1;

  var res = n;
  while(--n) res *=n;
  return res;
}
console.log(factorial(0)); // 0! = 1
console.log(factorial(1)); // 1! = 1
console.log(factorial(2)); // 2! = 2 * 1 = 2
console.log(factorial(3)); // 3! = 3 * 2 * 1 = 6
console.log(factorial(4)); // 4! = 4 * 3 * 1 * 1 = 24
console.log(factorial(5)); // 5! = 5 * 4 * 3 * 2 * 1 = 120
```

재귀 함수는 반복되는 처리를 반복문 없이 구현할 수 있다는 장점이 있지만 무한 반복에 빠질 위험이 있고, 이로 인해 스택 오버플로 에러를 발생시킬 수 있으므로 주의해서 사용해야 한다. 따라서 재귀 함수는 반복문을 사용하는 것보다 재귀 함수를 사용하는 편이 더 직관적으로 이해하기 쉬울 때만 한정적으로 사용하는 것이 바람직하다.



## 중첩 함수

- 함수 내부에 정의된 함수를 **중첩 함수(nested function)**또는 **내부 함수(inner function)**라 한다.
- 중첩 함수를 포함하는 외부(outer function)이라 부른다.
- 일반적으로 중첩 함수는 자신을 포함하는 외부 함수를 돕는 헬퍼 함수(helper function) 역할을 한다.

``` javascript
function outer(){
    var x = 1;
    
    function inner(){
        var y = 2;
        console.log(x+y); //3
    }
    inner();
}

outer();
```

- ES6부터 함수 정의는 문이 위치할 수 있는 문맥이라면 어디든지 가능하다.
- 함수 선언문의 경우 ES6이전에는 코드의 최상위 또는 다른 함수 내부에서만 정의할 수 있었으나 ES6부터는 if문이나 for문 등의 코드 블록 내에서도 정의할 수 있다.



## 콜백 함수

어떤 일을 반복 수행하는 repeat 함수 예시

```javascript
// n만큼 어떤 일을 반복한다
function repeat(n) {
  // i를 출력한다.
  for (var i = 0; i < n; i++) console.log(i);
}

repeat(5); // 0 1 2 3 4
```

- repeat 함수는 매개변수를 통해 전달 받은 숫자만큼 반복해서 `console.log(i)`를 호출한다.
- `repeat`함수는 `console.log(i)`에 의존하고 있어 다른 일을 할 수 없다.
- 따라서 만약 repeat 함수의 반복문 내부에서 다른 일을 하고 싶다면 함수를 새롭게 정의해야 한다.

```javascript
// n만큼 어떤 일을 반복한다
function repeat1(n) {
  // i를 출력한다.
  for (var i = 0; i < n; i++) console.log(i);
}

repeat1(5); // 0 1 2 3 4

// n만큼 어떤 일을 반복한다
function repeat2(n) {
  for (var i = 0; i < n; i++) {
    // i가 홀수일 때만 출력한다.
    if (i % 2) console.log(i);
  }
}

repeat2(5); // 1 3
```

- 위 예제의 함수들은 반복하는 일은 변하지 않고 공통적으로 수행하지만 반복하면서 하는 일의 내용은 다르다.
- 즉, 함수의 일부분만이 다르기 때문에 매번 함수를 새롭게 정의해야 한다.
- 함수의 변하지 않는 공통 로직은 미리 정의해 두고, 경우에 따라 변경되는 로직은 추상화해서 함수 외부에서 내부로 전달하는 것이다.

```javascript
// 외부에서 전달받은 f를 n만큼 반복 호출한다
function repeat(n, f) {
  for (var i = 0; i < n; i++) {
    f(i); // i를 전달하면서 f를 호출
  }
}

var logAll = function (i) {
  console.log(i);
};

// 반복 호출할 함수를 인수로 전달한다.
repeat(5, logAll); // 0 1 2 3 4

var logOdds = function (i) {
  if (i % 2) console.log(i);
};

// 반복 호출할 함수를 인수로 전달한다.
repeat(5, logOdds); // 1 3
```

- 위 repeat 함수는 경우에 따라 변경되는 일을 함수 f로 추상화했고 이를 외부에서 전달받는다.
- 자바스크립트의 함수는 일급 객체이므로 함수의 매개변수를 통해 함수를 전달할 수 있다.
- repeat 함수는 더 이상 내부 로직에 강력히 의존하지 않고 외부에서 로직의 일부분을 함수로 전달받아 수행하므로 더욱 유현한 구조를 갖게 된다.
- 이처럼 **함수의 매개변수를 통해 다른 함수의  내부로 전달되는 함수를 콜백 함수(callback function)라고 하며, 매개변수를 통해 함수의 외부에서 콜백 함수를 전달받은 함수를 고차 함수(Higher-Order Function, HOF)라고 한다.**
- 중첩 함수가 외부 함수를 돕는 헬퍼 함수의 역할을 하는 것 처럼 **콜백 함수도 고차 함수에 전달되어 헬퍼 함수의 역할을 한다. 단, 중첩 함수는 고정되어 있어서 교체하기 곤란하지만 콜백 함수는 함수 외부에서 고차 함수 내부로 주입하기 때문에 자유롭게 교체할 수 있다는 장점이 있다.**
- 즉, **고차 함수는 콜백 함수를 자신의 일부분으로 합성한다.**
- **고차 함수는 매개변수를 통해 전달받은 콜백 함수의 호출 시점을 결정해서 호출한다.**다시 말해, **콜백 함수는 고차 함수에 의해 호출되며 이때 고차 함수는 필요에 따라 콜백 함수에 인수를 전달할 수 있다. **따라서 고차 함수에 콜백 함수를 전달할 때 콜백 함수를 호출하지 않고 함수 자체를 전달해야 한다.

<blockquote>모든 콜백 함수가 고차 함수에 의해 호출되는 것은 아니다. 예를 들어, setTimeout 함수의 콜백 함수는 setTimeout 함수가 호출하지 않는다.</blockquote>

```javascript
// 익명 함수 리터럴을 콜백 함수로 고차 함수에 전달한다.
// 익명 함수 리터럴은 repeat 함수를 호출할 때마다 평가되어 함수 객체를 생성한다.
repeat(5, function (i) {
  if (i % 2) console.log(i);
}); // 1 3
```

이때 콜백 함수로서 전달된 함수 리터럴은 고차 함수가 호출될 때마다 평가되어 함수 객체를 생성한다. 따라서 콜백 함수를 다른 곳에서도 호출할 필요가 있거나, 콜백 함수를 전달받는 함수가 자주 호출된다면 함수 외부에서 콜백 함수를 정의한 후 함수 참조를 고차 함수에 전달하는 편이 효율적이다.

```javascript
// logOdds 함수는 단 한 번만 생성된다.
var logOdds = function (i) {
  if (i % 2) console.log(i);
};

// 고차 함수에 함수 참조를 전달한다.
repeat(5, logOdds); // 1 3
```

- 위 예제의 `logOdds` 함수는 단 한 번만 생성된다. 하지만 콜백 함수를 익명 함수 리터럴로 정의하면서 곧바로 고차 함수에 전달하면 고차 함수가 호출될 때마다 콜백 함수가 생성된다.
- 콜백 함수는 함수형 프로그래밍 패러다임 뿐만 아니라, 비동기 처리(이벤트 처리, Ajax 통신, Timer 함수 등)에 활용되는 중요한 패턴이다.



## 순수 함수와 비순수 함수

- 함수형 프로그래밍에서는 어떤 외부 상태에 의존하지도 않고 변경하지도 않는, 즉 부수 효과가 없는 함수를 **순수 함수(pure function)**라 하고, 외부 상태에 의존하거나 외부 상태를 변경하는, 즉 부수효과가 있는 함수를 **비순수 함수(impure function)**이라 한다.
- 순수 함수는 동일한 인수가 전달되면 언제나 동일한 값을 반환하는 함수다. 즉, 순수 함수는 어떤 외부 상태에도 의존하지 않고 오직 매개변수를 통해 함수 내부로 전달된 인수에게만 의존해 반환 값을 만든다.
- 순수 함수의 또 하나의 특징은 함수의 외부 상태를 변경하지 않는다는 것이다.
- **즉, 순수 함수는 어떤 외부 상태에도 의존하지 않으며 외부 상태를 변경하지도 않는 함수다.**

```javascript
var count = 0; // 현재 카운트를 나타내는 상태

// 순수 함수 increase는 동일한 인수가 전달되면 언제나 동일한 값을 반환한다.
function increase(n) {
  return ++n;
}

// 순수 함수가 반환한 결과값을 변수에 재할당해서 상태를 변경
count = increase(count);
console.log(count); // 1

count = increase(count);
console.log(count); // 2
```

- 반대로 함수의 외부 상태에 따라 반환 값이 달라지는 함수, 다시 말해, 외부 상태에 의존하는 함수를 **비순수 함수**라고 한다.
- 비순수 함수의 또 하나의 특징은 순수 함수와는 달리 함수의 외부 상태를 변경하는 부수 효과(side effect)가 있다는 것이다. 즉, 비순수 함수는 외부 상태에 의존하거나 외부 상태를 변경하는 함수이다.

```javascript
var count = 0; // 현재 카운트를 나타내는 상태: increase 함수에 의해 변화한다.

// 비순수 함수
function increase() {
  return ++count; // 외부 상태에 의존하며 외부 상태를 변경한다.
}

// 비순수 함수는 외부 상태(count)를 변경하므로 상태 변화를 추적하기 어려워진다.
increase();
console.log(count); // 1

increase();
console.log(count); // 2
```

- 위 예제와 같이 함수 내부에서 외부 상태를 직접 참조하면 외부 상태에 의존하게 되어 반환값이 변할 수 있고, 외부 상태도 변경할 수 있으므로 비순수 함수가 된다. 함수 내부에서 외부 상태를 직접 참조하지 않더라도 매개변수를 통해 객체를 전달받으면 비순수 함수가 된다.
- 함수가 외부 상태를 변경하면 상태 변화를 추적하기 어려워진다. 따라서 함수 외부 상태의 변경을 지양하는 순수 함수를 사용하는 것이 좋다.
- 위 예제의 increase 함수와 같은 비순수 함수는 코드의 복잡성을 증가시킨다. 비순수 함수를 최대한 줄이는 것은 부수 효과를 최대한 억제하는 것과 같다.
- **함수형 프로그래밍은 순수 함수와 보조 함수의 조합을 통해 외부 상태를 변경하는 부수 효과를 최소화해서 불변성(immutability)을 지향하는 프로그래밍 패러다임이다.**
- 함수형 프로그래밍은 결국 순수 함수를 통해 부수 효과를 최대한 억제해 오류를 피하고 프로그램의 안정성을 높이려는 노력의 일환이라 할 수 있다. 자바스크립트는 멀티 패러다임 언어이므로 객체지향 프로그래밍뿐만 아니라 함수형 프로그래밍을 적극적으로 활용하고 있다.

