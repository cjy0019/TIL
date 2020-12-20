# React 라우팅

## 1. Routing 이란?

라우팅이란 출발지에서 목적지까지의 경로를 결정하는 기능이라고 할 수 있다. 애플리케이션의 라우팅은 사용자가 태스크를 수행하기 위해 어떤 화면(view)에서 다른 화면으로 화면을 전환하는 내비게이션을 관리하기 위한 기능을 의미한다. 일반적으로 사용자자 요청한 URL 또는 이벤트를 해석하고 새로운 페이지로 전환하기 위한 데이터를 취득하기 위해 서버에 필요 데이터를 요청하고 화면을 전환하는 위한 일련의 행위를 말한다.

**브라우저가 화면을 전환하는 경우**

1. 브라우저의 주소창에 URL을 입력하면 해당 페이지로 이동한다.
2. 웹페이지의 링크를 클릭하면 해당 페이지로 이동한다.
3. 브라우저의 뒤로가기 또는 앞으로가기 버튼을 클릭하면 사용자가 방문한 웹페이지의 기록의 뒤 또는 앞으로 이동한다.

AJAX 요청에 의해 서버로부터 데이터를 응답받아 화면을 생성하는 경우, 브라우저의 주소창의 URL은 변경되지 않는다. 이는 사용자의 방문 history를 관리할 수 없음을 의미하며, SEO(검색엔진 최적화) 이슈의 발생 원인이기도 하다. **history 관리를 위해서는 각 페이지는 브라우저의 주소창에서 구별할 수 있는 유일한 URL을 소유하여야 한다.**



## 2. 전통적인 Routing

사용자가 `<a href="route.html">`을 클릭하면 해당 리소스를 서버에 요청한다. 이 때 서버는 html로 화면을 표시하기 위한 리소스를 응답한다. 이를 서버 렌더링이라고 한다. 이 때 이전 페이지에서 수신된 html로 전환하는 과정에서 전체 페이지를 다시 렌더링하므로 새로고침이 발생한다.

<p align="center"><img src="https://poiemaweb.com/img/traditional-webpage-lifecycle.png" width="50%"></p>

이 방식은 JS가 필요없이 응답된 html만으로 렌더링이 가능하고 각 페이지 마다 고유의 URL이 존재하므로 history 관리 및 SEO 대응에 문제가 없지만 중복된 리소스를 요청마다 수신 해야되고 전체 페이지를 다시 렌더링 해야하므로 성능상 좋지 않다. 



## 3. 모던 SPA 라우팅

SPA는 기본적으로 웹 애플리케이션에 필요한 모든 정적 리소스를 최초에 한번 다운로드한다. 이후 새로운 페이지 요청 시, 페이지 갱신에 필요한 데이터만을 전달받아 페이지를 갱신하므로 전체적인 트래픽을 감소할 수 있고, 변경되는 부분만 갱신하므로 네이티브 앱과 유사한 사용자 경험을 제공할 수 있다.

> SPA는 초기 구동 속도가 상대적으로 느리다. 하지만 SPA는 웹페이지보다는 애플리케이션에 적합한 기술이므로 트래픽의 감소와 속도, 사용성, 반응성 향상 등의 장점을 생각한다면 이는 결정적인 단점은 아니다.

### 3.1 SPA 라우팅 과정

1. 브라우저에게 최초의 '/' 경로로 요청을 한다.
2. React Web App을 내려준다.
3. 내려받은 React App에서 '/' 경로에 맞는 컴포넌트를 보여준다.
4. React App 에서 다른 페이지로 이동하는 동작을 수행한다.
5. 새로운 경로에 맞는 컴포넌트를 보여준다.



## 4. REACT ROUTER

리액트에서 사용되는 가장 대표적인 라우팅 패키지인 'REACT ROUTER'에 대해 알아보자.

[REACT ROUTER](https://reactrouter.com/)

<img src="https://github.com/cjy0019/TIL/blob/master/images/react-router-logo.PNG?raw=true" width="20%">

- cra 에 기본으로 내장된 패키지가 아니다.
- react-router-dom은 Facebook의 공식 패키지는 아니지만 가장 대표적으로 많이 쓰이고 있다.

### 4.1 사용법

#### 4.1 프로젝트 생성

```bash
$ npx create-react-app react-router-example
$ cd react-router-example
```

#### 4.2 라우터 돔 패키지 설치

```bash
$ npm i react-router-dom
```

#### 4.3 특정 경로에서 보여줄 컴포넌트를 작성

- '/' => Home 컴포넌트
- '/profile' => profile 컴포넌트
- '/about' => About 컴포넌트

```jsx
// App.js
function App() {
  return (
    <div className='App'>
      <Home />
      <Profile />
      <About />
    </div>
  );
}
```

```jsx
// /pages/Home.jsx
import React from 'react';

export default function Home() {
  return (
    <div>
      <h1>Home</h1>
    </div>
  );
}
```

나머지 Profile.jsx, About.jsx도 동일하게 만든다. 

#### 4.4 BrowserRouter

```jsx
// App.js
import{ BrowserRouter } from 'react-router-dom';

// 남이 만든 컴포넌트 => 사용법을 숙지해야한다.
// 컴포넌트의 사용법은 곧 => props를 어떻게 설정하는가에 달려있다.

function App() {
  return (
    <BrowserRouter>
      <Home />
      <Profile />
      <About />
    </BrowserRouter>
  );
}
```

**import 주의 사항**

> 일반적으로 import문에서 대문자로 시작하면 클래스이거나 컴포넌트이다. 반대로 소문자일 경우에는 변수이거나 함수이다.

#### 4.5 Route

**예시**

```jsx
<Route path="주소규칙" component={보여줄 컴포넌트} />
```

```jsx
import { BrowserRouter, Route } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Route path='/' component={Home} />
      <Route path='/profile' component={Profile} />
      <Route path='/about' component={About} />
    </BrowserRouter>
  );
}
```

주소창에 `localhost:3000/`을 입력하면 Home이라는 글자가 잘나오지만 /profile에 들어가보면 다음과 같이 예상과는 다르게 나온다. react-router-dom의 매칭 알고리즘에 의해서 '/'도 포함시키고 '/profile'도 포함한 페이지를 찾아서 렌더링해주기 때문에 나타난 결과이다. 이런 현상을 해결하기 위해서 **exact**라는 키워드를 사용해준다.

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/router-examp.PNG?raw=true" width="50%"></p>

```jsx
function App() {
  return (
    <BrowserRouter>
      <Route path='/' exact component={Home} />
      <Route path='/profile' component={Profile} />
      <Route path='/about' component={About} />
    </BrowserRouter>
  );
}
```

#### 4.6 Dynamic Routing

정해지지 않은 경로에 대한 라우팅을 다이내믹 라우팅이라고 한다.

#### 4.6.1 /Profile/1

```jsx
function App() {
  return (
    <BrowserRouter>
      <Route path='/' exact component={Home} />
      <Route path='/profile' exact component={Profile} />
      <Route path='/profile/:id' component={Profile} />
      <Route path='/about' component={About} />
    </BrowserRouter>
  );
}
```

/profile/:id 에서 id라는 값을 사용하기 위해서 profile이라는 컴포넌트의 props를 출력해본다. Route라는 컴포넌트가 profile 컴포넌트에 props를 넘겨주고 렌더링하고 있다고 볼 수 있다.

```jsx
// profile.jsx
import React from 'react';

export default function Profile(props) {
  console.log(props);
  return (
    <div>
      <h1>Profile</h1>
    </div>
  );
}
```

다음과 같이 props가 출력되는 것을 볼 수 있다.

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/profile-props.PNG?raw=true" width="70%"></p>

props라는 객체를 확인해보면 match라는 객체 안에 params라는 프로퍼티의 객체의 값으로 id 값을 가지고 있음을 확인할 수 있다. params의 id를 찾아내고 이를 이용해 다음과 같이 활용할 수 있다.

```jsx
export default function Profile({ history, location, match }) {
  const id = match.params.id;

  if (id === undefined) {
    return (
      <div>
        <h1>Profile</h1>
      </div>
    );
  }
  return (
    <div>
      <h1>profile: {id}</h1>
    </div>
  );
}
```

**주의 : url을 불러왔기 때문에 string 타입이다.**

#### 4.6.2 about?id=3

**쿼리 스트링이란?**

**사용자가 입력된 데이터를 전달하는 방법 중의 하나로, url 주소에 미리 협의된 데이터를 파라미터를 통해 넘기는 것을 말한다.**

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/search-about.PNG?raw=true" width="70%"></p>

props를 통해 다음과 같이 전달되어 지는데 "?id=3" 이라는 문자열이 출력 된 것을 확인할 수 있다. 문자열에서 3이라는 값만 가져오고 싶다면 여러가지 방법을 사용할 수 있다.

```jsx
// About.jsx
export default function About(props) {
  const search = props.location.search;
  
  return (
    <div>
      <h1>About</h1>
    </div>
  );
}
```

1. `search.slice(-1)`
2. `search.split('id=')[1]`

다음과 같은 방법을 사용하면, id가 한자리 값이 아닐 경우, 또는 ?id=34&name=mark 같은 쿼리 스트링이 올 경우에 큰 문제가 생긴다. 물론 해결책이 있겠지만 매우 번거롭다. 이를 해결해주는 브라우저의 내장 객체가 있는데 이를 활용하면 간단하게 해결할 수 있다.

#### 4.6.3 URLSearchParams

```jsx
const searchParams = new URLSearchParams(search);
searchParams.get('id');
```

하지만 URLSearchParams도 문제가 없는 것은 아니다. IE를 지원하지 않기 때문에 크로스 브라우징 이슈가 발생한다.

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/urlsearchparams.PNG?raw=true" width="50%"></p>

#### 4.6.4 query-string

URLSearchParams 처럼 내장 객체가 아닌 외부 라이브러리를 사용하는 방법도 있다. 그 중에서 대표적인 `query-string`이라는 라이브러리를 사용해 볼 것이다.

```bash
$ npm i query-string
```

```jsx
import qs from 'query-string';

export default function About(props) {
  const search = props.location.search;
  
  const queryString = qs.parse(search);
  console.log(queryString.id);  // 3
    
  return (
    <div>
      <h1>About</h1>
    </div>
  );
}
```



#### 4.7 switch

```jsx
function App() {
  return (
    <BrowserRouter>
      <Switch>
        <Route path='/' component={Home} />
        <Route path='/profile' component={Profile} />  
        <Route path='/profile/:id' component={Profile} />  
        <Route path='/about' component={About} />
      </Switch>
    </BrowserRouter>
  );
}
```

Switch는 위와 같이 사용한다. 만약에 각 비교문이 포함 관계에 있다면 순서에 따라 결과가 달라진다. 즉 switch문은 위에서 아래로 경로를 비교하면서 올바른 라우팅 주소를 찾는다. 하지만 위에 코드와 같이 exact 키워드를 사용하지 않으면 /profile, /about 을 사용해도 가장 위에서 걸리기 때문에 Home만 출력할 것이다. 따라서 exact 키워드를 쓰지 않고 switch문을 활용하려면 순서를 명확히 구분해줘야 한다.

```jsx
function App() {
  return (
    <BrowserRouter>
      <Switch>
        <Route path='/about' component={About} />
        <Route path='/profile/:id' component={Profile} />
        <Route path='/profile' component={Profile} />
        <Route path='/' component={Home} />
      </Switch>
    </BrowserRouter>
  );
}
```

#### 4.7.1 Switch를 이용한 NotFound 처리

```jsx
function App() {
  return (
    <ErrorBoundary FallbackComponent = {ErrorPage}>
      <BrowserRouter>
        <Switch>
          <Route path='/' component={Home} />
          <Route path='/profile' component={Profile} />
          <Route path='/profile/:id' component={Profile} />
          <Route path='/about' component={About} />
          <Route component={NotFound} />
        </Switch>
      </BrowserRouter>
    </ErrorBoundary>
  );
}
```

**ErrorBoundary**를 이용해서 다음과 같이 NotFound와 에러 페이지를 모두 렌더링 가능하게 표현할 수 있다.



#### 4.8 JSX 링크로 라우팅 이동하기

react-router-dom 패키지에 저장되어 있는 Link 컴포넌트로 라우팅을 할 수 있다. 일반적으로 사용자들은 주소창에 /about 과 같이 주소로 접속하지 않고 페이지 내에 `<a>`태그를 통해서 이동하는데 이 때 서버에 요청하는 상황이 발생한다. react-router-dom의 Link를 사용하면 클라이언트 사이드에서 해결할 수 있다.

```jsx
function App() {
  return (
    <ErrorBoundary FallbackComponent={ErrorPage}>
      <BrowserRouter>
        <div>
          <ul>
            <li>
              <Link to='/' />
              home
            </li>
            <li>
              <Link to='/profile' />
              profile
            </li>
            <li>
              <Link to='/profile/3' />
              profile : 3
            </li>
            <li>
              <Link to='/about' />
              about
            </li>
            <li>
              <Link to='/about?id=5' />
              about : 5
            </li>
          </ul>
        </div>
        <Switch>
          <Route path='/' component={Home} />
          <Route path='/profile' component={Profile} />
          <Route path='/profile/:id' component={Profile} />
          <Route path='/about' component={About} />
          <Route component={NotFound} />
        </Switch>
      </BrowserRouter>
    </ErrorBoundary>
  );
}
```

사실 Link 컴포넌트도 내부에서는 a태그를 사용하고 있다. 브라우저가 인지 못하게 history API를 이용해서 주소창만 바꾸고 Switch문을 돌면서 주소에 맞는 라우팅만 보여주는 것이다.



#### 4.9 JS로 라우팅 이동하기

login.jsx 라는 컴포넌트를 생성하고 안에서 버튼을 이용해 라우팅 할 때 다음과 같이 작성할 수 있다. (중간 생략)

```jsx
function App() {
  return (
    <ErrorBoundary FallbackComponent={ErrorPage}>
      <BrowserRouter>
        <div>
          <ul>
            <li>
              <Link to='/Login'>Login</Link>
            </li>
          </ul>
        </div>
        <Switch>
          <Route path='/about' component={About} />
          <Route path='/profile/:id' component={Profile} />
          <Route path='/profile' component={Profile} />
          <Route path='/Login' component={Login} />
          <Route path='/' component={Home} />
          <Route component={NotFound} />
        </Switch>
      </BrowserRouter>
    </ErrorBoundary>
  );
}
```

```jsx
// login.jsx
export default function Login(props) {
  console.log(props);
  return (
    <div>
      <h1>Login</h1>
      <button
        onClick={() => {
          setTimeout(() => {
            props.history.push('/');
          }, 2000);
        }}>
        로그인
      </button>
    </div>
  );
}
```

JS에서는 `window.location.assign()`으로 라우팅을 이동할 수 있지만 서버에 요청하는 문제가 생긴다. 따라서 컴포넌트의 props의 `props.history.push('/')`를 사용하면 문제를 해결할 수 있다.

하지만 Login => A => B => C => Button 처럼 로그인 안에 여러 중첩 구조를 가지고 있다면 실수를 유발 시킬 수 있다.

#### 4.9.1 withRouter

```jsx
// Button.jsx
import React from 'react';
import { withRouter } from 'react-router-dom'; // withRouter 함수

function Button(props) {
  return (
    <button
      onClick={() => {
        setTimeout(() => {
          props.history.push('/');
        }, 700);
      }}>
      pretty button
    </button>
  );
}
const Newbutton = withRouter(Button)

export default Newbutton;
```

withRouter는 고차 컴포넌트(HOC)이다.

고차 컴포넌트는 간단히 말해서 function이며 매개변수로 컴포넌트를 받고, 리턴으로 컴포넌트를 해준다고 할 수 있다.



#### 4.10 Redirect

