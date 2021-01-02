# 라이프사이클

모든 리액트 컴포넌트에는 라이프사이클(수명 주기)가 존재한다.

 **컴포넌트의 수명은 페이지에 렌더링되기 전인 준비 과정에서 시작해서 페이지에서 사라질 때 끝이난다.**  이를 생명주기라고 하고 이러한 생명주기 안에서는 특정 시점에 자동으로 호출되는 메서드가 있는데, 이를 **라이프 사이클 이벤트**라고 한다.

라이프사이클 메서드는 클래스형 컴포넌트에서만 사용이 가능한데 최근에는 Hooks 기능을 사용해서 비슷한 작업을 처리할 수 있게 되었다.



## 1. 라이프사이클 메서드

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/react-life-cycle-2.png?raw=true" width="50%"></p>

라이프사이클 메서드의 종류는 총 9가지이다. will 접두사가 붙은 메서드는 어떤 작업을 작동하기 전이고, Did접두사가 붙은 메서드는 어떤 작업을 작동한 후에 실행되는 메서드이다.

라이프사이클은 총 세 가지 **마운트, 업데이트, 언마운트** 카테고리로 나뉜다. 



### 1.1 마운트

DOM이 생성되고 웹 브라우저상에 나타나는 것을 마운트(mount)라고 한다.

이 때 발생하는 메서드는 다음과 같다.

- **constructor** : 컴포넌트를 새로 만들 때마다 호출되는 클래스 생성자 메서드
- **getDerivedStateFromProps** : props에 있는 값을 state에 넣을 때 사용하는 메서드
- **render** : UI 렌더링 메서드
- **componentDidMout** : 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드

```jsx
class lifecycle extends Component {
  state = {
    count: 0,
  };

  render() {
    console.log('render');
    const { count } = this.state;
    return (
      <div>
        <p>{count}</p>
      </div>
    );
  }
  constructor(props) {
    super(props);
    console.log('constructor');
  }

  componentWillMount() {
    console.log('componentWillMount');
  }

  componentDidMount() {
    console.log('componentDidMount');
      
    // 1. 타이머
    // 2. API를 호출(비동기)
    // 3. 렌더 된 결과물에 무언가 한다.(최초에만 해야하는 일)
    // 4. unmount에서 하는 일과 반대
  }
}

export default lifecycle;
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/mountimg.PNG?raw=true" width="40%"></p>

**위 코드는 v16.3 이전이다.**



###  1.2 업데이트

컴포넌트는 다음과 같은 상황에 업데이트를 한다.

1. props가 바뀔 때 
2. state가 바뀔 때
3. 부모 컴포넌트가 리렌더링 될 때
4. this.forceUpdate로 강제로 렌더링을 트리거 할 때

업데이트와 관련된 메서드

- **getDerivedStateFromProps** : 이 메서드는 마운트 과정에서도 호출되며 업데이트가 시작하기 전에도 호출된다. props의 변화에 따라 state 값에도 변화를 주고 싶을 때 사용
- **shouldComponentUpdate** : 컴포넌트가 리렌더링을 해야 할지 말아야 할지를 결정하는 메서드이다. 이 메서드에서는 true 또는 false를 반환해야 하는데 true를 반환하면 다음 라이프사이클 메서드를 계속 실행하고, false를 반환하면 작업을 중지한다. 
- **getSnapshotBeforeUpdate** : 컴포넌트 변화를 DOM에 반영하기 바로 직전에 호출하는 메서드이다.
- **componentDidUpdate** : 컴포넌트의 업데이트 작업이 끝난 후 호출하는 메서드이다.



### 1.3 언마운트

마운트의 반대, 컴포넌트를 DOM에서 제거하는 것을 언마운트라고 한다.

- **componentWillUnmount** : 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드이다.



### 2. 메서드 상세 설명

#### 2.1 render 함수

라이프사이클의 유일한 필수 메서드이다. 이 메서드 안에서 this.props와 this.state에 접근할 수 있고, 리액트 요소를 반환한다. 요소는 div 같은 태그가 될 수도 있고, 따로 선언한 컴포넌트가 될 수도 있다. 아무것도 보여 주고 싶지 않다면 null이나 false를 반환한다. DOM 정보를 가져오거나 state에 변화를 줄 때는 componentDidMount에서 처리해야 한다.



#### 2.2 constructor

이 메서드에서는 초기 state를 정할 수 있다.



#### 2.3 getDerivedStateFromProps

리액트 v16.3 이후 새로 도입된 라이프사이클 메서드이다. props로 받아 온 값을 state에 동기화시키는 용도로 사용하며 컴포넌트가 마운트될 때와 업데이트될 때 호출된다.



#### 2.4 componentDidMount

이것은 컴포넌트를 만들고, 첫 렌더링을 다 마친 후 실행한다. 이 안에서 다른 자바스크립트 라이브러리 또는 프레임워크의 함수를 호출하거나 이벤트 등록, setTimeout, setInterval, 네트워크 요청 같은 비동기 작업을 처리한다.



#### 2.5 shouldComponentUpdate

props 또는 state를 변경했을 때, 리렌더링을 시작할지 여부를 지정하는 메서드이다. 컴포넌트를 만들 때 이 메서드를 따로 생성하지 않으면 언제나 true를 반환한다. 

이 메서드 안에서 현제 props와 state는 this.props와 this.state로 접근하고 새로 설정될 props또는 state는 nextProps와 nextState로 접근할 수 있다.



#### 2.6 getSnapshotBeforeUpdate

이것은 리액트 v16.3 이후 만든 메서드이다. 이 메서드는 render에서 만들어진 결과물이 브라우저에 실제로 반영되기 직전에 호출됩니다. 이 메서드에서 반환하는 값은 componentDidUpdate에서 세 번째 파라미터인 snapshot 값으로 전달 받을 수 있다. 주로 업데이트 직전의 값을 참고할 일이 있을 때 활용된다.



#### 2.7 componentDidUpdate

리렌더링을 완료한 후 실행된다. 업데이트가 끝난 직후이므로, DOM 처리를 해도 무관하다. 여기서는 prevProps 또는 prevState를 사용하여 컴포넌트가 이전에 가졌던 데이터에 접근할 수 있다. 또 getSnapshotBeforeUpdate에서 반환한 값이 있다면 여기서 snapshot 값을 전달받을 수 있다.



#### 2.8 componentWillUnMount 

컴포넌트를 DOM에서 제거할 때 실행한다. componentDidMount에서 등록한 이벤트, 타이머, 직접 생성한 DOM이 있다면 여기서 제거를 해야한다.



#### 2.9 componentDidCatch

v16에서 도입되었고, 컴포넌트 렌더링 도중에 에러가 발생했을 때 애플리케이션이 먹통이 되지 않고 오류 UI를 보여 줄 수 있게 해준다.

```jsx
componentDidCatch(error, info){
    this.setState({
        error : true
    });
    console.log({error, info});
}
```

이 메서드를 사용할 때는 컴포넌트 자신에게 발생하는 에러를 잡아낼 수 없고 자신의 this.props.children으로 전달되는 컴포넌트에서 발생하는 에러만 잡아낼 수 있다는 점을 알아야 한다.



<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/lifecycle.png?raw=true" width="90%"></p>