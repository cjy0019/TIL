# React 시작하기

## 1. 준비물

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/node&npm_logo.png?raw=true" width ="70%"></p>

Node 8.16.0 버전 또는 Node 10.16.0이상의 버전이 필요하다.

npm은 5.6 버전 이상이 필요하다. 

[NodeJS 다운받기](https://nodejs.org/en/)

Current(현재 버전)은 최신 기능을 제공하고 기존 API의 기능 개선에 초점이 맞춰진 버전으로, 업데이트가 잦고 기능이 변경될 가능성이 높기 때문에 간단한 개발 및 테스트에 적당한 버전이다.



## 2. Create React App

- 특별한 빌드 구성없이 빠르게 React 앱을 만들 수 있게 제공하는 개발환경이다.

먼저 프로젝트를 진행할 폴더를 만들고, 다음의 명령어를 입력해준다.

**npx**

```bash
npx create-react-app [프로젝트 이름]
cd [프로젝트 이름]
npm start
```

**npm**

```bash
npm init react-app [프로젝트 이름]
```

**yarn**

```bash
yarn create react-app [프로젝트 이름]
```



<img src="https://github.com/cjy0019/TIL/blob/master/images/react_tut_error.PNG?raw=true" width="55%">



다음과 같은 오류가 날 경우 vscode로 열어서 실행해준다.

- `npm install -g create-react-app`을 통해 global로 설치했을 경우 `npm uninstall -g create-react-app` 또는 `yarn global remove create-react-app`으로 제거 후에 해당 프로젝트에 다시 설치한다.

완료가 된 경우 다음과 같은 구조의 디렉토리를 형성하게 된다.

```code
my-app
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    └── serviceWorker.js
    └── setupTests.js
```



**npm start** or **yarn start**

```bash
cd [프로젝트 이름]

npm start 
```

개발 모드에서 앱을 실행한다. http://localhost:3000을 열어서 브라우저에서 확인할 수 있다.

코드를 변경하면 페이지가 자동으로 로드된다.



<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/react_finish.PNG?raw=true" width="70%"></p>



[자세한 내용은 리액트 공식 github을 참조하세요](https://github.com/facebook/create-react-app#creating-an-app)