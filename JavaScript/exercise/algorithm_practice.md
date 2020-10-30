# 알고리즘 연습(Level 1)



## 1. 짝수와 홀수

evenOrOdd 함수는 정수 num을 매개변수로 받는다. num은 1이상의 정수이며, num이 음수인 경우는 없다. num이 짝수일 경우 ‘Even’을 반환하고 홀수인 경우 ‘Odd’를 반환하도록 evenOrOdd 함수를 완성하라.

```javascript
// if문
function evenOrOdd(num) {
  if (num % 2 === 0) return "Even";
  else return "Odd";
}

// 3항 연산자
function evenOrOdd(num) {
  return num % 2 ? "Odd" : "Even";
}
console.log(evenOrOdd(2)); // Even
console.log(evenOrOdd(3)); // Odd
console.log(evenOrOdd(1000)); // Even
```



## 2. 1 ~ 10,000의 숫자 중 8이 등장하는 횟수 구하기(Google)

1부터 10,000까지 8이라는 숫자가 총 몇번 나오는가? 이를 구하는 함수를 완성하라.

단, 8이 포함되어 있는 숫자의 갯수를 카운팅 하는 것이 아니라 8이라는 숫자를 모두 카운팅 해야 한다. 예를 들어 8808은 3, 8888은 4로 카운팅 해야 한다.

(hint) 문자열 중 n번째에 있는 문자 : str.charAt(n) or str[n]

```javascript
// 문자열로 변환하여 문자열 '8'을 카운팅한다.
function getCount8() {
  let count = 0; // 8을 카운팅 하는 변수
    
  for (let i = 1; i < 10000; i++) { // 1 ~ 10000까지의 정수
    for (let j = 0; j < i.toString().length; j++) { 
        // 숫자 내에서 순회하는 변수
      if (i.toString().charAt(j) === "8") {
        count++;
      }
    }
  }
  return count;
}

console.log(getCount8()); // 4000
```



## 3. 문자열 다루기

alphaString46 함수는 문자열 s를 매개변수로 입력받는다. s의 길이가 4 ~ 6이고, 숫자로만 구성되어 있는지 확인하는 alphaString46 함수를 완성하라.

예를 들어 s가 ‘a234’이면 false를 리턴하고 ‘1234’라면 true를 리턴한다.

```javascript
function alphaString46(s) {
	// 풀이
}

console.log(alphaString46('1234')); // true
console.log(alphaString46('9014')); // true
console.log(alphaString46('723'));  // false
console.log(alphaString46('a234')); // false
console.log(alphaString46(''));     // false
console.log(alphaString46());       // false
```

```javascript
function alphaString46(s) {
  if (s !== "" && s !== undefined) {
    if (s.length >= 4 && s.length <= 6) {
      for (let i = 0; i < s.length; i++) {
        if (s.charCodeAt(i) >= 48 && s.charCodeAt(i) <= 57) return true;
        else return false;
      }
    } else return false;
  } else return false;
}
```



## 4. 문자열 내 p와 y의 개수

numPY함수는 대문자와 소문자가 섞여있는 문자열 s를 인수로 전달받는다. s에 존재하는 ‘p’의 개수와 ‘y’의 갯수를 비교해 같으면 true, 다르면 false를 리턴하도록 함수를 완성하라. 대소문자를 구별하지 않으며 ‘p’, ‘y’ 모두 하나도 없는 경우는 항상 true를 리턴한다.

예를 들어 s가 ‘pPoooyY’면 true를 리턴하고 ‘Pyy’라면 false를 리턴한다.

```javascript
function numPY(s) {
	// 풀이
}

console.log(numPY('pPoooyY')); // true
console.log(numPY('Pyy'));     // false
console.log(numPY('ab'));      // true
console.log(numPY(''));        // true
console.log(numPY());          // true
```

```javascript
function numPY(s) {
  let countP = 0,
    countY = 0;

  if (s === "" || s === undefined) return true;

  for (let i = 0; i < s.length; i++) {
    if (s[i] === "p" || s[i] === "P") countP++;
    else if (s[i] === "y" || s[i] === "Y") countY++;
  }
  if (countP === countY) return true;
  else return false;
}
```

