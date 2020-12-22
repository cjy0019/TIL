# React Shadow

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

