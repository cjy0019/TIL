# Styled Components

컴포넌트 스타일링의 또 다른 패러다임은 자바스크립트 파일 안에 스타일을 선언하는 방식이다. 'CSS-in-JS'라고 부르기도 하는데 관련 라이브러리가 많지만 가장 대표적으로 사용되는 컴포넌트인 styled-components에 대해 학습해보자.

styled-components를 사용하면 자바스크립트 파일 하나에 스타일까지 작성할 수 있기 때문에 .css 또는 .scss 확장자를 가진 스타일 파일로 따로 만들지 않아도 된다. 비슷한 라이브러리로는 emotion이 있다.

## 1. 설치 및 사용법

```bash
$ npx create-react-app styled-components-example
$ cd styled-components-exmaple
$ npm i styled-components
```



src/components/Button.jsx 라는 컴포넌트를 생성한다. 

```jsx
import React from 'react';
import styled from 'styled-components';

const StyledButton = styled.button``;
// styled.{내장 html 태그를 의미한다} h1, a, button 등 태그 사용이 가능하다

export default StyledButton;
```

생성된 버튼 요소를 브라우저에서 확인해보면 다음과 같이 저절로 class가 생성되었음을 알 수 있다. 자동으로 class를 생성해주기는 하지만 스코핑 문제를 기술적으로 완전히 해결했다고 볼 수는 없다.(최대한 클래스명을 중복되지 않도록 하자는 의미)

```html
<button class="sc-bdfBwQ">버튼</button>
// sc = styled-component
```



## 2. style

```javascript
import styled from 'styled-components';

const StyledButton = styled.button`
  background: transparent;
  border-radius: 3px;
  border: 2px solid palevioletred;
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;
`;

export default StyledButton;
```

백틱으로 감싼 부분 안쪽이 CSS부분이라고 생각할 수 있다. CSS와 같은 형식으로 코딩해 줄 수 있다. 다만 문자열이기 때문에 자동완성이 적용되지 않는다는 단점이 있다.

```html
<button class="sc-jSgupP hxWdXt">버튼</button>
// 앞에 sc-jsgupP라는 클래스가 버튼을 가리키고 있고 styled.button으로 작성한 css 스타일링은 hxwdXt라는 클래스에 따로 저장된다.
```



### 2.1 특징

```jsx
<Button primary>버튼</Button>
<Button>버튼</Button>
```

다음과 같이 클래스가 다른 두 개의 버튼 컴포넌트를 사용하려고 할 때, 기존의 방법으로는 버튼 컴포넌트를 두개 만들어서 사용해야 했다. 단지 style의 color 속성만 바꾼다할지라도 하지만 styled-components를 이용하여 조금 더 간편하게 작성해줄 수 있다.

```javascript
import styled, { css } from 'styled-components';

const StyledButton = styled.button`
  background: transparent;
  border-radius: 3px;
  border: 2px solid palevioletred;
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;

  ${(props) => {
    props.primary &&
    css`
        background : red;
        color : white;
      `;}}
`;

export default StyledButton;
```

위의 코드처럼 CSS 파트에 함수를 작성할 수 있는데 함수의 파라미터로는 항상 props가 전달되고 return 으로는 css가 전달된다. 예시처럼 primary클래스가 있을 때 background, color를 간단하게 교체해줄 수 있다.



### 2.1.1 override

원래 스타일링이 되어져 있는 버튼 컴포넌트에 오버라이딩을 하고 싶을 땐 다음과 같이 작성할 수 있다.

```jsx
export const PrimaryStyledButton = styled(StyledButton)`
  background: violet;
  color: white;
`;
```



### 2.1.2 as

기본 스타일링된 컴포넌트를 사용하지만 다른 태그를 이용하고 싶을 땐 as키워드를 사용할 수 있다.

```jsx
<Button as="a" href="/hello">버튼</Button>
// 기존 버튼 컴포넌트의 스타일이 적용된 상태에서 태그를 a 태그로 바꿔준다.
```



### 2.1.3 style 변경

기본 스타일 된 컴포넌트에서 프로퍼티 값 하나만 변경하고 싶다면 다음과 같이 할 수 있다. props가 존재하는 스타일의 border 색만 바꾸기

```jsx
// 컴포넌트 생략 부분...
<MyButton>내버튼</MyButton>
<MyButton color='green'>내버튼</MyButton>
```

```jsx
const StyledMyButton = styled(MyButton)`
  background: transparent;
  border-radius: 3px;
  border: 2px solid ${(props)=> props.color || "palevioletred"};
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;
  cursor: pointer;
`;
```

**hover case**

```jsx
const StyledMyButton = styled(MyButton)`
  background: ${(props) => props.color && 'gold'};
  border-radius: 3px;
  border: 2px solid palevioletred;
  color: palevioletred;
  margin: 0 1em;
  padding: 0.25em 1em;
  cursor: pointer;

  :hover {
    border: 4px solid red;
  }
`;
```



### 2.14 global style

createGlobalStyle 이라는 컴포넌트를 생성해서 다음과 같이 넣어주면 글로벌 속성으로 스타일이 적용된다.

```jsx
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`{
  button {
    font-size: 30px;
  }
}`;
```

```jsx
function App() {
  return (
    <div className='App'>
      <GlobalStyle />
      <header className='App-header'>
        <img src={logo} className='App-logo' alt='logo' />
        <p>
          <Button primary>버튼</Button>
          <Button error>버튼</Button>
          <Button>버튼</Button>
        </p>
      </header>
    </div>
  );
}
```



### 2.15 어트리뷰트 변경

StyledA라는 컴포넌트에 속성을 변경해주고 싶을 때 사용하는 방법이다.

```jsx
// StyledA.jsx
import styled from 'styled-components';

const StyledA = styled.a.attrs((props) => ({
  color: props.color || 'green',
  target: '_blank',
}))`
  color: ${(props) => props.color};
`;

export default StyledA;

```

```html
// app.js
<p>
    <StyledA color='orange' href='https://www.naver.com'>
        태그 1
    </StyledA>
</p>
```

`target:_blank` 속성을 지정해주고 싶을 때 `styled.a.attrs()`라는 함수를 사용한다. 사용할 때 인자로 props를 주고 return 값으로 여러가지 속성들을 지정해줄 수 있다.



**스타일 작성 방법**

1. component.jsx, component.css
2. component.jsx, component.module.css
3. component.jsx, component.style.jsx