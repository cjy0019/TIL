# TypeScript

<p align="center"><img src="https://poiemaweb.com/img/typescript-logo.png" width="50%"></p>

## 1. Intro

초창기 자바스크립트는 웹페이지의 보조적인 기능을 수행하기 위해 한정적인 용도로 사용되었다. 이 시기에 대부분 로직은 주로 웹서버에서 실행되었고 브라우저(클라이언트)는 서버로부터 전달받은 HTML과 CSS를 렌더링하는 수준이었다.

HTML5가 등장하기 이전까지 웹 애플리케이션은 플래시, 실버라이트, 액티브엑스와 같은 플러그인에 의존하여 인터랙티브한 웹페이지를 구축해왔다. 그러다가 HTML5가 등장함으로써 **플러그인**에 의존하던 구축 방식은 자바스크립트로 대체되었다. 또한 AJAX의 활성화로 데스크탑 애플리케이션과 유사한 사용자 경험을 제공할 수 있는 **SPA(Single Page Application)**가 대세가 되었다.  이로써 과거 서버 측이 담당하던 업무의 많은 부분이 클라이언트 측으로 이동하게 되었고, 자바스크립트는 위상이 높아지게 되었다.

자바스크립트는 과거 웹페이지의 보조적인 기능을 수행하기 위해 한정적인 용도로 만들어졌기 때문에 장점과 단점을 가지고 있다. C나 Java와 같은 C-family 언어와는 구별되는 아래와 같은 특징이 있다.

- Prototype-based Object Oriented Language
- Scope와 this
- 동적 타입(dynamic typed) 언어 혹은 느슨한 타입(loosely typed) 언어

이와 같은 특성은 클래스 기반 객체지향 언어(Java, C++, C# 등)에 익숙한 개발자를 혼란스럽게 하며 코드가 복잡해질 수 있고 디버그와 테스트 공수가 증가하는 등의 문제를 일으킬 수 있다.

이같은 자바스크립트의 태생적 문제를 극복하고자 CoffeeScript, Dart, Haxe와 같은 **AltJS**(자바스크립트의 대체 언어)가 등장하였다.

TypeScript 또한 자바스크립트 대체 언어의 하나로써 **자바스크립트(ES5)의 Superset(상위확장)이다.** C#의 창시자인 덴마크 출신 소프트웨어 엔지니어 아네르스 하일스베르가 개발을 주도한 TypeScript는 Microsoft에서 2012년 발표한 오픈소스로, 정적 타이핑을 지원하고 ES6의 클래스, 모듈 등과 ES7의 Decorator등을 지원한다.



TypeScript는 ES5의 Superset이므로 기존의 자바스크립트 (ES5)문법을 그대로 사용할 수 있다. 또한, ES6의 새로운 기능들을 사용하기 위해 Babel과 같은 별도 트랜스파일러를 사용하지 않아도 ES6의 새로운 기능을 기존의 자바스크립트 엔진에서 실행할 수 있다.

구글은 원래 Anuglar의 주력 언어로 TypeScript의 상위 집합인 AtScript를 계획했지만, TypeScript를 채용하는 것으로 방향을 전환했다. 그 배경으로 Angular에 필요한 기능을 TypeScript의 사양에 포함하는 것을 TypeScript 진영과 합의한 것으로 전해진다.



또한 구글은 2년간의 검토 끝에 2017년 3월 사내 표준 언어(Canonical Languages)로 TypeScript의 사용을 승인하였다.



## 2. TypeScript의 장점

### 2.1 정적 타입

TypeScript를 사용하는 가장 큰 이유 중 하나는 정적 타입을 지원한다는 것이다. 아래 함수를 살펴보자.

```javascript
function sum(a,b){
    return a + b;
}
```

위 함수를 정의한 개발자의 의도는 아마도 2개의 숫자 타입 인수를 전달받아 그 합계를 반환하려는 것으로 추측된다. 하지만 코드상으로는 어떤 타입의 인수를 전달하여야 하는지, 어떤 타입의 반환값을 리턴해야 하는지 명확하지 않다. 따라서 위 함수는 아래와 같이 호출될 수 있다.

```javascript
function sum(a, b) {
  return a + b;
}

sum('x', 'y'); // 'xy'
```

위 코드는 자바스크립트 문법상 어떠한 문제도 없으므로 자바스크립트 엔진은 아무런 이의 제기없이 위 코드를 실행할 것이다. 이러한 상황이 발생한 이유는 변수나 반환값의 타입을 사전에 지정하지 않는 자바스크립트의 동적 타이핑(Dynamic Typing)에 의한 것이다.

위 함수를 TypeScript의 정적 타입을 사용하여 다시 작성 해보자.

```typescript
function sum(a: number, b: number){
    return a + b;
}

sum('x', 'y');
// error TS2345: Argument of type '"x"' is not assignable to parameter of type 'number'.
```

TypeScript는 정적 타입을 지원하므로 컴파일 단계에서 오류를 포착할 수 있는 장점이 있다. 명시적인 정적 타입 지정은 개발자의 의도를 명확하게 코드로 기술할 수 있다. 이는 코드의 가독성을 높이고 예측할 수 있게 하며 디버깅을 쉽게 한다.



### 2.2 도구의 지원

TypeScript를 사용하는 이유는 여러가지 있지만 가장 큰 장점은 IDE(통합개발환경)를 포함한 다양한 도구의 지원을 받을 수 있다는 것이다. IDE와 같은 도구에 타입 정보를 제공함으로써 높은 수준의 인텔리센스(IntelliSense), 코드 어시스트, 타입 체크, 리팩토링 등을 지원받을 수 있다.



### 2.3 강력한 객체지향 프로그래밍 지원

인터페이스, 제네릭 등과 같은 강력한 객체지향 프로그래밍 지원은 크고 복잡한 프로젝트의 코드 기반을 쉽게 구성할 수 있도록 도우며, Java, C# 등의 클래스 기반 객체지향 언어에 익숙한 개발자가 자바스크립트 프로젝트를 수행하는 데 진입 장벽을 낮추는 효과도 있다.



### 2.4 Angular

마지막으로 Angular는 TypeScript 뿐만 아니라 자바스크립트(ES5, ES6), Dart로도 작성할 수 있지만 Angular 문서, 커뮤니티 활동에서 가장 많이 사용되고 있는 것이 TypeScript이다. Angular 관련 문서의 예제 등도 TypeScript로 작성된 것이 대부분이어서 관련 정보를 얻을 때 이점이 있으며 이러한 현상은 앞으로도 지속될 것으로 예상된다.



## 3. 개발환경 구축

TypeScript 파일(.ts)은 브라우저에서 동작하지 않으므로 TypeScript 컴파일러를 이용해 자바스크립트 파일로 변환해야 한다. 이를 컴파일 또는 트랜스파일링이라 한다.

### 3.1 Node.js 설치

- Node.js를 먼저 설치한다.

### 3.2 TypeScript 컴파일러 설치 및 사용법

- 다음과 같이 터미널에서 npm을 사용하여 TypeScript를 전역에 설치한다.

```bash
$ npm install -g typescript
```

- 설치가 완료되었으면 버전을 출력하여 TypeScript의 설치를 확인한다.

```bash
$ tsc -v
Version 4.1.2
```

- TypeScript 컴파일러(tsc)는 TypeScript 파일(.ts)을 자바스크립트 파일로 트랜스파일링한다.

- 트랜스파일링을 실행해보기 위해 아래와 같은 파일을 작성해 보자. 참고로 TypeScript 파일의 확장자는 .ts이다.

```typescript
// person.ts
class Person {
  private name: string;

  constructor(name: string) {
    this.name = name;
  }

  sayHello() {
    return "Hello, " + this.name;
  }
}

const person = new Person('Lee');

console.log(person.sayHello());
```

트랜스파일링을 실행해 보자. tsc 명령어 뒤에 트랜스파일링 대상 파일명을 지정한다. 이때 확장자 .ts는 생략할 수 있다.

```bash
$ tsc person
```

트랜스파일링 실행 결과, 같은 디렉터리에 자바스크립트 파일(person.js)이 생성된다.

```javascript
// person.js
var Person = /** @class */ (function () {
    function Person(name) {
        this.name = name;
    }
    Person.prototype.sayHello = function () {
        return "Hello, " + this.name;
    };
    return Person;
}());
var person = new Person('Lee');
console.log(person.sayHello());
```

이때 트랜스파일링된 person.js의 자바스크립트 버전은 ES3이다. 이는 TypeScript 컴파일 타겟 자바스크립트 기본 버전이 ES3이기 때문이다.

만약, 자바스크립트 버전을 변경하려면 컴파일 옵션에 `--target` 또는 `-t`를 사용한다. 현재 tsc가 지원하는 자바스크립트 버전은 ‘ES3’(default), ‘ES5’, ‘ES2015’, ‘ES2016’, ‘ES2017’, ‘ES2018’, ‘ES2019’, ‘ESNEXT’이다. 예를 들어, **ES6 버전으로 트랜스파일링을 실행하려면 아래와 같이 옵션을 추가한다.**

```bash
$ tsc person -t ES2015
```

```javascript
// person.js
class Person {
    constructor(name) {
        this.name = name;
    }
    sayHello() {
        return "Hello, " + this.name;
    }
}
const person = new Person('Lee');
console.log(person.sayHello());
```

트랜스파일링이 성공하여 자바스크립트 파일이 생성되었으면 Node.js REPL을 이용해 트랜스파일링된 person.js를 실행해보자.

```bash
$ node person
Hello, Lee
```

매번 옵션을 지정하는 것은 번거로우므로 tsc 옵션 설정 파일을 생성하도록 하자.

```bash
$ tsc --init
message TS6071: Successfully created a tsconfig.json file.
```

아래와 같이 tsc 옵션 설정 파일인 tsconfig.json이 생성된다.

```json
{
  "compilerOptions": {
    /* Basic Options */
    // "incremental": true,                   /* Enable incremental compilation */
    "target": "es5",                          /* Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017', 'ES2018', 'ES2019' or 'ESNEXT'. */
    "module": "commonjs",                     /* Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'. */
    // "lib": [],
```

**tsc 명령어 뒤에 파일명을 지정하면 tsconfig.json이 무시되므로 주의하기 바란다.**

```bash
$ tsc person # ✘ tsconfig.json이 무시된다.
```

tsconfig.json을 적용하려면 아래와 같이 트랜스파일링하도록 한다.

```bash
$ tsc
```

위와 같이 파일명을 지정하지 않으면 프로젝트 폴더 내의 모든 TypeScript 파일이 모두 트랜스파일링된다. 상속 관계에 있는 두 개의 TypeScript class를 작성해보자.

```typescript
// person.ts
export class Person {
  protected name: string;

  constructor(name: string) {
    this.name = name;
  }
  sayHello() {
    return "Hello, " + this.name;
  }
}
```

```typescript
// student.ts
import { Person } from './person';

class Student extends Person {
  study(): string {
    return `${this.name} is studying.`;
  }
}

const student = new Student('Lee');

console.log(student.sayHello());
console.log(student.study());
```

코드 작성을 마쳤으면 다음 명령으로 두 개의 TypeScript 파일을 한번에 트랜스파일링한다.

```bash
$ tsc
$ node student
Hello, Lee
Lee is studying.
```

`--watch` 또는 `-w` 옵션을 사용하면 트랜스파일링 대상 파일의 내용이 변경되었을 때 이를 감지하여 자동으로 트랜스파일링이 실행된다.

```bash
$ tsc --watch
21:23:30 - Compilation complete. Watching for file changes.
```

또는 아래와 같이 tsconfig.json에 watch 옵션을 추가할 수도 있다.

```json
{
  // ...
  "watch": true
}
```

