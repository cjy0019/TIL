# Redux Basic

## 1. Redux 개요

리덕스는 리액트에서 가장 많이 사용하는 상태 관리 라이브러리이다. 리덕스를 사용하면 컴포넌트의 상태 업데이트 관련 로직을 따로 분리하여 효율적으로 관리할 수 있고, props를 사용하지 않아도 손쉽게 값을 전달해 줄 수 있다.

단순히 상태 관리만을 위한다면 Context API를 사용하는 것만으로도 충분하다. 하지만 리덕스를 사용하면 더욱 체계적으로 관리할 수 있기 때문에 프로젝트의 규모가 크다면 리덕스를 사용하는 것이 좋다. 

<p align="center"><img src="https://s3-ap-northeast-2.amazonaws.com/opentutorials-user-file/module/4078/11034.png" width="70%"></p>

[사진 출처](https://opentutorials.org/module/4078/24935)



## 2. Redux 시작하기

```bash
$ npx create-react-app redux-start

$ npm i redux
```



### 3. 코딩 순서

1. state에 대한 구상
2. action 
3. reducer
4. createStore



### 4. 액션

상태에 어떠한 변화가 필요하면 액션이 발생한다. 액션은 하나의 단순한 **객체(object)**라고 할 수 있다.

액션은 payload에 따라 두 가지 형태로 구분이 된다.

```javascript
// 1. payload 없는 액션
{ type : 'TEST'}

// 2. payload 있는 액션
{ type : 'TEST', params: 'hello'}
```

type은 필수 프로퍼티이고, type은 문자열(오타 있을 시 찾기 어렵다&#128569;)이다.



#### 4.1 액션 생성자

액션 생성자는(action creator)는 액션 객체를 만들어 주는 함수이다.

```javascript
function 액션생성자 (...args){ return 액션; }
```

함수를 통해 액션을 생성하고, 액션 객체를 리턴해준다.

```javascript
crateTest('hello');
// {type : 'TEST', params : 'hello'} 리턴
```

변화가 일어날 때 마다 액션 객체를 만들어야 하는데 매번 액션 객체를 직접 작성하기 번거로울 수 있고, 만드는 과정에서 실수로 정보를 놓칠 수도 있다. 이러한 일을 방지하기 위해 이를 함수로 만들어 관리하는데 이를 액션 생성자라고 부른다.



#### 4.2 액션이 전달되는 과정

- 액션 생성자를 통해 액션을 만들어 낸다.
- 만들어낸 액션 객체를 리덕스 스토어에 보낸다.
- 리덕스 스토어가 액션 객체를 받으면 스토어의 상태 값이 변경된다.
- 변경된 상태 값에 의해 상태를 이용하고 있는 컴포넌트가 변경된다.
- 액션은 스토어에 보내는 일종의 인풋이라고 생각할 수 있다.



#### 4.3 액션 준비

액션 타입을 정의하여 변수로 정의

- 선택 사항이다.
- 타입을 문자열로 계속해서 지정할 때 실수를 유발할 가능성이 크다.
- 미리 정의한 변수를 사용하면, 스펠링에 주의를 덜 기울여도 된다.

액션 객체를 만들어 내는 함수(action creator)를 만드는 단계

- 하나의 액션 객체를 만들기 위해 하나의 함수를 만들어낸다.
- 액션의 타입은 미리 정의한 타입 변수로부터 가져와서 사용한다.

```javascript
// action type 변수
const ADD_TODO = 'ADD_TODO';

// action creator
function addTodo(text) {
  return {
    type: ADD_TODO,
    text,
  };
}
```



### 5. 리듀서(reducer)

리듀서는 한 마디로 변화를 일으키는 함수이다. 액션을 만들어서 발생시키면 리듀서가 현재 상태와 전달 받은 액션 객체를 파라미터로 받아 온다. 그리고 두 값을 참고하여 새로운 상태를 만들어서 반환한다. 

즉 액션을 주면, 액션이 적용되어 새로운 결과를 만들어 준다.

단순한 함수이고 pure function(순수 함수)이다. 또한 Immutable 이다.

```javascript
function reducer(previousState, action){
    // immutable 해야하기 때문에 새로운 state를 리턴해야한다.
    return newState;
}
```

> 실행되는 시점
>
> 1. 앱이 최초로 실행될 때 => 초기 state를 만들어서 할당한다.
> 2. 액션이 전달되었을 때

```javascript
import { ADD_TODO } from './actions';

function todoApp(previousState, action) {
  // 최초의 초기값 할당
  if (previousState === undefined) {
    return [];
  }

  // 변경이 일어나는 로직
  if (action.type === ADD_TODO) {
    return [...previousState, action.text];
  }

  // 변경 없음
  return previousState;
}
```



### 6. 스토어(store)

프로젝트에 리덕스를 적용하기 위해 스토어를 만들어야 한다.. 한 개의 프로젝트는 단일 스토어만 존재할 수 있다. 스토어 안에는 현재 애플리케이션 상태와 리듀서가 들어가 있다.



#### 6.1 스토어 만들기

```javascript
const store = createStore(reducer);
```

```javascript
// store.js
import { createStore } from 'reudx';
import { todoApp } from './reducers';

const store = createStore(todoApp);

export default store;
```



#### 6.2 Store의 내장 메서드

```javascript
store.getState();

store.dispatch(action); , store.dispatch(action_creator());

const unsubscribe = store.subscribe(()=> {});

store.replaceReducer(다른 리듀서);
```



##### 6.2.1 store.getState()

`store.getState()`는 store의 상태를 반환한다.



##### 6.2.2 store.dispatch

디스패치(dispatch)는 스토어의 내장 함수 중 하나인데 '액션을 발생시킨다'는 의미를 가직 있다. 따라서 dispatch(action)과 같은 형태로 사용한다.

**이 함수가 호출되면 스토어는 리듀서 함수를 실행시켜서 새로운 상태를 만들어준다.**

