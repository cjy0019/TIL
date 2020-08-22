# 타입 변환과 단축 평가

값의 타입은 개발자의 의도에 따라 다른 타입으로 변환할 수 있다.
개발자가 의도적으로 값의 타입을 변환하는 것을 **명시적 타입 변환(explicit coercion)** 또는 **타입 캐스팅(type casting)**이라 한다.

```javascript
var x = 10;

//명시적 타입 변환
var str = x.toString();
console.log(typeof str, str); //string 10

console.log(typeof x, x); // number 10
```

개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되는 것을 **암묵적 타입 변환(implicit coercion)** 또는 **타입 강제 변환(type coercion)**이라고 한다.

```javascript
var x = 10;

// 암묵적 타입 변환
var str = x + '';
console.log(typeof str, str); // string 10

console.log(typeof x, x); // number 10
```

명시적 타입 변환이나 암묵적 타입 변환이 기존 원시값을 직접 변경하는 것은 아니다. 기존 원시값을 이용해 다른 타입의 새로운 원시값을 생성하는 것이다.

## 암묵적 타입 변환

```javascript
'10' + 2 // 102

5 * '10' // 50
```

