# 제어문(control flow statement)



## 블록문

block statement/ compound statement는 0개 이상의 문을 중괄호로 묶은 것으로 블록이라고 부른다
문의 끝에는 세미 콜론(;)을 붙이는 것이 일반적이다.
하지만 블록문은 자체 종결성(self closing)을 갖기 때문에 세미콜론을 붙이지 않는다.

```javascript
//블록문
{
    var foo = 10;
}

//제어문
var x = 1;
if(x<10){
    x++;
}

//함수 선언문
function sum(a,b){
    return a + b;
}
```

## 조건문

자바스크립트는 **if..else문과 switch문** 두 가지 조건문을 제공한다.

```javascript
if(조건식){
    // 조건식이 참이면 이 코드 블록이 실행
}
else{
    // 조건식이 거짓이면 이 코드 블록이 실행됨
}
```

*조건식을 추가하려면 else if 문을 사용한다*

ex)

```javascript
// x가 짝수이면 result 변수에 '짝수', 홀수이면 '홀수'를 할당한다
var x = 2;
var result;

if(x % 2){
    result = '홀수';
}
else{
    result = '짝수';
}

// 삼항 연산자로 교체
var x = 2;

var result = x % 2 ? '홀수' : '짝수';

// 경우의 수가 세가지 일 때
var num = 2;
var kind = num ? (num > 0 ? '양수' : '음수') : 영;
```



## switch 문

switch 문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮긴다.

```javascript
switch(표현식){
    case 표현식1:
        switch 문의 표현식과 표현식1이 일치하면 실행될 문;
        break;
    case 표현식2:
        switch 문의 표현식과 표현식2가 일치하면 실행될 문;
        break;
    default:
        switch 문의 표현식과 일치하는 표현식을 갖는 case 문이 없을 때 실행;
}
```



## 반복문(loop statement)

반복문은 조건식의 평가 결과가 참인 경우 코드 블록을 실행한다.

- for 문
- while 문
- do.. while 문



### for 문

for 문의 일반적인 형태

```javascript
for(변수 선언문 또는 할당문; 조건식; 증감식){
    조건식이 참인 경우 반복 실행될 문;
}
```

for 문의 변수 선언문, 조건식, 증감식은 모두 옵션이므로 반드시 사용할 필요는 없다.

```javascript
//무한루프
for(;;){...}
```

for 문 내에 for 문을 중첩해 사용할 수 있다. 이를 **중첩 for문**이라 한다.

```javascript
for(var i = 1; i <= 6; i++){
    for(var j = 1; j<=6; j++){
        if(i + j ===6) console.log(`[${i}, ${j}]`);
    }
} //주사위 두 개 던져 합이 6이 되는 경우
```



### while 문

while 문은 주어진 조건식의 평가 결과가 참이면 코드 블록을 계속해서 반복 실행
while 문은 반복 횟수가 불명확할 때 주로 사용

```javascript
var count = 0;

while(count < 3){
    console.log(count); // 0 1 2
    count++;
}
```

```javascript
while(true){...} //무한루프
```

```javascript
// 무한루프 탈출
var count = 0;

while(true){
    console.log(count);
    count++;
    if(count === 3) break;
}
```



### do...while 문

do...while 문은 코드 블록을 먼저 실행하고 조건식을 평가한다. 즉 코드 블록은 무조건 한번 이상 실행된다.

```javascript
var count = 0;

do{
    console.log(count);
    count++;
} while(count < 3); // 0 1 2 
```



## break 문

레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출하기 위해 사용된다.

*이 세가지 문의 코드 블록 외에 break를 사용하면 SntaxError가 발생*

```javascript
var string = 'Hello World.';
var search = 'l';
var index;

// 문자열은 유사배열이므로 for 문으로 순회할 수 있다.
for (var i = 0; i < string.length; i++) {
  // 문자열의 개별 문자가 'l'이면
  if (string[i] === search) {
    index = i;
    break; // 반복문을 탈출한다.
  }
}

console.log(index); // 2

// 참고로 String.prototype.indexOf 메서드를 사용해도 같은 동작을 한다.
console.log(string.indexOf(search)); // 2
```



## continue 문

continue 문은 반복문의 코드 블록 실행을 현 지점에서 중단하고 반복문의 증감식으로 실행을 이동시킨다.

```javascript
var string = 'Hello World.';
var search = 'l';
var count = 0;

// 문자열은 유사배열이므로 for 문으로 순회할 수 있다.
for (var i = 0; i < string.length; i++) {
  // 'l'이 아니면 현 지점에서 실행을 중단하고 반복문의 증감식으로 이동한다.
  if (string[i] !== search) continue;
  count++; // continue 문이 실행되면 이 문은 실행되지 않는다.
}

console.log(count); // 3

// String.prototype.match 메서드를 사용해도 같은 동작을 한다.
const regexp = new RegExp(search, 'g');
console.log(string.match(regexp).length); // 3
```

