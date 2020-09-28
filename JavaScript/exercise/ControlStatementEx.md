# exercise 문제



### Q1) 변수 x가 10보다 크고 20보다 작을 때 변수 x를 출력하는 조건식을 완성하시오.

```javascript
var x = 15;

// 변수 x가 10보다 크고 20보다 작을 때 변수 x를 출력하는 조건식을 완성하라.
if(...){
   console.log(x);
   }
```

**answer**

```javascript
var x = 15;

if (x > 10 && x < 20) {
  console.log(x);
}
```



### Q2) for문을 사용하여 0부터 10미만의 정수 중에서 짝수만을 작은 수부터 출력하시오.

```javascript
0
2
4
6
8
```

**answer**

```javascript
for (var i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    console.log(i);
  }
}
```



### Q3) for문을 사용하여 0부터 10미만의 정수 중에서 짝수만을 작은 수부터 문자열로 출력하시오.

```javascript
02468
```

**answer**

```javascript
var str = '';

for (var i = 0; i < 10; i++) {
  if (i % 2 === 0) {
    str += i;
  }
}
console.log(str);
```



### Q4) for문을 사용하여 0부터 10미만의 정수 중에서 홀수만을 큰수부터 출력하시오.

```javascript
9
7
5
3
1
```

**answer**

```javascript
for (var i = 9; i >= 0; i--) {
  if (i % 2 !== 0) {
    console.log(i);
  }
}
```



### Q5) while문을 사용하여 0부터 10미만의 정수 중에서 짝수만을 작은 수부터 출력하시오.

```javascript
0
2
4
6
8
```

**answer**

```javascript
var i = 0;

while (i < 10) {
  if (i % 2 === 0) {
    console.log(i);
  }
  i++;
}
```



### Q6) while문을 사용하여 0부터 10미만의 정수 중에서 홀수만을 큰 수부터 출력하시오.

```
9
7
5
3
1
```

**answer**

```javascript
var i = 9;

while (i >= 0) {
  if (i % 2 !== 0) {
    console.log(i);
  }
  i--;
}
```



### Q7) for문을 사용하여 0부터 10미만의 정수의 합을 출력하시오.

```javascript
45
```

**answer**

```javascript
var sum = 0;

for (var i = 0; i < 10; i++) {
  sum += i;
}
console.log(sum);
```



### Q8) 1부터 20미만의 정수 중에서 2또는 3의 배수가 아닌 수의 총합을 구하시오.

```javascript
73
```

**answer**

```javascript
var sum = 0;

for (i = 1; i < 20; i++) {
  if (i % 2 !== 0 && i % 3 !== 0) {
    sum += i;
  }
}
console.log(sum);
```



### Q9)  1부터 20미만의 정수 중에서 2또는 3의 배수인 수의 총합을 구하시오.

```javascript
117
```

**answer**

```javascript
var sum = 0;

for (var i = 0; i < 20; i++) {
  if (i % 2 === 0 || i % 3 === 0) {
    sum += i;
  }
}

console.log(sum);
```



### Q10) 두 개의 주사위를 던졌을 때, 눈의 합이 6이 되는 모든 경우의 수를 출력하시오.

```javascript
[1, 5]
[2, 4]
[3, 4]
[4, 2]
[5, 1]
```

**answer**

```javascript
var sum = 0;

for (var i = 1; i <= 6; i++) {
  for (var j = 1; j <= 6; j++) {
    if (i + j === 6) {
      console.log('[' + i + ',' + j + ']');
    }
  }
}
```



### Q11) 삼각형 출력하기 - pattern 1

- 다음을 참고하여 *(별)로 높이가 5인(var line = 5)삼각형을 문자열로 완성하시오. 개행문자('\n')을 사용하여 개행한다. 완성된 문자열의 마지막은 개행문자('n')로 끝나도 관계없음.

```code
// 높이(line)가 5
*
**
***
****
*****
```

**answer**

```javascript
var res = '';
var star = '*';

for (var line = 1; line <= 5; line++) {
  for (var j = 0; j < line; j++) {
    res += star;
  }
  res += '\n';
}
console.log(res);
```



### Q12) 삼각형 출력하기 - pattern 2

- 다음을 참고하여 *(별) 트리를 문자열로 완성하라. 개행문자('\n')를 사용하여 개행한다. 완성된 문자열의 마지막은 개행문자('\n')로 끝나도 관계없다.

```code
*****
 ****
  ***
   **
    *
```

**answer**

```javascript
var result = "";
var newLine = "\n";
var jump = " ";
var star = "*";

for (var line = 0; line < 5; line++) {
  for (var i = 0; i < line; i++) {
    result += jump;
  }
  for (var j = 5; j > line; j--) {
    result += star;
  }
  result += newLine;
}
console.log(result);

```





### Q13) 삼각형 출력하기 - pattern 3

- 다음을 참고하여 *(별)로 트리를 문자열로 완성하시오. 개행문자('\n')를 사용하여 개행한다. 완성된 문자열의 마지막은 개행문자('\n')로 끝나도 관계없다.

```code
*****
****
***
**
*
```

**answer**

```javascript
var result = "";
var star = "*";

for (var i = 0; i < 5; i++) {
  for (var j = 5; j > i; j--) {
    result += star;
  }
  result += "\n";
}

console.log(result);
```



### Q14) 삼각형 출력하기 - pattern 4

- 다음을 참고하여 *(별)로 트리를 문자열로 완성하라. 개행문자('\n')를 사용하여 개행한다. 완성된 문자열의 마지막은 개행문자('\n')로 끝나도 상관없다.

```code
    *
   **
  ***
 ****
*****
```

**answer**

```javascript
var result = "";
var jump = " ";
var star = "*";
var newLine = "\n";

for (var line = 1; line <= 5; line++) {
  for (var space = 5; space > line; space--) {
    result += jump;
  }

  for (var j = 0; j < line; j++) {
    result += star;
  }
  result += newLine;
}
console.log(result);

```



### Q15) 정삼각형 출력하기

```code
    *
   ***
  *****
 *******
*********
```

**answer**

```javascript
var result = "";
var jump = " ";
var star = "*";
var newLine = "\n";

for (var line = 0; line < 5; line++) {
  for (var space = 5; space > line; space--) {
    result += jump;
  }

  for (var j = 0; j < 2 * line + 1; j++) {
    result += star;
  }
  result += newLine;
}

console.log(result);

```



### Q16) 역정삼각형 출력하기

```code
*********
 *******
  *****
   ***
    *
```

**answer**

```javascript
var result = "";
var jump = " ";
var star = "*";
var newLine = "\n";

for (var line = 0; line < 5; line++) {
  for (var space = 0; space < line; space++) {
    result += jump;
  }

  for (var print = 10; print > line * 2 + 1; print--) {
    result += star;
  }
  result += newLine;
}

console.log(result);

```

