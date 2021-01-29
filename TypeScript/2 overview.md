# 타입스크립트 개요

<img src="https://github.com/cjy0019/TIL/blob/master/images/typescript.jpeg?raw=true" width="50%">

## 1. TSC(TypeScript Compiler, TSC)

일반적으로 자바스크립트 프로그램은 개발자가 작성한 다수의 텍스트 파일로 구성된다. 이 텍스트들을 컴파일러라고 불리는 프로그램이 파싱해서 AST(Abstract Syntax tree)라는 자료구조로 변환한다. 그리고 컴파일러는 AST를 바이트라는 low-level의 언어로 변환한다. 바이트코드가 생성되면 런타임이라는 다른 프로그램에 바이트코드를 입력해 평가하고 결과를 얻을 수 있다. 

1. 프로그램이 AST로 파싱됨.
2. AST가 바이트코드로 컴파일됨.
3. 런타임이 바이트코드를 평가한다.

타입스크립트가 특이한 점은 컴파일러가 코드를 **바이트코드 대신 자바스크립트 코드로 변환한다는 점이다**. 즉, AST로 파싱이 일어난 후 런타임이 바이트코드를 평가하기 전에 **타입 검사기가 AST를 확인하는 과정을 거친다.**



## 2. 세팅

```bash
# 새 NPM 프로젝트 초기화
$ npm init -y

# TSC, TSLint, NodeJS용 타입 선언 설치
$ npm install --save-dev typescript tslint @types/node
```



### 2.1 tsconfig.json

모든 타입스크립트 프로젝트는 루트 디렉터리에 tsconfig.json이라는 파일이 존재해야 한다.

```bash
$ touch tsconfig.json
```

```json
// tsconfig.json
{
  "compilerOptions": {
    "lib": ["ES2015"],
    "module": "commonjs",
    "outDir": "dist",
    "sourceMap": true,
    "strict": true,
    "target": "es2015"
  },
  "include": ["src"]
}
```

위와 같이 수동으로 세팅할 수 있지만,

```bash
$ tsc --init
```

내장 명령을 통해 자동으로 생성할 수도 있다.

```json
// tsconfig.json
{
  "compilerOptions": {
    "lib": ["ES2015"], // TSC가 코드 실행 환경에서 이용할 수 있다고 가정하는 API
    "module": "commonjs", // TSC가 코드를 컴파일할 대상 모듈 시스템(CommonJS, SystemJS, ES2015)
    "outDir": "dist", // 생성된 자바스크립트 코드를 출력할 디렉터리
    "sourceMap": true,
    "strict": true,
    "target": "es2015" // TSC가 코드를 컴파일할 자바스크립트 버전(ES5, ES2015, ES2016)
  },
  "include": ["src"] // TSC가 타입스크립트 파일을 찾을 디렉터리
}
```



## 2.2 tslint.json

일반적인 프로젝트에서는 TSLint 설정을 정의하는 tslint.json 파일도 포함한다.

```bash
./node_modules/.bin/tslint --init
```

위 명령어를 실행하면 다음과 같은 json형식의 파일이 생성된다.

```json
{
    "defaultSeverity": "error",
    "extends": [
        "tslint:recommended"
    ],
    "jsRules": {},
    "rules": {},
    "rulesDirectory": []
}
```

[tslint 규칙](https://palantir.github.io/tslint/rules/)

[tslint-react 규칙](https://www.npmjs.com/package/tslint-react)