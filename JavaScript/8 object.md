# 객체 리터럴

## 객체란?

자바스크립트는 **객체(object)**기반의 프로그래밍 언어이며, 자바스크립트를 구성하는 거의 '모든 것'이 객체다 원시 값을 제외한 나머지(함수, 배열, 정규표현식 등) 모두 객체다

원시 타입 - 단 하나의 값만을 나타냄
객체 타입 - 다양한 값(원시값 또는 다른 객체)을 하나의 구성한 복합적인 *자료구조다*

#### &#9989; 원시 타입의 값은 변경 불가능한 값이지만 객체 타입의 값은 변경 가능한 값이다

 <img src="https://poiemaweb.com/assets/fs-images/10-1.png" style="zoom: 50%;" />

객체는 0개 이상의 프로퍼티로 구성된 집합이고, *키(key)와 값(value)으로 구성된다.
**함수도 프로퍼티 값으로 활용할 수 있는데 프로퍼티 값이 함수일 경우 일반 함수와 구분하기 위해 메서드(method)라 부른다**

<img src="https://poiemaweb.com/assets/fs-images/10-2.png" style="zoom: 33%;" />

- 프로퍼티: 객체의 상태를 나타내는 값(data)
- 메서드 : 프로퍼티를 참조하고 조작할 수 있는 동작(behavior)

<span style=color:pink>자바스크립트의 객체는 함수와 밀접한 관계를 가진다. 함수로 객체를 생성하기도 하며 함수 자체가 객체이기도 하다. </span>



## 객체 리터럴에 의한 객체 생성

자바 같은 클래스 기반 객체지향 언어는 클래스를 사전에 정의하고 필요한 시점에 new 연산자와 함께 생성자를 호출하여 인스터스를 생성하는 방식으로 객체를 생성한다.

#### 인스턴스란(instance)?

클래스에 의해 생성되어 메모리에 저장된 실체를 말한다. 객체지향 프로그래밍에서 객체는 클래스와 인스턴스를 포함한 개념이다. 클래스는 인스턴스를 생성하기 위한 템플릿의 역할을 한다.

*자바스크립트는 프로토타입 기반 객체지향 언어로서 다양한 객체 생성 방법을 지원한다*

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

## 프로퍼티

```javascript
var person = {
    name : 'Cho', // 프로퍼티 키는 name , 프로퍼티 값은 'cho'
    age : 28
};
```

객체는 프로퍼티들의 집합미여 프로퍼티는 키와 값으로 구성된다.

## 메서드

자바스크립트의 함수는 <span style=color:pink>일급 객체</span>다. 따라서 함수는 값으로 취급할 수 있기 때문에 프로퍼티 값으로 사용할 수 있다.

```javascript
var circle = {
    radius : 5,
    
    getDiameter: function(){
        return 2 * this.radius; //this는 circle을 가리킨다
    }
};

console.log(circle.getDiameter()); // 10
```

자바스크립트에서 함수를 값으로 취급할 수 있는 이유는? 일급 객체이기 때문에!



## 프로퍼티 접근

프로퍼티에 접근하는 방법은 두 가지다.

- 마침표 프로퍼티 접근 연산자(.)를 사용하는 **마침표 표기법(dot notation)**
- 대괄호 프로퍼티 접근 연산자([...])를 사용하는 **대괄호 표기법(bracket notation)**

```javascript
var person = {
    name: 'Cho'
};

console.log(person.name);
console.log(person['name']);
```

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



## 프로퍼티 값 갱신

이미 존재하는 프로퍼티에 값을 할당하면 프로퍼티 값이 갱신된다.

```javascript
var person = {
    name : 'Cho'
};

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

delete 연산자는 객체의 프로퍼티를 삭제한다. 이때 delete 연산자의 피연산자는 프로퍼티 값에 접근할 수 있는 표현식이어야 한다.

```javascript
var person = {
    name : 'Cho'
};

person.age = 28;

delete person.age;
delete person.adderess; //person 객체에 address 프로퍼티가 존재하지 않는다. 따라서 삭제할 수 없다.

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

// ES6
const obj = {
    name: 'Cho',
    sayHi(){
        console.log('Hi! ' + this.name);
    }
};

obj.sayHi();
```

