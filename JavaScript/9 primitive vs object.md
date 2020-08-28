# 원시값 VS 객체

**원시타입 : 숫자, 문자열, 불리언, null, undefined, 심벌**

- 변경 불가능한 값(immutable value)이다.
- 원시값을 변수에 할당하면 변수에 할당하면 실제 값이 저장된다.
- 원시값을 갖는 변수를 다른 변수에 할당하면 원본의 원시값이 복사되어 전달된다. - pass by value

**객체타입**

- 변경 가능한 값(mutable)이다.
- 객체를 변수에 할당하면 변수에는 참조값이 저장된다.
- 객체를 가리키는 변수를 다른 변수에 할당하면 원본의 참조값이 복사되어 전달된다. - pass by reference

## 원시값

### 변경 불가능한 값

- 한 번 생성된 원시값은 읽기 전용(read only) 값이다. 
- **변경 불가능하다는 것은 변수가 아니라 값에 대한 진술이다.**
- 즉, 원시값 자체를 변경할 수 없다는 것이지 변수 값을 변경할 수 없다는 것이 아니다. 변수는 언제든지 재할당을 통해 값 교체가 가능하다.
- 반대로 **상수는 재할당이 금지된 변수를 말한다.**

```javascript
const a = {};

a.b = 1;
console.log(a); // {b : 1}
// const 키워드를 사용해 선언한 변수에 할당한 객체는 변경할 수 있다.
```

<span style=color:pink>이러한 원시값의 특성은 데이터의 신뢰성을 보장한다</span>



![img](https://poiemaweb.com/assets/fs-images/11-1.png)

***원시값을 할당한 변수에 새로운 원시값을 재할당하면 메모리 공간에 저장되어 있는 원시값을 변경하는 것이 아니라 새로운 메모리 공간을 확보하고 재할당한 원시값을 저장한 후, 변수는 새로운 원시값을 가리킨다***

![img](https://poiemaweb.com/assets/fs-images/11-2.png)

### 문자열과 불변성

ECMAScript 사양

- 문자열 타입 : 2byte
- 숫자 타입 : 8byte
- 이외의 원시 타입은 크기를 명확히 정하지 않아서 브라우저 제조사의 구현에 따라 원시 타입의 크기는 다를 수 있다.

ex) 숫자는 값 1도, 100000도 동일한 8바이트가 필요하지만 문자열의 경우 1개의 문자는 2바이트 10개의 문자는 20바이트가 필요하다.

```javascript
var str = 'hello';
str = 'world';
```

첫 번째 문이 실행되면 문자열 'Hello'가 생성되고 식별자 str은 문자열 'Hello'가 저장된 메모리 공간의 첫 번째 메모리 셀 주소를 가리킨다.
두 번째 문이 실행되면 이전에 생성된 문자열 'Hello'를 수정하는 것이 아니라 새로운 문자열 'world'를 메모리에 생성하고 식별자 str은 이것을 가리킨다.

**유사 배열 객체**

유사 배열 객체란 마치 배열처럼 인덱스로 프로퍼티 값에 접근할 수 있고 length 프로퍼티를 갖는 객체를 말한다

```javascript
var str = 'string';
// 문자열은 유사 배열이므로 배열과 유사하게 인덱스를 사용해 각 문자에 접근할 수 있다.

str[0] = 'S';

console.log(str); // string
```

`str[0] = 'S'`처럼 이미 생성된 문자열의 일부 문자를 변경해도 반영되지 않는다. 문자열은 변경 불가능한 값이기 때문이다. 이처럼 한 번 생성된 문자열은 읽기 전용 값으로서 변경할 수 없다. 원시값은 어떤 일이 있어도 불변한다. 따라서 예기치 못한 변경으로부터 자유롭다. 이는 데이터의 신뢰성을 보장한다.

그러나 변수에 새로운 문자열을 재할당하는 것은 물론 가능하다. 이는 기존 문자열을 변경하는 것이 아니라 새로운 문자열을 새롭게 할당하는 것이기 때문이다.

## 값에 의한 전달

```javascript
var score = 80;
var copy = score; // copy 변수에는 score 변수의 값 80이 복사되어 할당된다.

console.log(score); // 80
console.log(copy);  // 80

score = 100;

console.log(score); // 100
console.log(copy);  // 80

console.log(score, copy); // 80  80
console.log(score === copy); // true
```

copy의 값은 80일 것이다

이처럼 변수에 원시값을 갖는 변수를 할당하면 할당받는 변수(copy)에는 할당되는 변수(score)의 값이 <u>복사되어</u>전달 된다.
이를 **값에 의한 전달(Pass by value)**이라 한다.

![img](https://poiemaweb.com/assets/fs-images/11-3.png)

score 변수와 copy 변수는 숫자 80을 갖는다는 점에서 동일하다.
but **score 변수와 copy 변수의 값은 80은 다른 메모리 공간에 저장된 별개의 값이다**

## 객체

- 객체는 프로퍼티의 개수가 정해져 있지 않으며, 동적으로 추가되고 삭제할 수 있다. **객체는 원시값과 같이 확보해야 할 메모리 공간의 크기를 사전에 정해 둘 수 없다**

### 자바스크립트 객체의 관리 방식

자바스크립트 객체는 프로퍼티 키를 인덱스로 사용하는 <span style=color:pink>해시 테이블</span>이라고 생각할 수 있다. 해시테이블과 유사하지만 높은 성능을 위해 더 나은 방법으로 객체를 구현한다.

<img src="https://poiemaweb.com/assets/fs-images/11-6.png" alt="img" style="zoom:33%;" />

자바스크립트는 클래스 없이 객체를 생성할 수 있고 객체가 생성된 이후라도 동적으로 프로퍼티와 메서드를 추가할 수 있다. 이는 편리하지만 성능면에서 클래스 기반 객체보다 떨어지는 것이 사실이다.

**따라서 V8 자바스크립트 엔진에서는 프로퍼티에 접근하기 위해 동적 탐색 대신 <span style=color:pink>히든 클래스(hidden class)</span>라는 방식을 사용해 객체의 프로퍼티에 접근하는 정도의 성능을 보장한다**



### 변경 가능한 값

객체 타입의 값, 즉 객체는 변경 가능한 값이다.

```javascript
var person = {
    name : 'Cho'
};
```

객체를 할당한 변수가 기억하는 메모리 주소를 통해 메모리 공간에 접근하면 **참조값(reference value)**에 접근할 수 있다. <u>참조값은 생성된 객체가 저장된 메모리 공간의 주소, 그 자체다</u>

<img src="https://poiemaweb.com/assets/fs-images/11-7.png" alt="img" style="zoom:50%;" />

```javascript
var person = {
    name:'Cho'
};

console.log(person);
```

- 일반적으로 원시값을 할당한 변수의 경우 "변수는 ~값을 갖는다" 라고 표현한다.
- 하지만 객체를 할당한 변수의 경우 '변수는 객체를 참조하고 있다', '변수는 객체를 가리키고 있다' 라고 표현한다.
- 즉, 위의 예제에서 person 변수는 객체 `{name : 'Cho'}`를 가리키고(참조하고) 있다.

#### 원시값처럼 이전 값을 복사해서 새롭게 생성한다면 신뢰성은 확보되지만 메모리의 효율적 소비가 어렵고 성능이 나빠진다. 따라서 메모리를 효율적으로 사용하기 위해, 변경 가능한 값으로 설계되어 있다.



## 얕은 복사(shallow copy) vs 깊은 복사(deep copy)

객체를 프로퍼티 값으로 갖는 경우 얕은 복사는 한 단계까지만 복사하는 것을 말하고 깊은 복사는 객체에 중첩되어 있는 객체까지 모두 복사하는 것을 말한다.

*이해하고 다시 정리하자*



## 참조에 의한 전달

```javascript
var person = {
    name : 'Cho'
};

var copy = person;
```

객체를 가리키는 변수(person)을 다른변수에 할당하면 원본의 참조값이 복사되어 전달된다. 이를 **참조에 의한 전달**이라고 한다.

<img src="https://poiemaweb.com/assets/fs-images/11-9.png" alt="img" style="zoom:33%;" />

이처럼 person과 copy는 저장된 메모리 주소는 다르지만 동일한 참조값을 갖는다. **즉, 두 개의 식별자가 하나의 객체를 공유한다는 것을 의미한다**

```javascript
var person = {
  name: 'Lee'
};

// 참조값을 복사(얕은 복사). copy와 person은 동일한 참조값을 갖는다.
var copy = person;

// copy와 person은 동일한 객체를 참조한다.
console.log(copy === person); // true

// copy를 통해 객체를 변경한다.
copy.name = 'Kim';

// person을 통해 객체를 변경한다.
person.address = 'Seoul';

// copy와 person은 동일한 객체를 가리킨다.
// 따라서 어느 한쪽에서 객체를 변경하면 서로 영향을 주고 받는다.
console.log(person); // {name: "Kim", address: "Seoul"}
console.log(copy);   // {name: "Kim", address: "Seoul"}
```

