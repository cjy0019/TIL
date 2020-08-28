# ASCII vs Unicode



## ASCII Code(미국 정보교환 표준 부호)

- American Standard Code for Information Interchange 의 약자로 대표적인 문자 인코딩이다.
- 아스키는 **7비트 인코딩**으로 33개의 출력 불가능한 제어 문자들과 공백을 비롯한 95개의 출력 가능한 문자들로 총 128개로 이루어짐

- 아스키 코드(ASCII Table)는 0번부터 127번까지만 사용한다. 127번 이후 코드를 사용했던 적도 있었는데 이는 표준이 아니며 운영체제마다 다른 코드(문자)를 배치했기 때문에 호환이 되지 않습니다.
- 128 ~ 255 특수 문자, 0~127 자주쓰는 문자, 0~31 특수 제어 코드

<span style=color:red;font-size:20px;>왜 아스키 코드는 7비트만 사용할까?</span>

- 통신 에러 검출을 위한 비트를 **Parity Bit**라고 하는데 1비트를 <span style=color:pink>통신에러 검출을 위해 사용하기 때문</span>

<span style=color:red;font-size:20px;>패리비트 사용법?</span>

- 7개의 비트 중에서 1의 개수가 홀수이면 1, 짝수면 0을 붙이는 방식으로 전송 도중에 데이터가 변경되는 문제를 변경하기 위해서 사용되었다.

![](https://mblogthumb-phinf.pstatic.net/20160530_210/kimkwon429_1464589111496s786l_JPEG/ascii.jpg?type=w2)



## 문자열을 아스키 코드로 변환하기

### 예제 1) 'charCodeAt' 이라는 문자열의 'C'를 아스키 코드로 변환하시오.

```javascript
var str = "charCodeAt";

console.log("str.charCodeAt(4) : "+ str.charcodeAt(4));
// str.charCodeAt(4) : 67
```

### 예제2) 아스키 코드값이 123에 해당하는 문자를 출력하시오.

```javascript
var val = 123;

console.log("String.fromCharCodeAt(val) : "+ String.fromCharCodeAt(val));
// String.fromCharCode(val) : {
```

### 예제 3) 문자열 'ASCII' 를 출력하시오

```javascript
console.log(
  "String.fromCharCode(65,83,67,73,73) : " +
    String.fromCharCode(65, 83, 67, 73, 73)
);
// String.fromCharCode(65,83,67,73,73) : ASCII
```



## 유니코드(Unicode)

- 중국어, 한글은 표현할 수 있는 문자의 갯수가 영어보다 훨씬 많다
- 이를 아스키코드에 모두 담을 수 없어서 용량을 크게 확장한 2byte 의 유니코드가 등장함
- 2byte는 16비트로 2의16승(=65536)개 이므로 온 문자를 모두 담을 수 있을거라 생각했다.
- 그러나 고어, 아프리카 토속어 등을 모두 담으려 하다보니 이마저도 부족했다.

**숫자와 글자, 키 값이 1:1로 매핑된 형태의 코드이다**

![](https://t1.daumcdn.net/cfile/tistory/2140515058B9A83811)

한글 프로그램에서 볼 수 있는 유니코드 문자들 예시!

### 예제 1) '유니코드'라는 문자를 유니코드로 변환할 경우

```javascript
console.log("유".charCodeAt(0).toString(16)); 
console.log("니".charCodeAt(0).toString(16));
console.log("코".charCodeAt(0).toString(16));
console.log("드".charCodeAt(0).toString(16));
// c720
// b2c8
// cf54
// b4dc
```

### 예제2) unicode를 문자열로 변환하기

```javascript
console.log(String.fromCharCode(parseInt('\c720', 16)));
console.log(String.fromCharCode(parseInt('\b2c8', 16)));
console.log(String.fromCharCode(parseInt('\cf54', 16)));
console.log(String.fromCharCode(parseInt('\b4dc', 16)));

// 유
// 니
// 코
// 드
```

