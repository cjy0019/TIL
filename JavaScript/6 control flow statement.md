# 제어문(control flow statement)

- 제어문(control flow statement)은 주어진 조건에 따라 코드  블록을 실행(조건문)하거나 반복 실행(반복문)할 때 사용한다.
- 일반적을 코드는 위에서 아래 방향으로 순차적으로 실행되지만, 제어문을 사용하면 코드의 실행 흐름을 인위적으로 제어할 수 있다.



## 블록문(코드 블록)

블록문(block statement/ compound statement)은 0개 이상(있을수도 없을수도) 의 문을 중괄호로 묶은 것으로 블록이라고 부르고 자바스크립트는 블록문을 하나의 실행 단위로 취급한다.
문의 끝에는 세미 콜론(;)을 붙이는 것이 일반적이다.
**하지만 블록문은 자체 종결성(self closing)을 갖기 때문에 세미콜론을 붙이지 않는다.**

```javascript
//블록문
{
    var foo = 10;
    console.log(foo);
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

### if...else 문

if...else 문은 주어진 조건식(불리언 값으로 평가될 수 있는 표현식의 평가 결과, 즉 논리적 참 또는 거짓에 따라 실행할 코드 블록을 결정한다. 조건식의 평가 결과가 `true`일 경우 if 문의 코드 블록이 실행되고 `false`일 경우 `else`문의 코드 블록이 실행된다.)

```javascript
if(조건식){
    // 조건식이 참이면 이 코드 블록이 실행
}
else{
    // 조건식이 거짓이면 이 코드 블록이 실행됨
}
```

if 문의 조건식은 불리언 값으로 평가되어야 한다. 만약 if 문의 조건식이 불리언 값이 아닌 값으로 평가되면 자바스크립트 엔진에 의해 암묵적으로 불리언 값으로 강제 변환되어 실행할 코드 블록을 결정한다.

*조건식을 추가하려면 else if 문을 사용한다*

ex) 대부분의 `if...else`문은 삼항 조건 연산자로 바꿔 쓸 수 있다.

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

console.log(result); // 짝수
```

**삼항 조건 연산자로 교체**

```javascript
// 삼항 연산자로 교체
var x = 2;

var result = x % 2 ? '홀수' : '짝수';

// 경우의 수가 세가지 일 때
var num = 2;
var kind = num ? (num > 0 ? '양수' : '음수') : 영; // 0이 아닌 경우는 모두 true로 계산된다
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

예제) 월을 평가해보기

```javascript
var month = 11;
var monthName;

switch (month) {
  case 1: monthName = 'January';
  case 2: monthName = 'February';
  case 3: monthName = 'March';
  case 4: monthName = 'April';
  case 5: monthName = 'May';
  case 6: monthName = 'June';
  case 7: monthName = 'July';
  case 8: monthName = 'August';
  case 9: monthName = 'September';
  case 10: monthName = 'October';
  case 11: monthName = 'November';
  case 12: monthName = 'December';
  default: monthName = 'Invalid month';
}

console.log(monthName); // Invalid month
```

- `November`가 출력되지 않고 `Invalid month`가 출력된다. 이는 `switch`문의 표현식의 평가 결과와 일치하는 `case`문으로 실행 흐름이 이동하여 문을 실행한 것은 맞지만 문을 실행한 후에 `switch`문을 탈출하지 않고 `switch`문이 끝날 때까지 이후의 모든 `case`문과 `default`문을 실행했기 때문에 발생한 현상이다.
- 이를 **폴스루(fall through)**라고 한다. 다시 말해, 'November'가 할당된 후 'December' 'Invalid month'가 재할당된 것이다.

**수정**

```javascript
// 월을 영어로 변환한다. (11 → 'November')
var month = 11;
var monthName;

switch (month) {
  case 1: monthName = 'January';
    break;
  case 2: monthName = 'February';
    break;
  case 3: monthName = 'March';
    break;
  case 4: monthName = 'April';
    break;
  case 5: monthName = 'May';
    break;
  case 6: monthName = 'June';
    break;
  case 7: monthName = 'July';
    break;
  case 8: monthName = 'August';
    break;
  case 9: monthName = 'September';
    break;
  case 10: monthName = 'October';
    break;
  case 11: monthName = 'November';
    break;
  case 12: monthName = 'December';
    break;
  default: monthName = 'Invalid month';
}

console.log(monthName); // November
```

- `default`문에는 `break`를 생략하는 것이 일반적이다.
- `default`문은 switch 문의 맨 마지막에 위치하므로 `default`문의 실행이 종료되면 `switch`문을 빠져나간다. 따라서 별도의 `break`문이 필요없다.



## 반복문(loop statement)

반복문은 조건식의 평가 결과가 참인 경우 코드 블록을 실행한다.

- for 문
- while 문
- do.. while 문



### for 문

for 문의 일반적인 형태

```pseudocode
for(변수 선언문 또는 할당문; 조건식; 증감식){
    조건식이 참인 경우 반복 실행될 문;
}
```

for 문의 변수 선언문, 조건식, 증감식은 모두 옵션이므로 반드시 사용할 필요는 없다.

```javascript
//무한루프
for(;;){...}
```

<img src="https://poiemaweb.com/assets/fs-images/8-1.png" style="zoom: 33%;" />

1. `for`문을 실행하면 맨 먼저 변수 선언문 `var i = 0`이 실행된다. 변수 선언문은 단 한번만 실행된다.
2. 변수 선언문의 실행이 종료되면 조건식이 실행된다. 현재 `i`의 변수의 값은 0이므로 조건식의 평가 결과는 `true`이다.
3. 조건식의 평가 결과가 `true`이므로 코드 블록이 실행된다. 증감문으로 실행 흐름이 이동하는 것이 아니라 코드 블록으로 흐름이 이동하는 것에 주의한다.
4. 코드 블록의 실행이 종료되면 증감식 `i++`가 실행되어 i변수의 값은 1이 된다.
5. 증감식 실행이 종료되면 다시 조건식이 실행된다.
6. 조건식의 평가 결과가 `true`이므로 코드 블록이 다시 실행된다.
7. 코드 블록의 실행이 종료되면 증감식 `i++`가 실행되어 i변수의 값은 2가 된다.
8. 증감식 실행이 종료되면 다시 조건식이 실행되고 현재 `i`의 변수의 값이 2이므로 조건식 평가는 `false`가 된다.



#### for 문 내에 for 문을 중첩해 사용할 수 있다. 이를 **중첩 for문**이라 한다.

```javascript
for(var i = 1; i <= 6; i++){
    for(var j = 1; j<=6; j++){
        if(i + j ===6) console.log(`[${i}, ${j}]`);
    }
} //주사위 두 개 던져 합이 6이 되는 경우
```



### while 문

while 문은 주어진 조건식의 평가 결과가 참이면 코드 블록을 계속해서 반복 실행한다. `for`문은 반복 횟수가 명확할 때 주로 사용하고 `while`문은 반복 횟수가 불명확할 때 주로 사용한다.

`while`문은 조건문의 평가 결과가 거짓이 되면 코드 블록을 실행하지 않고 종료한다. 조건식의 평가 결과가 불리언 값이 아니면 불리언 값으로 강제 변환하여 논리적 참, 거짓을 구별한다.

```javascript
var count = 0;

while(count < 3){
    console.log(count); // 0 1 2
    count++;
}
```

```javascript
// 무한 루프
while(true){...} 
```

무한 루프를 탈출하기 위해서 탈출 조건을 만들고 `break`문으로 코드 블록을 탈출한다.

```javascript
// 무한루프 탈출
var count = 0;

while(true){
    console.log(count);
    count++;
    if(count === 3) break;
} // 0 1 2
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

`break`문은 레이블 문, 반복문 또는 switch 문의 코드 블록을 탈출하기 위해 사용된다.

*이 세가지 문의 코드 블록 외에 break를 사용하면 SntaxError가 발생*

```javascript
if (true) {
  break; // Uncaught SyntaxError: Illegal break statement
}
```

레이블 문(label statement)이란 식별자가 붙은 문을 말한다.

```javascript
// foo라는 레이블 식별자가 붙은 레이블 문
foo : console.log('foo');
```

```javascript
// foo 라는 식별자가 붙은 레이블 블록문
foo: {
  console.log(1);
  break foo;
  console.log(2);
}
console.log("done!"); 

// 1
// done!
```

- 중첩된 `for`문의 내부 `for`문에서 `break`문을 실행하면 내부 `for`문을 탈출하여 외부 `for`문으로 진입한다. 이 때 내부 `for`문이 아닌 외부`for`문을 탈출하려면 레이블 문을 사용한다.

```javascript
// outer라는 식별자가 붙은 레이블 for 문
outer: for(var i = 0; i < 3; i++){
    for(var j = 0; j < 3; j++){
        // i + j === 3 이면 outer라는 식별자가 붙은 레이블 for 문을 탈출한다.
        if(i + j === 3) break outer;
        console.log(`inner [${i}, ${j}]`);
    }
}
console.log("Done!");

inner [0, 0]
inner [0, 1]
inner [0, 2]
inner [1, 0]
inner [1, 1]
Done!
```

- 레이블 문은 중첩된 `for`문 외부로 탈출할 때 유용하지만 그 밖의 경우에는 일반적으로 권장하지 않는다.
- 레이블 문을 사용하면 프로그램의 흐름이 복잡해져서 가독성이 나빠지고 오류를 발생시킬 가능성이 높아지기 때문이다.

예제) 특정 문자의 인덱스(위치)를 검색하는 프로그램

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

- continue 문은 반복문의 코드 블록 실행을 <u>현 지점에서 중단</u>하고 <span style = color:red>반복문의 증감식</span>으로 실행을 이동시킨다.
- `break`문처럼 반복문을 탈출하지 않는다.

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
