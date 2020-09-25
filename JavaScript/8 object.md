# 객체 리터럴

## 객체란?

자바스크립트는 **객체(object)**기반의 프로그래밍 언어이며, 자바스크립트를 구성하는 거의 '모든 것'이 객체다. 원시 값을 제외한 나머지(함수, 배열, 정규표현식 등) 모두 객체다

원시 타입 - 단 하나의 값만을 나타낸다.
객체 타입(*object/reference type*) - 다양한 타입의 값(원시값 또는 다른 객체)을 하나의 단위로 구성한 복합적인 자료구조(*data structure*)이다.

#### &#9989; 원시 타입의 값은 변경 불가능한 값이지만 객체 타입의 값은 변경 가능한 값이다

 <img src="https://poiemaweb.com/assets/fs-images/10-1.png" style="zoom: 50%;" />

객체는 0개 이상의 프로퍼티로 구성된 집합이고, *키(key)와 값(value)*으로 구성된다.
**자바스크립트의 함수는 일급 객체이므로 값으로 취급할 수 있다. 따라서 함수도 프로퍼티 값으로 활용할 수 있는데 프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 메서드(method)라 부른다**

<img src="https://poiemaweb.com/assets/fs-images/10-2.png" style="zoom: 33%;" />

- 프로퍼티: 객체의 상태를 나타내는 값(data)
- 메서드 : 프로퍼티를 참조하고 조작할 수 있는 동작(behavior)



#### 객체와 함수

<blockquote>자바스크립트의 객체는 함수와 밀접한 관계를 가진다. 함수로 객체를 생성하기도 하고 함수 자체가 객체이기도 하다. </blockquote>



## 객체 리터럴에 의한 객체 생성

<del>자바 같은 클래스 기반 객체지향 언어는 클래스를 사전에 정의하고 필요한 시점에 new 연산자와 함께 생성자(constructor)를 호출하여 인스턴스를 생성하는 방식으로 객체를 생성한다.</del>

#### 인스턴스란(instance)?

**설계도를 바탕으로 소프트웨어 세계에 구현된 구체적인 실체**

- 객체를 소프트웨어에 실체화 하면 그것을 ‘인스턴스’라고 부른다.
- 실체화된 인스턴스는 메모리에 할당된다.

*자바스크립트는 프로토타입 기반 객체지향 언어로서 다음과 같은 다양한 객체 생성 방법을 지원한다*

- 객체 리터럴
- Object 생성자 함수
- 생성자 함수
- Object.create 메서드
- 클래스 (ES6)

```javascript
// 객체 리터럴을 이용한 객체 생성

var person = {
    name: 'Cho',
    helloWorld: function(){
        console.log(`Hello! My name is ${this.name}.`);
    }
};

console.log(typeof person); //object
console.log(person); // {name:"Cho", helloWorld: f }
```

**중괄호 내에 프로퍼티를 정의하지 않으면 빈 객체가 생성된다.**

```javascript
var empty = {}; // 빈 객체
console.log(typeof empty); // object
```

객체 리터럴의 중괄호는 코드 블록을 의미하지 않는다. 코드 블록의 닫는 중괄호 뒤에는 세미콜론을 붙이지 않는다. 하지만 객체 리터럴은 값으로 평가되는 **표현식**이다. 따라서 객체 리터럴의 닫는 중괄호 뒤에는 세미콜론을 붙인다.

**객체 리터럴은 자바스크립트의 유연함과 강력함을 대표하는 객체 생성 방식이다. 객체를 생성하기 위해 클래스를 정의하고 new 연산자와 함께 생성자를 호출할 필요가 없다.**



## 프로퍼티

```javascript
var person = {
    name : 'Cho', // 프로퍼티 키는 name , 프로퍼티 값은 'cho'
    age : 28 // 프로퍼티 키는 age, 프로퍼티 값은 20
};
```

**객체는 프로퍼티들의 집합이며 프로퍼티는 키와 값으로 구성된다.** 프로퍼티를 나열할 때는 쉼표(,)로 구분한다.

- 프로퍼티 키 : 빈 문자열을 포함하는 모든 문자열 또는 심벌 값
- 프로퍼티 값 : 자바스크립트에서 사용할 수 있는 모든 값

프로퍼티 키는 프로퍼티 값에 접근할 수 있는 이름으로서 식별자 역할을 한다. 하지만 반드시 식별자 네이밍 규칙을 따라야 하는 것은 아니다.

심벌 값도 프로퍼티 키로 사용할 수 있지만 일반적으로 문자열을 사용한다. 이 때 프로퍼티 키는 문자열이므로 따옴표(`'...'`또는 `"..."`)로 묶어야 한다. 하지만 식별자 네이밍 규칙을 준수하는 이름, 즉 **자바스크립트에서 사용 가능한 유효 이름인 경우 따옴표를 생략할 수 있다. 반대로 식별자 네이밍 규칙을 따르지 않는  이름은 반드시 따옴표를 붙여주어야 한다는 것이다.**

```javascript
var person = {
  firstName : 'JaeYeon', // 식별자 네이밍 규칙을 준수하는 프로퍼티 키
  'last-name' : 'Cho', //  식별자 네이밍 규칙을 준수하지 않는 프로퍼티 키
};
```

이 예제에서 `last-name`은 식별자 네이밍 규칙을 준수하지 않았다. 따라서 따옴표를 생략할 수 없다. 자바스크립트는 따옴표를 생략하면 `last-name`에서 `-`를 연산로 해석하기 때문이다.

```javascript
var person = {
  firstName: "Jaeyeon",
  last-name: "Cho", // SyntaxError: Unexpected token '-'
};

```

문자열 또는 문자열로 평가할 수 있는 표현식을 사용해 프로퍼티 키를 동적으로 생성할 수 있다. 이 경우에는 **프로퍼티 키로 사용할 표현식을 대괄호(`[...]`)로 묶어야 한다.**

```javascript
var obj = {};
var key = 'hello';

// ES5 : 프로퍼티 키 동적 생성
obj[key] = 'world';
// ES6 : 계산된 프로퍼티 이름
// var obj = { [key]: 'world'};

console.log(obj); // {hello : "world"}
```

프로퍼티 키에 문자열이나 심벌 값 이외의 값을 사용하면 암묵적 타입 변환을 통해 문자열이 된다.

```javascript
var foo = {
    0 : 1,
    1 : 2,
    2 : 3
};

console.log(foo); // {0 : 1, 1: 2, 2: 3}
```



## 메서드

**자바스크립트에서 사용할 수 있는 모든 값은 프로퍼티 값으로 사용할 수 있다.** 자바스크립트의 함수는<span style=color:red>일급 객체</span>다. 따라서 함수는 값으로 취급할 수 있기 때문에 프로퍼티 값으로 사용할 수 있다.

```javascript
var circle = {
    radius : 5,
    
    getDiameter: function(){ // <- 메서드
        return 2 * this.radius; //this는 circle을 가리킨다
    }
};

console.log(circle.getDiameter()); // 10
```

메서드 내부에서 사용한 `this`키워드는 객체 자신을 가리키는 참조변수이다.



## 프로퍼티 접근

프로퍼티에 접근하는 방법은 두 가지다.

- 마침표 프로퍼티 접근 연산자(.)를 사용하는 **마침표 표기법(dot notation)**
- 대괄호 프로퍼티 접근 연산자([...])를 사용하는 **대괄호 표기법(bracket notation)**

프로퍼티 키가 식별자 네이밍 규칙을 준수하는 이름, 즉 자바스크립트에서 사용 가능한 유효한 이름이면 마침표 표기법과 대괄호 표기법을 모두 사용할 수 있다.

마침표 프로퍼티 접근 연산자 또는 대괄호 프로퍼티 접근 연산자의 좌측에는 객체로 평가되는 표현식을 기술한다. 마침표 프로퍼티 접근 연산자의 우측 또는 대괄호 프로퍼티 접근 연산자의 내부에는 프로퍼티 키를 지정한다.

```javascript
var person = {
    name: 'Cho'
};

// 마침표 표기법에 의한 프로퍼티 접근
console.log(person.name); // Cho

// 대괄호 표기법에 의한 프로퍼티 접근
console.log(person['name']); // Cho
```

- 대괄호 표기법을 사용하는 경우 **대괄호 프로퍼티 접근 연산자 내부에 지정하는 프로퍼티 키는 반드시 따옴표로 감싼 문자열이어야 한다.**
- 대괄호 프로퍼티 접근 연산자 내에 따옴표로 감싸지 않은 이름을 프로퍼티 키로 사용하면 자바스크립트 엔진은 식별자로 해석한다.



```javascript
var person = {
  name : 'Cho'  
};

console.log(person[name]); // ReferenceError: name is not defined
console.log(person['age']); // undefined
```

위 예제에서 `ReferenceError`가 발생한 이유는 대괄호 연산자 내의 따옴표로 감싸지 않은 이름, 즉 식별자 `name`을 평가하기 위해서 선언된 `name`을 찾았지만 찾지 못했기 때문이다.

**객체에 존재하지 않는 프로퍼티에 접근하면 `undefined`를 반환한다. 이 때 `ReferenceError`가 발생하지 않는다는 것에 주의하자**

```javascript
var person = {
  'last-name': 'cho',
  1: 10
};

person.'last-name';  // -> SyntaxError: Unexpected string
person.last-name;    // -> 브라우저 환경: NaN
                     // -> Node.js 환경: ReferenceError: name is not defined

person[last-name];   // -> ReferenceError: last is not defined
person['last-name']; // -> cho

// 프로퍼티 키가 숫자로 이뤄진 문자열인 경우 따옴표를 생략할 수 있다.
person.1;     // -> SyntaxError: Unexpected number
person.'1';   // -> SyntaxError: Unexpected string
person[1];    // -> 10 : person[1] -> person['1']
person['1'];  // -> 10
```

프로퍼티 키가 식별자 네이밍 규칙을 준수하지 않는 이름, 즉 자바스크립트에서 사용 가능한 유효한 이름이 아니면 반드시 대괄호 표기법을 사용해야 하지만 **프로퍼티 키가 숫자로 이뤄진 경우 따옴표를 생략할 수 있다.**

**<span style=color:red>`person.last-name`의 실행 결과가 Node.js 환경에서 "ReferenceError: name is not defined" 이고 브라우저에선 `NaN`인 이유는?</span>**

1. `person.last-name`을 실행할 때 자바스크립트 엔진은 먼저 `person.last`를 평가한다. `person`객체에는 프로퍼티 키가 `last`인 프로퍼티가 없기 때문에 `person.last`는 `undefined`로 평가된다.
2. 따라서 `person.last-name`은 `undefined-name`과 같다. 
3. 다음으로 자바스크립트 엔진은 `name`이라는 식별자를 찾는다. 이때 `name`은 프로퍼티 키가 아니라 식별자로 해석된다.
4. `Node.js`환경에서는 어디에도 `name`이라는 식별자 선언이 없으므로 "ReferenceError: name is not defined"이라는 에러가 발생하지만 **브라우저 환경에서는 `name`이라는 전역 변수(전역 객체 `window`의 프로퍼티)가 암묵적으로 존재한다.**
5. 전역 변수 `name`은 `window`의 이름을 가리키며, 기본값은 빈 문자열이다. 따라서 `person.last-name`은 `undefined - ''`과 같으므로 `NaN`이 된다.



## 프로퍼티 값 갱신

이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신된다.

```javascript
var person = {
    name : 'Cho'
};
// person 객체에 name 프로퍼티가 존재하므로 name 프로퍼티의 값이 갱신된다.
person.name = 'Kim';

console.log(person); // {name : "Kim"}
```



## 프로퍼티 동적 생성

존재하지 않는 프로퍼티에 값을 할당하면 프로퍼티가 동적으로 생성되어 추가되고 프로퍼티 값이 할당된다.

```javascript
var person = {
    name : 'Cho'
};

person.age = 28;
console.log(person); //{name : 'Cho', age : 28}
```



## 프로퍼티 삭제

delete 연산자는 객체의 프로퍼티를 삭제한다. 이때 delete 연산자의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야 한다. 만약 존재하지 않는 프로퍼티를 삭제하면 아무런 에러 없이 무시된다.

```javascript
var person = {
    name : 'Cho'
};

// 프로퍼티 동적 생성
person.age = 28;

delete person.age;
delete person.adderess; //person 객체에 address 프로퍼티가 존재하지 않는다. 따라서 삭제할 수 없다. 이 때 에러가 발생하지 않는다.

console.log(person); // {name : 'Cho'}
```



## ES6에서 추가된 객체 리터럴의 기능

### 프로퍼티 축약 표현

```javascript
// ES5
var x = 1, y = 2;

var obj = {
    x: x,
    y: y
};
console.log(obj); // {x:1, y:2}

//ES6
let x = 1, y = 2;
const obj = { x, y };
console.log(obj); // {x:1, y:2}

```

ES6에서는 프로퍼티 값으로 변수를 사용하는 경우 변수 이름과 프로퍼티 키가 동일한 이름일 때, 프로퍼티 키를 생략(property shorthand)할 수 있다.



### 메서드 축약 표현

```javascript
// ES5
var obj = {
    name: 'Cho',
    sayHi: function(){
        console.log('Hi!' + this.name);
    }
};

obj.sayHi();
```

ES6에서는 메서드를 정의할 떄, `function`키워드를 생략한 축약 표현을 사용할 수 있다.

```javascript
// ES6
const obj = {
    name: 'Cho',
    sayHi(){
        console.log('Hi! ' + this.name);
    }
};

obj.sayHi();
```

