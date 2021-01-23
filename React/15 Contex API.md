# Contex API

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/contextAPI.PNG?raw=true" width="70%"></p>

**전역적으로 필요한 상태를 관리해야 할 때는 최상위 컴포넌트인 App에 state에 넣어서 관리한다.** 하지만 이럴 경우, 부모의 상태가 바뀌기 때문에 하위 컴포넌트들이 모두 다시 렌더링된다. 

이런 문제점을 해결하기 위해서 나온 것이 Context API이다. Context API를 사용하면 Context를 만들어 단 한 번에 원하는 값을 받아와서 사용할 수 있다는 장점이 있다. 



### <사용법>

#### 1. 데이터를 Set 하기

1.1 먼저 컨텍스트를 생성한다. 

```js
// contexts/PersonContext.js

import React from 'react';

const PersonContext = React.createContext();

export default PersonContext;
```

1.2 컨텍스트, 프로바이더를 사용한다.

```jsx
// index.js
import PersonContext from './contexts/PersonContext';

ReactDOM.render(
  <React.StrictMode>
    <PersonContext.Provider>
      <App />
    </PersonContext.Provider>
  </React.StrictMode>,
  document.getElementById('root'),
);
```

1.3 value를 사용한다.

```jsx
const persons = [
  { id: 0, name: 'mark', age: 39 },
  { id: 1, name: 'jaeyeon', age: 29 },
];

ReactDOM.render(
  <React.StrictMode>
    <PersonContext.Provider value={persons}>
      <App />
    </PersonContext.Provider>
  </React.StrictMode>,
  document.getElementById('root'),
);
```

다음의 과정이 끝나면 App이라는 컴포넌트 하위에 있는 컴포넌트들은 모두 context를 사용할 수 있게 된다.



#### 2. 데이터를 Get하기(1) - Consumer

2.1 컨텍스트를 가져온다.

2.2 컨텍스트, 컨슈머를 사용한다.

2.3 value를 사용한다.

```jsx
import React from 'react';
import PersonContext from '../contexts/PersonContext';

// Consumer를 사용하는 경우, class, function 관계 없다
export default function Example1() {
  return (
    <PersonContext.Consumer>
      {(value) => <p>{JSON.stringify(value)}</p>}
    </PersonContext.Consumer>
  );
}
```



#### 3. 데이터를 Get하기 (2) - class

3.1 static contextType에 컨텍스트를 설정한다.

3.2 this.context => value 이다.

```jsx
import React from 'react';
import PersonContext from '../contexts/PersonContext';

class Example2 extends React.Component {
  render() {
    return (
      <>
        <h1>this.context 사용</h1>
        <ul>
          {this.context.map((person) => (
            <li>{person.name}</li>
          ))}
        </ul>
      </>
    );
  }
  static contextType = PersonContext;
}

export default Example2;
```



#### 4. 데이터를 Get하기 (3) - useContext

4.1 useContext로 컨텍스트를 인자로 호출한다.

4.2 useContext의 리턴이 value 이다.

```jsx
import React, { useContext } from 'react';
import PersonContext from '../contexts/PersonContext';

export default function Example3() {
  const persons = useContext(PersonContext);
  return (
    <>
      <h1>useContext 사용</h1>
      <ul>
        {persons.map((person) => (
          <li>{person.name}</li>
        ))}
      </ul>
    </>
  );
}
```



#### 5. Person context의 데이터를 바꾸려면?

```jsx
// App.js
import logo from './logo.svg';
import './App.css';
import Example1 from './components/Example1';
import Example2 from './components/Example2';
import Example3 from './components/Example3';
import PersonContext from './contexts/PersonContext';
import { useState } from 'react';

function App() {
  const [persons, setPersons] = useState([
    { id: 0, name: 'mark', age: 39 },
    { id: 1, name: 'jaeyeon', age: 29 },
  ]);

  const add = () => {
    setPersons([...persons, { id: 2, name: 'React', age: 10 }]);
  };

  return (
    <PersonContext.Provider value={{ persons, add }}>
      <div className='App'>
        <header className='App-header'>
          <Example1 />
          <Example2 />
          <Example3 />
        </header>
      </div>
    </PersonContext.Provider>
  );
}

export default App;
```

다음과 같이 최상위 컴포넌트인 App.js에서 persons에 useState를 사용하여 데이터를 Set해주고 useState의 값을 Provider의 value라는 props에 값으로 전달해준다. 

```jsx
// Example3.jsx
import React, { useContext } from 'react';
import PersonContext from '../contexts/PersonContext';

export default function Example3() {
  const { persons, add } = useContext(PersonContext);
  return (
    <>
      <h1>useContext 사용</h1>
      <ul>
        {persons.map((person) => (
          <li>{person.name}</li>
        ))}
      </ul>
      <button onClick={click}>추가</button>
    </>
  );
  function click() {
    add();
  }
}
```

