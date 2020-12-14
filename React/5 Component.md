# Component

리액트에서의 컴포넌트는 매우 중요하다. 리액트로 만들어진 앱을 이루는 최소 단위가 컴포넌트이기 때문이다. 

리액트를 사용하여 애플리케이션 인터페이스를 설계한다면 사용자가 볼 수 있는 요소는 여러가지 컴포넌트로 구성되어 있다.

컴포넌트의 기능은 단순한 템플릿 이상이다. 데이터가 주어지면 이에 맞추어 UI를 만들어주기도 하고, 라이프사이클 API를 이용하여 컴포넌트가 화면에서 나타날 때, 사라질 때, 변화가 일어날 때 주어진 작업들을 처리할 수 있고 임의의 메서드를 만들어 특별한 기능을 하게 할 수도 있다.

결국 컴포넌트는 데이터를 입력받아 DOM Node를 출력하는 함수다. 이 때 입력받는 데이터는 props나 state 같은 것들이 있다.



#### Hooks 이전

- 컴포넌트 내부에 상태가 있다면?
  - class
- 컴포넌트 내부에 상태가 없다면?
  - 라이프사이클을 사용해야 한다면?
    - class
  - 라이프사이클에 관계 없다면?
    - function



#### Hooks 이후

- class
- function



## 1. 클래스형 컴포넌트

클래스형 컴포넌트와 함수형 컴포넌트의 역할은 똑같다. 차이점은 클래스형 컴포넌트는 state 기능 및 라이프사이클 기능을 사용할 수 있다는 것과 임의 메서드를 정의할 수 있다는 것이다.

**클래스형 컴포넌트에서는 render함수가 꼭 있어야 하고, 그 안에서 보여 주어야 할 JSX를 반환해야 한다.**

함수형 컴포넌트는 state와 라이프사이클 API의 사용이 불가능했었는데 리액트 v16.8 업데이트 이후 Hooks라는 기능이 도입되면서 해결되었다.

리액트 공식 매뉴얼에서는 컴포넌트를 새로 작성할 때 함수형 컴포넌트와 Hooks를 사용하도록 권장하고 있지만 클래스형 컴포넌트가 사라지는 것이 아니므로 알고 있어야한다.



### 1.1 모듈 내보내기

```javascript
export default MyComponent;
```

위 코드는 다른 파일에서 이 파일을 import할 때, 위에서 선언한 MyComponent 클래스를 불러오도록 설정한다.

### 1.2 모듈 불러오기

```js
import React from 'react';

const MyComponent = () => {
  return <div>나의 새롭고 멋진 컴포넌트</div>;
};

export default MyComponent;
```



## 2. props

props는 properties를 줄인 표현으로 컴포넌트 속성을 설정할 때 사용하는 요소이다. props 값은 해당 컴포넌트를 불러와 사용하는 부모 컴포넌트에서 설정할 수 있다.



### 2.1 JSX 내부에서 props 렌더링

```jsx
import React from 'react';

const MyComponent = props => {
  return <div>안녕하세요, 제 이름은 {props.name}입니다.</div>;
};

export default MyComponent;

```


### 2.2 컴포넌트를 사용할 때 props 값 지정하기

```javascript
import React from 'react';
import MyComponent from './MyComponent';

const App = () => {
  return <MyComponent name="React"/>;
};

export default App;
```

### 2.3 props 기본값 설정 : defaultProps

props값을 따로 지정하지 않았을 때 보여 줄 기본값을 설정하는 키워드이다.

```jsx
MyComponent.defaultProps = {
    name : '기본 이름'
}
```

### 2.4 children

컴포넌트 태그 사이의 내용을 보여 주는 props가 있는데 이것을 children 이라고 부른다.

```jsx
import React from 'react';

const MyComponent = (props) => {
  return (
    <div>
      안녕하세요, 제 이름은 {props.name}입니다.
      <br />
      children 값은 {props.children} 입니다.
    </div>
  );
};

MyComponent.defaultProps = {
  name: '기본 이름',
};

export default MyComponent;
```

**디스트럭쳐링 할당을 통해서 조금 더 간결하게 작성할 수 있다.**

```jsx
import React from 'react';

const MyComponent = (props) => {
  // 파라미터가 객체라면
  // const MyComponent = ({ name, children}) =>
  const { name, children } = props;
  return (
    <div>
      안녕하세요, 제 이름은 {props.name}입니다.
      <br />
      children 값은 {props.children} 입니다.
    </div>
  );
};

MyComponent.defaultProps = {
  name: '기본 이름',
};
```

### 2.5 propTypes

컴포넌트의 필수 props를 지정하거나 props의 타입을 지정할 때는 propTypes를 사용한다. 

```javascript
import propTypes from 'prop-types';

MyComponent.propTypes = {
    name : PropTypes.string,
}; 
// prop의 타입을 string으로 지정한다.
```

```jsx
const App = () =>{
    return <MyComponent name={3}>리액트</MyComponent>
};
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/prop-type-err.PNG?raw=true" width="70%"></p>

### 2.6 클래스 형 컴포넌트의 props

```jsx
import React, { Component } from 'react';
import propTypes from 'prop-types';

class MyComponent extends Component {
  render() {
    const { name, children } = this.props;
    return (
      <div>
        안녕하세요, 제 이름은 {name}입니다.
        <br />
        children 값은 {children}입니다.
      </div>
    );
  }
}

MyComponent.defaultProps = {
  name: '기본 이름',
};

MyComponent.propTypes = {
  name: propTypes.string,
};

export default MyComponent;
```

**defaultProps와 propTypes를 class 내부에서 설정할 수도 있다.**

```jsx
class MyComponent extends Component {
  static defaultProps = {
    name: '기본 이름',
  };

  static propTypes = {
    name: propTypes.string,
  };
}
```



## Props와 State

Props는 컴포넌트 외부에서 컴포넌트에 주는 데이터이다. State는 컴포넌트 내부에서 변경할 수 있는 데이터이다. 둘다 변경이 발생하면 렌더가 다시 일어날 수 있다.

```jsx
<FunctionComponent /> => {}
<FunctionComponent>자식</FunctionComponent> => {children : "자식"}
<FunctionComponent name="Mark">자식</FunctionComponent> => {children : "자식", name : "Mark"}
<FunctionComponent name="Mark" age={38}>자식</FunctionComponent> => {children : "자식", name : "Mark", age : 38}
```



### Render 함수

Props와 State는 render함수를 바탕으로 컴포넌트를 그린다. 그리고 Props와 State가 변경되면 컴포넌트를 다시 그린다. 컴포넌트를 그리는 방법을 기술하는 함수가 바로 렌더 함수이다.

