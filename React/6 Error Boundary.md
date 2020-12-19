# Error Boundary

UI를 담당하는 부분에서 에러가 발생했을 때는 애플리케이션을 중단시키지 않고 사용자들에게 정보를 제공해줘야 한다. 하지만 과거에는 컴포넌트 내부에서 에러가 발생하면 React 내부 상태를 훼손하고 에러를 띄워주었다. 이런 문제점을 해결하기 위해 나온 것이 Error Boundary 컴포넌트이다.

Error Boundary 컴포넌트는 컴포넌트 트리구조 어디에서 에러가 발생해도 이를 캐치하고 fallback UI를 렌더링해준다.

단, **트리 내에서 하위에 존재하는 컴포넌트의 에러만을 캐치한다.** 



## 1. 사용법

### 1.1 설치

```bash
$npm install --save react-error-boudary
```

```jsx
import { ErrorBoundary } from "react-error-boundary"
```



### 1.2 작성법

ErrorBoundary 컴포넌트는 컴포넌트 트리의 가장 상위에 위치시키는 것이 일반적이다. 다음과 같이 사용할 수 있다.

```jsx
class App extends React.Component {
  render() {
    return (
      <ErrorBoundary>
        <div>
          <header className='App-header'>
            <Button />
          </header>
        </div>
      </ErrorBoundary>
    );
  }
}
```

ErrorBoundary를 사용할 때 FallbackComponent를 사용해서 에러처리가 된 화면을 렌더링 해줄 수 있는데 이를 ErrorBoundary 컴포넌트의 props로 전달시켜준다.

```jsx
function ErrorPage() {
  return <div>Error 발생했습니다!</div>;
}

class App extends React.Component {
  render() {
    return (
      <ErrorBoundary FallbackComponent={ErrorPage}>
        <div>
          <header className='App-header'>
            <Button />
          </header>
        </div>
      </ErrorBoundary>
    );
  }
}
```

ErrorPage라는 컴포넌트를 생성해서 FallbackComponent의 값으로 넘겨준다. 개발 모드에서는 확인할 수 없고, 빌드를 했을 때 확인할 수 있다.



### 2. 주의 사항

ErrorBoundary는 다음의 에러들은 캐치하지 않는다.

- 이벤트 핸들러
- 비동기 코드(ex_setTimeOut())
- 서버 사이드 렌더링
- ErrorBoundary 자체의 에러



