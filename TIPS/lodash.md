# lodash

<img src="https://github.com/cjy0019/TIL/blob/master/images/Lodash.png?raw=true" width="40%">

## lodash 란?

- lodash는 자바스크립트 유틸리티 라이브러리이다.
- 유틸리티 라이브러리로 array, collection, date, number, object 등이 있으며, 데이터를 쉽게 다룰 수 있도록 도와준다.
- 특히, 자바스크립트에서 배열 안의 객체들의 값을 핸들링할때 유용하다.



## cloneDeep

객체 핸들링 중에서 깊은 복사에 관한 라이브러리이다. 일반적으로 객체를 복사할 때 다음과 같이 코딩한다.

```javascript
// 얕은 복사
const original = { a: { b: 2 } };

const clone = {...original};
```

**하지만 original 객체의 프로퍼티인 a는 또 다른 객체의 참조값(reference)을 저장하고 있다.** 따라서 얕은복사가 이루어진 것이다. 중복된 객체까지 복사하려면 다음과 같이 코딩한다.

```javascript
// 깊은 복사
const original = { a: { b : 2}};

const clone = {...original, a : {...original.a}};
```

original 객체를 풀고 그 안에서 a의 프로퍼티인 중복 객체를 풀어서 값을 덮어 씌우는 방식이다.

하지만 한번만 중첩이 되어 있는 경우, 간단하게 깊은 복사를 할 수 있지만 중첩이 여러번되어 있는 경우 값을 다루기 매우 번거롭다. 재귀를 사용하여 구현할 수도 있지만 lodash 라이브러리를 사용하면 간단하게 깊은 복사를 할 수 있다.

```javascript
const original = {
  a: { b: 2 },
  c: {
    d: 3,
    e: {
      f: {
        g: 10,
      },
    },
  },
};
// ??
```



## 설치

설치는 매우 간단하다. npm을 통해 설치 해준다.

```bash
npm i lodash
```

```javascript
import _ from 'lodash';

// common js에서는 다음과 같이 사용한다.
// var loDash = require('lodash');

const original = {
  a: { b: 2 },
  c: {
    d: 3,
    e: {
      f: {
        g: 10,
      },
    },
  },
};

let copy = _.cloneDeep(original);
copy.c.e.f.g = 100;
console.log(original.c.e.f.g); //10
```

다음과 같이 사용하면 copy에 깊은 복사가 완료된  값이 저장된 것을 확인할 수 있다.



## Error

<img src="https://github.com/cjy0019/TIL/blob/master/images/lodash_error.PNG?raw=true" width="60%">

`package.json`의 “type” 필드에 별도의 값이 없거나 “commonjs”로 설정되어 있으면 기본 모듈 처리 방식이 require를 사용하는 commonjs 방식으로 설정되기 때문에 import 부분에서 에러가 발생했던 것이다. 

> require을 사용하면 동적으로 모듈을 불러올 수 있지만, 불필요한 코드들까지 불러오기 때문에 실제로 어떤 코드가 사용되었는지 명확히 알 수가 없다.

따라서 ES2015의 import 문을 사용하기 위해서는 다음과 같이 간단한 설정을 해주면된다.

<img src="https://github.com/cjy0019/TIL/blob/master/images/solove_lodash.PNG?raw=true" width="50%">

"type" 필드의 값을 "module"로 바꿔준다.



[공식 문서](https://lodash.com/docs/4.17.15)

