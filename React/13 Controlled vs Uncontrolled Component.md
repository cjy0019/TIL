# Controlled vs Uncontrolled Component

React는 컴포넌트에 관한 두 가지 개념을 가지고  설명한다. Controlled Component라고 불리는 제어 컴포넌트, 그리고 Uncontrolled Component라고 불리는 비제어 컴포넌트가 그 주인공이다.

엘리먼트의 상태를 누가 관리하느냐

- 엘리먼트를 가지고 있는 컴포넌트가 관리
  - controlled
- 엘리먼트의 상태를 관리하지 않고 ,엘리먼트의 참조만 컴포넌트가 소유
  - uncontrolled



## 1. Controlled Component

React는 내부의 state를 'Single Source of Truth(신뢰 가능한 단일소스)'로 관리하려는 설계원칙을 가지고 있다. 즉, **모든 데이터요소를 한 곳에서만 제어 또는 편집하도록 조작하는것이다.**

자식 컴포넌트가 data가 필요할 경우 해당 data는 가장 가까운 공통 부모 컴포넌트에게서만 props의 형태로 전달받아서 사용해야 한다.

대부분의 HTML 엘리먼트들은 엘리먼트가 내부적으로 어떤 데이터를 가지지 않기 때문에 문제 될 것이 없다.

하지만 HTML 엘리먼트 중 자체적으로 data를 가지는 엘리먼트들이 있는데 `<input>, <textarea>, <select>, <checkbox>`등이 있다.

- 위의 태그들은 user가 DOM에서 어떤 정보를 입력하거나 선택할 경우, 해당 정보를 HTML 엘리먼트가 직접 보관하게 되는데, 이는 Single Source of Truth원칙에 위배된다.
- 이를 해결하기 위해 Controlled 컴포넌트 개념이 등장했다.

**controlled Component**는 사용자 입력에서 발생하는 이벤트를 제어해서 HTML 엘리먼트에 들어온 정보를 컴포넌트 내부에 state로 저장하고 state를 기반으로 엘리먼트를 다시 re-rendering 시켜서 엘리먼트의 value를 변경시키는 방식이라고 할 수 있다.

```jsx
// Controlled Component
class Form extends Component{
    constructor(){
        super();
        this.state = {
            name : '',
        };
    }
    handleNameChange = (e) => {
        this.setState({ name : e.target.value });
    };
	
	render() {
        return (
            <div>
                <input
                  type="text"
                  value={this.state.name}
                  onChange={this.handleNameChange}
                />
            </div>
        )
    }
}
```

위의 코드를 보면

1. user가 정보를 input에 입력하면 onChange 메서드가 실행되면서 컴포넌트의 내부 state값을 user가 입력한 값으로 변경시킨다.
2. state가 update 되면서 컴포넌트가 re-rendering 되는데, re-rendering시 input 태그의 value에 현재 변경된 state를 넣어서 실시간으로 값이 변경되는 것을 화면에 반영할 수 있다.

input에 change 이벤트가 발생하는 동시에 컴포넌트의 state가 실시간으로 업테이트되기때문에 'Single Source of Truth(신뢰가능한 단일소스)'원칙을 기반으로 컴포넌트가 작동할수있다.

controlled component의 장점은 react가 내부적으로 관리하는 state와 유저가 입력하는 정보간의 sync가 맞기때문에 실시간 작업처리가 가능하다.



## Uncontrolled Component

**Uncontrolled Component**란 DOM 자체에서 데이터가 다루어진다. 즉, 태그 내부적으로 자기 자신의 state를 가지고 있다. state 업데이트에 대한 이벤트 핸들러를 작성하는 대신, ref를 사용하여 DOM에서 값을 가져올 수 있다.

```jsx
// Uncontrolled Component

class UserProfile extends React.Component {
    constructor(props){
        super(props);
        this.handleSubmit = this.handleSubmit.bind(this);
        this.input = React.createRef();
    }
    
    handleSubmit(event){
        alert('A name was submitted: ' + this.input.current.value);
        event.preventDefault();
    }
    
    render() {
        return (
            <form onSubmit={this.handleSubmit}>
                <label>
                    {'Name:'}
                    <input type="text" ref={this.input} />
                </label>
                <input type="submit" value="Submit" />
            </form>
        )
    }
}
```

1. user가 input에 값을 입력해도 컴포넌트내부에서는 아무동작도 발생하지 않는다.
2. input에 ref 속성을 부여해서 input의 값을 참조만 할수있다.
3. form이 submit되면 handleSubmit 함수에서 `this.input.current.value`로 user가 입력한 데이터에 접근할수 있다.

컴포넌트 내부에서 실시간으로 user정보를 관리하는 것이 아니기 때문에 실시간으로 작업을 처리하고자 할때는 부적합한 방식이다.



**결론**

- **controlled component**는 자체 state값을 가질 수 있는 태그가 자식엘리먼트 일때도 그 자식 엘리먼트의 state값들도 부모컴포넌트에서 control한다.
- **uncontrolled component**는 자체 state를 가질 수 있는 태그가 자식엘리먼트 일때 그 값을 직접 control 하는 것이 아니고 참조하여 사용한다.



