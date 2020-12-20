# React config

## 1. ESLint

*The pluggable linting utility for JS and JSX*

```bash
$ npm init -y
$ npm install eslint -D
$ npx eslint --init
```



### 1.1 실행

해당 파일에 대해 eslint를 적용시키고 싶다면 다음과 같이 입력한다.

```bash
$ npx eslint app.js

$ npx eslint app.js --fix
```

--fix라는 플래그를 사용하면 자동으로 고쳐준다.



**.eslintrc.json**

```json
{
    "env": {
        "browser": true,
        "es2021": true
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "ecmaVersion": 12
    },
    "rules": {
        "semi":["error","always"] // 세미콜론이 없을 때 에러 발생
    }
}
```

.eslintrc.json에 가서 다음과 같이 설정을 해줄수 있다.



### 1.2 cra react

cra를 이용해서 앱을 실행시켰다면 다음과 같이 eslint가 미리 설정되어 있다.

```json
"eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
    ],
    "rules" : {
        // bla bla
    }
  },
```

"rules"를 이용해서 내용을 덮어 씌울 수 있다.



### 1.3 eslint vs prettier

Prettier 에서 불필요하거나 Prettier와 충돌할 수 있는 모든 규칙을 끌 수도 있다.

```bash
$ npm i eslint-config-prettier -D
```

```json
"eslintConfig": {
    "extends": [
      "react-app",
      "react-app/jest"
      "prettier"
    ],
}
```



**rules**

.eslintrc.json에 넣어줄 rules에 관한 자료는 다음 링크에서 확인가능하다.

[rules 문서](https://eslint.org/docs/rules/)



## 2. Husky

### 2.1 설치

```bash
$ npm install husky@next --save-dev
```



### 2.2 설정

**package.json**

```json
"husky":{
    "hooks":{
        "pre-commit" : "lint-staged"
    }
},
"lint-staged":{
    "**/*.js":[
        "eslint --fix",
        "prettier --write",
        "git add"
    ]
}
```

