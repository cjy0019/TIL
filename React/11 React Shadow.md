# React Shadow & antd

## 1. 웹 컴포넌트

**MDN**

> 웹 컴포넌트는 그 기능을 나머지 코드로부터 캡슐화하여 재사용 가능한 커스텀 엘리먼트를 생성하고 웹 앱에서 활용할 수 있도록 해주는 다양한 기술들의 모음이다. 
>
> 웹 컴포넌트는 다음 문제들을 해결하는 것을 목표로 한다. 
>
> 세 가지 기술들로 구성되며, 재사용을 원하는 어느곳이든 코드 충돌에 대한 걱정이 없는 캡슐화된 기능을 갖춘 다용도의 커스텀 엘리먼트를 생성하기 위해 함께 사용될 수 있습니다.

- **Custom element** : 사용자 인터페이스에서 원하는대로 사용할 수있는 사용자 정의 요소 및 해당 동작을 정의 할 수있는 JavaScript API 세트이다.
- **Shadow DOM** : 새로운 document를 만든다고 볼 수 있다. 마치 html 요소안에 또 다른 새로운 document 가 있다는 것이다. 메인 다큐먼트 DOM 으로부터 독립적으로  document를 추가하고 연관된 기능을 제어하기 위한 JavaScript API 의 집합. 이 방법으로 엘리먼트의 기능을 프라이빗하게 유지할 수 있고 document의 다른 부분과의 충돌에 대한 걱정 없이 스크립트와 스타일을 작성할 수 있습니다.
- **HTML 템플릿**: `template` 과 `slot` 엘리먼트는 렌더링된 페이지에 나타나지 않는 마크업 템플릿을 작성할 수 있게 해줍니다. 그 후, 커스텀 엘리먼트의 구조를 기반으로 여러번 재사용할 수 있습니다.



## 2. react-shadow

**설치**

```bash
$ npm i react-shadow
```

```jsx
import React from 'react';
import root from 'react-shadow';

const style = `
p{
  color:orange
}`;

export default function Shadow() {
  return (
    <root.div>
      <p>안녕하세요</p>
      <style type='text/css'>{style}</style>
    </root.div>
  );
}
```

`root.div`안에서만 style이 적용된다. root와 바깥쪽은 완전 분리하여 스코핑을 도와준다.

react shadow를 사용하면 완전히 캡슐화를 할 수 있지만 css style을 문자열로 작성해야 한다는 단점을 가지고 있다.

1) css 파일을 별도로 관리하면서 필요할 때 가져오는 방법과 

2) 스타일 컴포넌트와 연결하는 방법이 있다.(모든 스타일을 재작성 해야하기 때문에)

방법2는 용량이 커질 수 있다는 단점이 존재하므로 주의하여 사용 해야한다.



## 3. Ant Design

**설치**

마찬가지로 npm을 통해 install 해준다.

```bash
$ npm i antd
```

다음으로 antd를 import 해줘야 하는데 전역 스타일이 있는 곳에 import를 해준다. 기본 cra에서는 index.js에 해준다.

#### 3.1 사용법

**전역 사용**

```jsx
// index.js
import 'antd/dist/antd.css';
// App.js
import { DatePicker } from 'antd';
function App() {
  return (
    <div className='App'>
      <header className='App-header'>
        <img src={logo} className='App-logo' alt='logo' />
        <DatePicker />
      </header>
    </div>
```

- 위의 코드와 같이 적용하면 antd.css에 있는 모든 스타일을 불러오고 용량, 성능 면에서 문제가 생긴다.
- 따라서 모듈화해서 사용한다.



**modularized 1**

```jsx
// App.js
import DatePicker from 'antd/es/date-picker';
import 'antd/es/date-picker/style/css';
```

- 전역 스타일을 사용할 때 보다 성능이나 용량면에서 낫지만 사용할 때마다 import를 해줘야 하기 때문에 번거롭다.



**modularized 2**

```bash
$ npm run eject
$ npm install babel-plugin-import --save-dev
```

```json
{
  ...
  "babel": {
    "presets": [
      "react-app"
    ],
    "plugins": [
      [
        "import",
        {
          "libraryName": "antd",
          "libraryDirectory": "es",
          "style": "css"
        }
      ]
    ]
  },
  ...
}
```

- 위 코드를 통해 import할 때 libraryName이 antd이면 자동으로 css를 추가해주는 설정을 해줄 수 있다.
- eject에 따른 단점이 존재한다.



#### 3.2 icons

**설치**

```bash
$ npm install @ant-design/icons
```

**사용법**

1. [antd-icons](https://ant.design/components/icon/)에서 원하는 아이콘을 찾는다.
2. 복사해서 원하는 곳에 삽입한다.
3. import 해준다. 예시)  facebook 아이콘

```jsx
// App.js
import { FacebookOutlined } from '@ant-design/icons';

function App() {
  return (
    <div className='App'>
      <GlobalStyle />
      <header className='App-header'>
        <img src={logo} className='App-logo' alt='logo' />
        <DatePicker />
        <FacebookOutlined />
      </header>
    </div>
```



#### 3.3 레이아웃

##### 3.3.1 Row & Col

antd에서는 Row 와 Col이라는 컴포넌트를 사용해서 디자인을 할 수 있다. Row는 말 그대로 행을 뜻하고 Col은 열을 뜻한다. Col의 props로 span을 줄 수 있는데 요소의 크기를 지정할 수 있다. 뷰포트 전체는 24개의 Col로 구성되어있는데 span에 값을 주면 24Col을 지정 값 만큼 나누어서 렌더링 해준다.

```jsx
import React, { Component } from 'react';
import { Row, Col } from 'antd';

const colStyle = () => ({
  height: 50,
  backgroundColor: 'red',
  opacity: Math.round(Math.random() * 100) / 100,
});

export default class App2 extends Component {
  render() {
    return (
      <div>
        <Row>
          <Col span={12} style={colStyle()}>
            하이
          </Col>
          <Col span={12} style={colStyle()}>
            하이
          </Col>
        </Row>
        <Row>
          <Col span={8} style={colStyle()}>
            하이
          </Col>
          <Col span={8} style={colStyle()}>
            하이
          </Col>
          <Col span={8} style={colStyle()}>
            하이
          </Col>
        </Row>
        <Row>
          <Col span={6} style={colStyle()}>
            하이
          </Col>
          <Col span={6} style={colStyle()}>
            하이
          </Col>
          <Col span={6} style={colStyle()}>
            하이
          </Col>
          <Col span={6} style={colStyle()}>
            하이
          </Col>
        </Row>
      </div>
    );
  }
}
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/antd.PNG?raw=true" width="80%"></p>



##### 3.3.2 Row gutter

Row 컴포넌트의 props로 gutter 속성을 줄 수 있다. gutter는 양쪽 사이에 공간을 의미하는데 내부적으로는 padding이 동작하고 있음을 알 수 있다.

```jsx
// 아래와 같이 gutter를 지정해야 딱 맞는 화면을 확인할 수 있다.
<Row gutter = {16 + 8n의 정수} />
```



##### 3.3.3 Col offset

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/offset.PNG?raw=true" width="80%"></p>

위 그림과 같이 화살표로 표시된 부분을 띄고 시작하고 싶다면 offset이라는 값을 줄 수 있다.

```jsx
<Row gutter={16}>
    <Col span={12} offset={12}>
        <div style={{ height: 50, backgroundColor: 'red', opacity: 0.7 }} />
    </Col>
</Row>
```



##### 3.3.4 정렬

가운데 정렬을 하려면 flex의 프로퍼티와 비슷한 값들을 props에 지정해준다.

```jsx
// 구 버전에서는 type을 지정해줘야한다
<Row type="flex" justify="좌우정렬" align="위아래정렬" />
```

```jsx
<Row
    style={{
        height: '100vh',
    }}
    justify='center'
    align='middle'>
    <Col
        span={4}
        style={{ height: 50, backgroundColor: 'red', opacity: 0.7 }}
        />
</Row>
```

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/justify.PNG?raw=true" width="50%"></p>

