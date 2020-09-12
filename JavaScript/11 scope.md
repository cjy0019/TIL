# 스코프

## 스코프란?

```javascript
function add(x,y){
    // 매개 변수는 함수 몸체 내부에서만 참조할 수 있다
    // 매개변수의 스코프는 함수 몸체 내부다
    console.log(x,y);
    return x+y;
}

add(2,5);

console.log(x,y); // ReferenceError
```

- 함수의 매개변수는 함수 몸체 내부에서만 참조할 수 있고 함수 몸체 외부에서는 참조할 수 없다고 한다.



```javascript
var var1 = 1; // 코드의 가장 바깥 영역에서 선언한 변수

if(true){
	var var2 = 2;
	if(true){
		var var3 = 3;
	}
}
function foo(){
    var var4 = 4; //함수 내에서 선언한 변수
    
    function bar(){
        var var5 =5;
    }
}

console.log(var1); // 1
console.log(var2); // 2
console.log(var3); // 3
console.log(var4); // ReferenceError
console.log(var5); // ReferenceError
```

- 변수는 자신이 선언된 위치에 의해 자신이 유효한 범위, 즉 다른 코드가 변수 자신을 참조할 수 있는 범위가 결정된다.
- 즉, **모든 식별자(변수 이름, 함수 이름, 클래스 이름)는 자신이 선언된 위치에 의해 다른 코드가 식별자 자신을 참조할 수 있는 유효범위가 결정된다.**
- 이를 스코프라 한다.



```javascript
var x = 'global';

function foo(){
    var x = 'local';
    console.log(x); // 1
}

foo();

console.log(x); // 2
```

- 코드의 가장 바깥 영역과 foo 함수 내부에 같은 이름을 갖는 변수 x를 선언했고 1과 2에서 x 변수를 참조한다.
- 이 때 자바스크립트 엔진은 어떤 변수를 참조해야 할 것인가를 결정한다.
- 자바스크립트 엔진은 스코프를 통해 어떤 변수를 참조해야 할지 결정한다.
- **따라서 스코프란 자바스크립트 엔진이 식별자를 검색할 때 사용하는 규칙이라고도 할 수 있다.**

<img src="https://poiemaweb.com/assets/fs-images/13-1.png" alt="img" style="zoom:50%;" />

- 만약 스코프라는 개념이 없다면 같은 이름을 갖는 변수는 충돌을 일으키므로 프로그램 전체에서 하나밖에 사용할 수 없다.

```javascript
function foo(){
    var x = 1;
    // var 키워드로 선언된 변수는 같은 스코프 내에서 중복 선언을 허용한다.
    // 아래 변수 선언문은 자바스크립트 엔진에 의해 var 키워드가 없는 것처럼 동작한다.
    var y = 2;
    console.log(x); // 2
}
foo();
```

하지만 `let`이나 `const`키워드로 선언된 변수는 같은 스코프 내에서 중복 선언을 허용하지 않는다.

```javascript
function bar(){
    let x = 1;
    
    let x = 2; // SyntaxError : Identifier 'x' has already been declared
}

bar();
```



## 스코프의 종류

코드는 전역(global)과 지역(local)으로 구분할 수 있다.

| 구분 | 설명                  | 스코프      | 변수      |
| ---- | --------------------- | ----------- | --------- |
| 전역 | 코드의 가장 바깥 영역 | 전역 스코프 | 전역 변수 |
| 지역 | 함수 몸체 내부        | 지역 스코프 | 지역 변수 |

### 전역과 전역 스코프

![img](https://poiemaweb.com/assets/fs-images/13-2.png)

- **전역**이란 코드의 가장 바깥 영역을 말한다.
- 전역은 전역 스코프를 만든다.
- 전역에 변수를 선언하면 전역 스코프를 갖는 전역 변수가 된다. 즉, 어디에서든지 참조할 수 있다.



### 지역과 지역 스코프

- 지역이란 **함수 몸체 내부**를 말한다. 
- 지역은 지역 스코프를 만든다.
- 지역에 변수를 선언하면 지역 스코프를 갖는 지역 변수가 된다.
- 지역 변수는 자신이 선언된 지역과 하위 지역(중첩 함수)에서만 참조할 수 있다.



## 스코프 체인

- 함수는 중첩될 수 있으므로 함수의 지역 스코프도 중첩될 수 있다.
- 중첩 함수의 지역 스코프는 중첩함수를 포함하는 외부 함수의 지역 스코프와 계층적 구조를 갖게 된다.
- 이 때 외부 함수의 지역 스코프를 중첩함수의 상위 스코프라고 한다.

<img src="https://poiemaweb.com/assets/fs-images/13-3.png" alt="img" style="zoom:50%;" />

