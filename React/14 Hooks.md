# Hooks

Hooks는 함수형 컴포넌트에서도 상태 관리를 할 수 있는 useState, 렌더링 직후 작업을 설정하는 useEffect 등의 기능을 제공하고 함수형 컴포넌트에서 할 수 없었던 작업을 가능하게 해준다.

Hooks 이전에는 클래스 컴포넌트와 함수형 컴포넌트를 나누어 사용했는데 Hooks가 나온 이후로는 함수형 컴포넌트를 주로 사용한다.

## 1. Basic Hooks

- useState
- useEffect
- useContext

### 1.1 useState

가장 기본적인 Hook으로 함수형 컴포넌트에서도 가변적인 상태를 지닐 수 있게 해준다.

```jsx
// 클래스형 컴포넌트로 작성한 카운터 예제
import React from 'react';

export default class Example1 extends React.Component {
  state = {
    count: 0,
  };

  render() {
    const { count } = this.state;
    return (
      <div>
        <p>You clicked {count} Times</p>
        <button onClick={this.click}>Click me</button>
      </div>
    );
  }
  click = () => {
    this.setState(({ count }) => ({ count: count + 1 }));
  };
}
```

클래스형 컴포넌트에서만 가능했던 상태관리를 Hooks를 사용하여 다음과 같이 함수형 컴포턴트에서도 상태를 관리할 수 있다.

```jsx
// 함수형 컴포넌트로 작성한 카운터 예제
import React, { useState } from 'react';

const Example2 = () => {
  const [count, setCount] = useState(0);

  const click = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>You clicked {count} Times</p>
      <button onClick={click}>Click me</button>
    </div>
  );
};

export default Example2;
```

useState의 setCount함수를 사용하면 count의 값을 변경한 후 변경된 값을 이용해서 함수를 다시 호출한다.

> class 컴포넌트의 단점
>
> - 컴포넌트 사이에서 상태와 관련된 로직을 재사용하기 어렵다.
> - 복잡한 컴포넌트들은 이해하기 어렵다.
> - class는 사람과 기계를 혼동시킨다(컴파일 단계에서 코드를 최적화하기 어렵게 만든다.)
> - this.state는 로직에서 레퍼런스를 공유하기 때문에 문제를 발생할 수 있다.

**useState vs setState**

useState는 변경된 state 값을 이용해서 그 시점에 렌더링을 다시 하지만 setState의 state는 객체 값이므로 reference를 계속해서 참조하고 있다. 따라서 다른 사용법에 차이점이 있다.



### 1.2 useEffect

useEffect는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다. 클래스형 컴포넌트의 componnetDidMount와 componentDidUpdate를 합친 형태로 보아도 무방하다.

```jsx
import React, { useEffect, useState } from 'react';

const Example5 = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('componentDidMount & componentDidUpdate');
  });
  const click = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>You clicked {count} Times</p>
      <button onClick={click}>Click me</button>
    </div>
  );
};

export default Example5;
```

**componentDidMount & componentDidUpdate**

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/useEffect.PNG?raw=true" width="70%"></p>

현재 사진 상에서 'componentDidMount & componentDidUpdate'가 콘솔에 두 번 찍힌 것을 확인할 수 있다. 가장 처음에 렌더링이 일어나자마자 즉 componentDidMount 시점에 콘솔에 찍혔고 클릭을 한번 했을 때 즉, componentDidUpdate 시점에 콘솔에 찍힌 것을 알 수 있다. 

**componentDidMount Only**

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/useEffect-componnetDidMount.PNG?raw=true" width="70%"></p>

여러 번을 클릭해서 state를 update 했음에도 불구하고 변화가 콘솔에는 한번만 찍힌 것을 알 수 있다. 즉 useEffect의 두번째 인자는 렌더링이 될 시점을 정해준다고 생각할 수 있다. 시점이 빈 배열이라면 최초에 렌더 된 직후를 의미한다.

```jsx
useEffect(() => {
    console.log('componentDidMount & componentDidUpdate');
  });
```

**componentWillUnmount**

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/useEffect-componentwillunmount.PNG?raw=true" width="60%"></p>

가장 먼저 componentDidMount 시점에 콘솔이 찍히고 이후에는 버튼을 한번 클릭하면 clean up이라는 것이 콘솔에 찍히게 된다. componentWillUnmount 시점에 렌더링을 하고 싶다면 useEffect 함수의 return으로 함수를 사용하는데 이렇게 되면 해당 함수는 다음 렌더를 하기전에 실행이 된다.

```jsx
useEffect(() => {
    console.log('componentDidMount & componentDidUpdate');

    return () => {
      console.log('clean up');
    };
  });
```



### 1.3 useContext

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/contextAPI.PNG?raw=true" width="70%"></p>

이런 문제점을 해결하기 위해서 나온 것이 Context API이다.

**전역적으로 필요한 상태를 관리해야 할 때는 최상위 컴포넌트인 App에 state에 넣어서 관리한다.** 하지만 이럴 경우, 부모의 상태가 바뀌기 때문에 하위 컴포넌트들이 모두 다시 렌더링된다. 그러나 Context API를 사용하면 Context를 만들어 단 한 번에 원하는 값을 받아와서 사용할 수 있다는 장점이 있다. 



#### 1.3.1 사용법

- 데이터를 set하는 것은 가장 상위 컴포넌트이다. 이를 Provider라고 부른다.

- 데이터를 get하는 것은 모든 하위 컴포넌트들이다.
  - Consumer로 하는 방법
  - 클래스 컴포넌트의 this.context로 하는 방법
  - 함수형 컴포넌트의 **useContext**로 하는 방법



## 2. Additional Hooks

- useReducer
- useCallback, useMemo
- useRef, useImperativeHandle
- useLayoutEffect
- useDebugValue



## 3. Custom Hooks

```jsx
import { useEffect, useState } from 'react';

export default function useWindowWidth() {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    const resize = () => {
      setWidth(window.innerWidth);
    };

    window.addEventListener('resize', resize);

    return () => {
      window.removeEventListener('resize', resize);
    };
  }, []);

  return width;
}
```

`window.innerWidth`가 변경될 때 마다 렌더링 해주는 커스텀 훅을 만들어 보았다. 이 hook을 타 컴포넌트 안에서 또는 다른 hook안에서 사용할 수 있다.