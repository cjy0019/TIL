# 예제

## 1. 1 ~ 10,000의 숫자 중 8이 등장하는 횟수 구하기 (Google)

1부터 10,000까지 8이라는 숫자가 총 몇 번 나오는가? 
이를 구하는 함수를 완성하라.
단, 8이 포함되어 있는 숫자의 갯수를 카운팅 하는 것이 아니라 8이라는 숫자를 모두 카운팅 해야 한다. 

예를 들어 8808은 3, 8888은 4로 카운팅 해야 한다.
(hint) 문자열 중 n번째에 있는 문자 : `str.charAt(n) or str[n]`

```javascript
function getCount8 () {
    
}
console.log(getCount8()); // 4000
```

**Answer**

```javascript
let string = '';
for (let i = 1; i <= 10000; i++) {
  string += i;
}

function getCount8(string) {
  var count = 0;
  for (let i = 0; i < string.length; i++) {
    if (string[i] === '8') {
      count++;
    }
  }
  return count;
}

console.log(getCount8(string));
```



## 2. 이상한 문자 만들기

toWeirdCase함수는 문자열을 인수로 전달 받는다. 
문자열 s에 각 단어의 짝수번째 인덱스 문자는 대문자로, 홀수번째 인덱스 문자는 소문자로 바꾼 문자열을 리턴하도록 함수를 완성하라.

예를 들어 s가 ‘hello world’라면 첫 번째 단어는 ‘HeLlO’, 두 번째 단어는 ‘WoRlD’로 바꿔 ‘HeLlO WoRlD’를 리턴한다.

**주의) 문자열 전체의 짝/홀수 인덱스가 아니라 단어(공백을 기준)별로 짝/홀수 인덱스를 판단한다.**

```javascript
function toWeirdCase(s) {
    
}
console.log(toWeirdCase('hello world'));    // 'HeLlO WoRlD'
console.log(toWeirdCase('my name is lee')); // 'My NaMe Is LeE'
```

**Answer**

```javascript
function toWeirdCase(s) {
  let newString = ""; // 최종결과를 저장할 변수를 선언한다
  s = s.split(" "); // 단어의 기준이 공백이므로 문자열을 띄어쓰기(' ') 기준으로 하나의 배열로 만든다.

  for (let word = 0; word < s.length; word++) { // 단어를 돌기 위한 바깥 for문을 실행한다 
    for (let detail = 0; detail < s[word].length; detail++) { // 단어 내부에서 각각의 단어에 접근한다
      if (detail % 2 === 0) { // 단어 내부에서 각각의 인덱스가 짝수일 때
        newString += s[i][detail].toUpperCase();
      } else {
        newString += s[i][detail]; // 홀수일 땐 그대로 삽입해준다
      }
    }
    newString += " "; // 하나의 단어에 대한 변환이 끝나면 공백을 삽입해준다.
  }
  return newString;
}

console.log(toWeirdCase('hello world')); // HeLlO WoRlD 
console.log(toWeirdCase('my name is lee')); // My NaMe Is LeE 
```

