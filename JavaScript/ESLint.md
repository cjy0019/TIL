# ESLint

- **ESLint**는 코딩 스타일 가이드를 따르지 않거나 문제가 있는 코드나 안티 패턴을 찾기 위해 사용하는 JavaScript linter이다.
- 코딩 컨벤션에 위배되는 코드나 안티 패턴을 자동 검출 해주므로 올바른 코딩 습관을 갖도록 돕는 유용한 툴이다. 사용할 것을 권장한다.



## install eslint

- Airbnb style guide를 기본으로 eslint를 설치하도록 한다. 
- eslint와 Airbnb style guide(Airbnb의 style guide를 eslint의 설정 파일화한 것)과 필요 플러그인을 로컬 설치한다. 
- eslint를 전역으로 설치할 수도 있지만 권장되지 않는다. 만약 전역으로 설치할 경우에는 공유 설정과 필요 플러그인을 로컬 설치해야 한다.

```bash
$ cd <project-folder>
$ npm init -y
# install eslint & friends
$ npm install eslint eslint-config-airbnb-base eslint-plugin-import eslint-plugin-html --save-dev
```

또는 아래의 방법으로 configuration file(.eslintrc.json)을 셋업할 수 있다.

```bash
$ cd <project-folder>
$ npm init -y
# Local Installation
$ npm install eslint --save-dev
# setup a configuration file
$ ./node_modules/.bin/eslint --init
? How would you like to configure ESLint? Use a popular style guid
e
? Which style guide do you want to follow? Airbnb
? Do you use React? No
? What format do you want your config file to be in? JavaScript
Checking peerDependencies of eslint-config-airbnb-base@latest
Installing eslint-config-airbnb-base@latest, eslint-plugin-import@
^2.7.0
npm WARN eslint-exam@1.0.0 No description
npm WARN eslint-exam@1.0.0 No repository field.

+ eslint-config-airbnb-base@12.0.0
+ eslint-plugin-import@2.7.0
updated 2 packages in 5.372s
Successfully created .eslintrc.js file in /Users/leeungmo/Desktop/eslint-exam
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/jslint.PNG?raw=true" width = "70%"></p>



## install ESLInt VSCode extension

VSCode ESLint extension을 설치한다.

`settings.json`으로 이동하여 아래의 설정을 추가한다.

```json
  ...
  // ESLINT
  "eslint.validate": [
    "javascript",
    "html"
  ]
```



## .eslintrc.json

프로젝트 루트에 `.eslintrc.json`을 생성하고 필요에 따라 아래와 같이 룰셋을 변경한다.

```javascript
{
  "parserOptions": {
    "ecmaVersion": 9
  },
  "env": {
    "browser": true,
    "commonjs": true,
    "node": true,
    "jquery": true
  },
  "extends": "airbnb-base",
  "plugins": [ "import", "html" ],
  "rules": {
    // "off" or 0 - turn the rule off
    // "warn" or 1 - turn the rule on as a warning (doesn’t affect exit code)
    // "error" or 2 - turn the rule on as an error (exit code is 1 when triggered)
    // "no-var": 0,
    "no-console": 0,
    "no-plusplus": 0,
    "vars-on-top": 0,
    "no-underscore-dangle": 0, // var _foo;
    "comma-dangle": 0,
    "func-names": 0, // setTimeout(function () {}, 0);
    "prefer-arrow-callback": 0, // setTimeout(function () {}, 0);
    "prefer-template": 0,
    "no-nested-ternary": 0,
    "max-classes-per-file": 0,
    "arrow-parens": ["error", "as-needed"], // a => {}
    "no-restricted-syntax": [0, "ForOfStatement"],
    "no-param-reassign": ["error", { "props": false }]
  }
}
```

