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
  )
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
  )
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
    )
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
    )
}
```

