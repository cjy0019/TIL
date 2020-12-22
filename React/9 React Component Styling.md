# React Component Styling

## 1. Style-loader

`<style>`태그를 삽입해서 CSS에 DOM을 추가해준다.

### 1.1 실습

```bash
$ npx create-react-app style-loaders-exmaple
$ cd style-loaders-example
$ npm run eject
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/webpack-eject.PNG?raw=true" width="50%"></p>

eject를 하면 create-react-app 속에 감춰져있던 파일들이 config라는 디렉토리안에 추가된다. 그 중에서 webpack에 관한 설정을 확인할 수 있는 webpack.config.js를 열어보자.



### 1.2 webpack.config.js

webpack에 관한 설정이 담겨있는 파일이다. 예전에는 개발자가 직접 작성해서 사용했으나 cra의 보급으로 직접 작성하지 않아도 간편하게 설정이 되어있다. 즉, create-react-app에서 지원하지 않는 모듈을 사용하겠다면 eject를 통해 따로 작성해줘야 한다!

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/webpack-config.PNG?raw=true" width="50%"></p>

css모듈에 관련된 설정을 보면 css, css모듈, sass, sass모듈 설정이 모두 각각 정해져있는 것을 볼 수 있다.

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/cssloader.PNG?raw=true" width="50%"></p>

- test  : 정규표현식에 해당하는 파일을 의미한다.
- exclude : module.css로 끝나는 파일을 제외한다. 
- use : getStyleLoaders메서드를 값으로 갖는 로더를 사용한다는 의미이다.(추후에 getStyleLoaders에 대해 공부하고 보충 설명하자)

다음과 같이 네 가지의 style-loader가 설정되어 있음을 확인했다.



### 2. 스타일 스코핑 문제

React.js에서는 다음과 같이 import를 진행하고 파일 전체가 style태그로 들어가게 된다. 이 때 같은 이름의 클래스를 다른 파일에서 만들었을 때 문제가 발생한다. **이를 스타일이 스코핑되지 않는다고 한다. 리액트의 문제점 중 하나이다.**

```javascript
import './index.css';
import App from './App';
```

클래스가 중복되는 문제를 방지하기 위한 여러 가지 방식들이 있는데 그 중 하나는 이름을 지을 때 특별한 규칙을 사용하는 것이고 다른 하나는 CSS Selector를 이용하는 것이다.



### 2.1 CSS Selector

CSS Selector를 사용하면 CSS 클래스가 특정 클래스 내부에 있는 경우에만 스타일을 적용할 수 있다. 예를 들어, App.js 컴포넌트의 header에 적용하고 싶다면 다음과 같이 하면된다. 원래는 'App-header'라는 이름의 클래스를 가지고 있었지만 CSS Selector를 사용해서 바꿀 수 있다.

```html
// App.js

function App() {
  return (
    <div className='App'>
      <header className='header'>
         ...
      </header>
    </div>
  );
}
```

```css
.App .header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}
```



### 2.2 이름 짓는 규칙

특별한 이름 규칙을 사용해서 중복되지 않는 class를 선언할 수 있다. 그 중 가장 대표적인 방법론으로 **BEM 네이밍**을 들 수 있다. 이름을 지을 때 해당 클래스가 어디에서 어떤 용도로 사용되는지 명확하게 작성하는 방식이다. 



### 2.3 SCSS

#### 2.3.1 node-sass

브라우저는 Sass의 문법을 알지 못하기 때문에 Sass(.scss) 파일을 css 파일로 트랜스파일링(컴파일)하여야 한다. 따라서 Sass 환경의 설치가 필요하다. node-sass는 Node.js를 컴파일러인 LibSass에 바인딩한 라이브러리 입니다.

```bash
$npm install node-sass
```

> ```code
> Error: Node Sass version 5.0.0 is incompatible with ^4.0.0.
> ```
>
> node-sass는 버전에 의존적이기 때문에 다음과 같은 에러가 발생하기도 한다. 에러가 뜬다면 일단 node_modules를 지우고 package.json에서 지원하는 node-sass 버전을 적어주고 다시 npm install을 진행한다.



### 2.3.2 SCSS 작성

```scss
.App {
  text-align: center;

  .logo {
    height: 40vmin;
    pointer-events: none;
  }

  .header {
    background-color: #282c34;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-size: calc(10px + 2vmin);
    color: white;
  }

  .link {
    color: #61dafb;
  }
}
```

SCSS에서도 기본적으로 CSS가 동작하기 때문에 CSS를 복사해서 붙여넣고 위와 같이 계층구조의 형태로 작성해줄 수 있다. BEM 보다는 가독성이 좋다고 할 수 있다. 또한 키프레임 또한 따로 관리할 수 있기 때문에 구조적인 코드를 만드는데 용이하다.



### 2.3 CSS module

CSS Module은 CSS를 불러와서 사용할 때 클래스 이름을 고유한 값, 즉 `[파일 이름]_[클래스이름]_[해시값]` 형태로 자동으로 만들어서 컴포넌트 스타일 클래스 이름이 중첩되는 현상을 방지해주는 기술이다. 리액트 구버전(v1)에서는 웹팩에서 css-loader 설정을 별도로 해야했지만, v2 버전부터는 별도로 설정할 필요 없이 .module.css 확장자로 파일을 저장하면 CSS Module이 완성된다.

```javascript
import styles from './App.module.css';
```

다음으로 CSS에 있는 코드를 복사해서 `App.module.css`에 복사한다.

```javascript
// App.js에서 console로 가져온 styles 모듈을 출력해본다
console.log(styles);

{
    App: "App_App__AOgs7"
    App-logo: "App_App-logo__2-rg8"
    App-logo-spin: "App_App-logo-spin__37-1f"
    header: "App_header__POKNi"
    link: "App_link__jb7Kt"
    logo: "App_logo__11dRw"
}
```

```jsx
function App() {
  console.log(styles);
  return (
    <div className={styles.App}>
      <header className={styles.header}>
        <img src={logo} className={styles.logo} alt='logo' />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className={styles.link}
          href='https://reactjs.org'
          target='_blank'
          rel='noopener noreferrer'>
          Learn React
        </a>
      </header>
    </div>
  );
}
```



### 2.4 SCSS Module

CSS 모듈을 사용하는 방법과 동일하다.



### 2.5 className 실습

```jsx
// components/Button.jsx
import React from 'react';
import styles from './Button.module.css';

export default class Button extends React.Component {
  state = {
    loading: false,
  };

  render() {
    const { loading } = this.state;
    return (
      <button
        {...this.props}
        className={
          loading ? `${styles.button} ${styles.loading}` : styles.button
        }
        onClick={this.startLoading}
      />
    );
  }
  startLoading = () => {
    this.setState({ loading: true });
    setTimeout(() => {
      this.setState({ loading: false });
    }, 1000);
  };
}
```

```css
// components/Button.module.css
.button {
  background: transparent;
  border-radius: 3px;
  border: 2px solid palevioletred;
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;
  font-size: 20px;
}

.loading {
  border: 2px solid grey;
  color: grey;
}
```

버튼을 누르면 다음으로 회색으로 변하는 클래스를 추가해주고 1초 후에 다시 원래대로 돌아오는 예제이다. 클래스를 사용하여 스타일링을 진행할 수도 있지만 간단한 로직인데 코드가 길어지는 현상이 발생할 수 있다.



### 2. classNames 라이브러리

```javascript
console.log(classNames('foo','bar', 'baz')); // foo bar baz
console.log(classNames({foo : true}, {bar : false})) // foo 
console.log(classNames(null, false, 'bar', undefined, 0, 1, {baz : null}, ""); // bar 1
```

classNames 라이브러리를 사용해서 위코드를 조금더 간결하게 만들 수 있다.

```jsx
// components/Button.jsx
import React from 'react';
import styles from './Button.module.css';

export default class Button extends React.Component {
  state = {
    loading: false,
  };

  render() {
    const { loading } = this.state;
    return (
      <button
        {...this.props}
        className={
          // loading ? classNames(styles.button, styles.loading): styles.button
          // loading ? classNames(styles.button, loading && styles.loading)
        }
        onClick={this.startLoading}
      />
    );
  }
  startLoading = () => {
    this.setState({ loading: true });
    setTimeout(() => {
      this.setState({ loading: false });
    }, 1000);
  };
}
```

조금더 간단하게 해보면,

```jsx
import React from 'react';
import styles from './Button.module.css';
import classNames from 'classnames/bind';

const cx = classNames.bind(styles);

export default class Button extends React.Component {
  state = {
    loading: false,
  };

  render() {
    const { loading } = this.state;

    return (
      <button
        {...this.props}
        className={cx('button', { loading })}
        onClick={this.startLoading}
      />
    );
  }
  startLoading = () => {
    this.setState({ loading: true });
    setTimeout(() => {
      this.setState({ loading: false });
    }, 1000);
  };
}
```

