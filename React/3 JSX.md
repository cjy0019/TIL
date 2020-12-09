# JSX

## 1. JSX란 무엇인가?

JSX는 JavaScript XML이라는 의미를 담고 있다. JavaScript를 확장한 문법이다.

JSX는 XML/HTML과 Syntax가 비슷하면서 리액트에서 사용되는 문법이다. 즉, 자바스크립트/React 코드와 공존할 수 있도록 ECMAScript를 확장한 코드라고 할 수 있다. 

JSX는 자바스크립트 파일에 있는 HTML 같은 텍스트들을 자바스크립트 엔진이 파싱할 수 있는 표준 자바스크립트 객체로 변환하기 위해 Babel과 같은 프리프로세서에 의해 사용되도록 의도되었다.

**기본적으로 JSX를 사용하면 자바스크립트 코드를 작성할 때랑 같은 파일에 HTML/XML(돔트리 구조와 비슷한)을 작성할 수 있고, 브라우저에서 실행되기 전에 번들링 과정에서 Babel은 JSX를 자바스크립트 코드로 변환한다.**

```react
// JSX
function App(){
    return (
    	<div>
        	Hello <b>react</b>
        </div>
    );
}
```

이렇게 작성된 JSX는 다음과 같이 변환된다.

```javascript
React.createElement(
          type,   태그 이름 문자열 | React 컴포넌트 | React.Fragment
         [props], // 리액트 컴포넌트에 넣어주는 데이터 객체
         [...children] // 자식으로 넣어주는 요소들
);
    
function App(){
    return React.createElement('div', null, 'Hello ', React.createElement('b', null, 'react'));
}
```

위의 코드와 같이`React.createElement`라는 메서드를 통해 요소(element)를 생성해야 한다면, 요소의 depth나 갯수만큼 사용해야 한다. 하지만 위의 JSX코드는 HTML형식을 지니고 있어서 가독성이 매우 좋다.



**ReactDOM.render**

> 이 코드는 컴포넌트를 페이지에 렌더링하는 역할을 하고, react-dom 모듈을 불러와야 사용할 수 있다. Main()의 역할을 담당하는 함수라고 볼 수도 있다. 첫 번째 파라미터에는 페이지에 렌더링할 내용을 JSX형태로 작성하고, 두 번째 파라미터에는 해당 JSX를 렌더링할 document 내부 요소를 설정한다.

```react
ReactDOM.render(
        React.createElement(Component, null, null),
        document.querySelector('#root'),
);
```



## 2. JSX 문법

### 2.1 부모 요소로 감싼다(최상위 요소가 하나여야 한다)

```react
import React from 'react';

function App() {
  return (
    <h1>Hello react</h1>
    <h2>Bye react</h2>
  );
}

export default App;
```

위의 코드는 에러를 발생시킨다. 부모 요소에 의해 래핑되어 있지 않아서 생긴 오류인데 다음과 같이 해결할 수 있다.

```react
import React from 'react';

function App() {
  return (
    <div>
        <h1>Hello react</h1>
        <h2>Bye react</h2>
    </div>
  );
}
export default App;
```

Virtual DOM에서 컴포넌트 변화를 감지할 때 효율적으로 비교할 수 있게 컴포넌트는 하나의 DOM 트리로 이루어져 있어야 한다는 규칙때문이다. 하지만 불필요한 태그를 생성하는 것은 좋지 않으므로,

```react
import React, {Fragment} from 'react';

function App(){
    return (
    	<Fragment>
            <h1>Hello react</h1>
            <h2>Bye react</h2>
        </Fragment>
    )
}
export default App;

function App(){
    return (
    	<>
            <h1>Hello react</h1>
            <h2>Bye react</h2>
        <>
    );
}
```

두가지의 방법으로 표현하여 해결할 수 있다.



### 2.2 자바스크립트 표현식

JSX 내부에서는 자바스크립트 표현식을 사용할 수 있다. **자바스크립트 표현식을 작성하려면 JSX 내부에서 코드를 { }로 감싸야 한다.**

```react
import React from 'react';

function App(){
    const name = 'React';
    return (
    	<>
            <h1>Hello {name}</h1>
            <h2>Bye react</h2>
        </>
    );
}
```



### 2.3 if문 대신 삼항 연산자

JSX의 {}에서 if문을 사용할 수 없다. if문은 표현식이 아닌 문이기 떄문이다. 따라서 if문을 쓰기보다는 삼항 연산자를 사용한다.

```react
function App(){
    const name = 'React';
    return (
    	<>
        	{name === 'React' ? (<h1>리액트입니다</h1>) : (<h2>리액트가 아닙니다</h2>)}
        </>
    );
}
```



### 2.4 AND 연산자를 이용한 렌더링

```react
function App() {
	const name = "REEACT";
    return <div>{name === 'React' && <h1>리액트입니다.</h1>}</div>;
}
```

다음과 같이 조건부로 렌더링을 해줄 수 있다. 주의할 점은 falsy한 값이 오면 0이 렌더링된다.



### 2.5 undefined

리액트 컴포넌트에서는 함수에서 undefined만 반환하여 렌더링하는 경우를 피해야한다.

```react
function App() {
    const name = undefined;
    return name;
}
```

다음 코드는 브라우저에서 오류를 발생시킨다. 이런 상황을 OR(||) 연산자를 사용하여 해결할 수 있다.

```react
function App() {
    const name = undefined;
    return name || '값이 undefined입니다';
}
```

그러나 JSX 내부에서 undefined를 렌더링하는 것은 괜찮다.

```react
function App() {
    const name = undefined;
    return <div>{name || 'react'}</div>
}
```



## 2.6 인라인 스타일링

리액트에서 DOM 요소에 스타일을 적용할 때는 객체 형태로 넣어야한다. -이 들어가는 문자는 카멜 케이스를 이용하여 작성해야한다. 
ex) backgroundColor

```react
function App() {
	const name = 'React';
    const style = {
		backgroundColor : 'black',
        color : 'aqua',
        fontSize : '48px',
        padding : 16 // 단위를 생략하면 px로 인지한다.
    };
    return <div style = {style}>{name} </div>;
}
```

미리 style을 지정하지 않고 바로 선언하고 싶다면 {{}}을 이용하여 작성한다.

```react
function App() {
    const name = 'React';
    return (
    	<div style = {{
                backgroundColor : 'black',
                color : 'aqua',
                fontSize : '48px',
                padding : 16 // 단위를 생략하면 px로 인지한다.
            }}>
        	{name}
        </div>
    );
}
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/react-style-img.PNG?raw=true" width ="60%"></p>

### 2.7 className

HTML에서 CSS클래스를 사용할 때는 `class`라는 키워드를 사용하는데 JSX에서는 **className**으로 설정해 주어야 한다.

```css
.react {
  background-color: aqua;
  color: black;
  font-size: 48px;
  font-weight: bold;
  padding: 16px;
}
```

```react
import './App.css';

function App() {
    const name = 'React';
    return <div className="react">{name}</div>;
}
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/react-img-change.PNG?raw=true" width ="60%"></p>

### 2.8 꼭 닫아야 하는 태그

`<input>`요소는 `<input>`이라고만 입력해도 동작한다. 하지만 JSX 에서는 오류를 발생시킬 수 있다.

```react
function App() {
    const name = '리액트';
    return (
    	<>
        	<div className="react">{name}</div>
        	<input>
        </>
    );
}
```

다음 오류를 해결하려면 `<input></input>`이와 같이 태그를 닫아주어야 한다. 태그에 별도의 내용이 들어가지 않는 경우에는 `<input />`과 같이 작성할 수도 있다.