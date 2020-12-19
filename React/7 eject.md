# CRAeject

리액트를 CRA(Create-react-app)을 사용해서 시작하면 명령어가 자동으로 설치된다.

**package.json**

```json
"scripts": {
    "start": "cross-env NODE_PATH=src react-scripts start",
    "build": "cross-env NODE_PATH=src react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject"
  }
```



## eject

eject는 모든 설정들을 밖으로 추출해주는 명령어이다. eject를 사용하면 CRA로 만든 프로젝트에서 CRA를 제거하게된다. 이는 다시 원래 상태로 돌이킬 수 없기 떄문에 결정전에 매우 신중해야한다. **일반적으로는 cra 내에서 해결이 안되는 설정을 추가해야 할 때 한다.**

```bash
$ npm run eject
```

<img src="https://github.com/cjy0019/TIL/blob/master/images/ejection.png?raw=true" width="40%">

- react-scripts는 사라진다.
- 드러내지 않고 cra에 의해 사용되던 각종 패키지가 다음과 같이 package.json에 나타난다.
- Jest, Babel, ESLint 설정이 추가된다.
- 각종 설정 파일이 config 폴더에 생성된다.