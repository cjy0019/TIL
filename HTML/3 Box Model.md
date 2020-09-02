# Box Model



## DOM(Document Object Model)

- 텍스트 파일로 만들어져 있는 웹 문서를 브라우저에 렌더링하면 웹 문서를 브라우저가 이해할 수 있는 구조로 메모리에 올려야 하는데 이를 **DOM**이라 한다.
- 즉, 모든 요소와 요소의 어트리뷰트, 텍스트를 각각의 객체로 만들고 이들 객체를 부자 관계를 표현할 수 있는 트리 구조로 구성한 것이 **DOM**이다.
- DOM은 자바스크립트를 통해 동적으로 변경할 수 있다.



### DOM tree

DOM tree는 브라우저가 HTML 문서를 로드한 후 파싱하여 생성하는 모델을 의미한다. 객체의 트리로 구조화되어 있기 때문에 **DOM tree**라 부른다.



#### 문서 노드(Document Node)

- 트리의 최상위에 존재하며 각각 요소, 어트리뷰트, 텍스트 노드에 접근하려면 문서 노드를 통해야 한다. 
- DOM tree에 접근하기 위한 시작점이다.

#### 요소 노드(Element Node)

- 요소 노드는 문서의 구조를 서술한다.
- 어트리뷰트, 텍스트 노드에 접근하려면 먼저 요소 노드를 찾아 접근해야 한다.
- 모든 요소 노드는 요소별 특성을 표현하기 위해 HTMLElement 객체를 상속한 객체로 구성된다.

#### 어트리뷰트 노드(Attribute Node)

- 어트리뷰트 노드는 HTML 요소의 어트리뷰트를 표현한다.

#### 텍스트 노드(Text Node)

- 텍스트 노드는 HTML 요소의 텍스트를 표현한다.
- 텍스트 노드는 요소 노드의 자식이며 자신의 자식 노드를 가질 수 없다.



## Box Model

모든 HTML 요소는 Box 형태의 영역을 가지고 있다.

이 Box는 **콘텐트(Content), 패딩(Padding), 테두리(Border), 마진(Margin)**로 구성된다.

![박스모델 이미지 by MDN](https://media.prod.mdn.mozit.cloud/attachments/2014/09/29/8685/0930aa361239ef7b22a8da798410a855/boxmodel-(3).png)

- 브라우저는 박스 모델의 크기(dimension)와 프로퍼티(색,배경, 모양), 위치를 근거로 하여 렌더링을 실행한다.



### Box Model 구성 요소

**콘텐츠 영역(content area)** 

- 콘텐츠 경계가 감싼 영역으로, 글이나 이미지, 비디오 등 요소의 실제 내용을 포함하는 영역으로 width, height 프로퍼티를 갖는다.

**패딩 영역(padding area)**

- padding edge가 감싼 영역으로, <u>콘텐츠 영역을 요소의 안쪽 여백까지 포함하는 크기로 확장 가능</u>
- padding 프로퍼티 값은 패딩 영역의 두께를 의미하며 기본색은 투명(transparent)이다.
- 요소에 적용된 배경의 컬러, 이미지는 패딩 영역까지 적용된다.

**테두리 영역(border)**

- 테두리 경계가 감싼 영역으로, 안쪽 여백 영역을 요소의 테두리까지 포함하는 크기로 확장. 
- 영역의 크기는 테두리 박스 너비와 테두리 박스 높이의 box-width라면 box-sizing:border-box라면 테두리 영역의 크기를 width,min-width, max-width, height, min-heihgt, max-height 속성을 명시적으로 설정할 수 있음 

**마진 영역(margin)**

- 테두리 바깥에 위치하는 요소의 외부 여백 영역이다.
- margin 프로퍼티 값은 마진 영역의 두께를 의미한다.
- 기본적으로 투명(transparent)하며 배경색을 지정할 수 없다.

```html
<html>
<head>
  <style>
    div {
      /* 배경색의 지정: 콘텐츠 영역과 패딩 영역에 적용된다. */
      background-color: lightgrey;
      /* 콘텐츠 영역의 너비 */
      width: 300px;
      /* 패딩 영역의 두께 */
      padding: 25px;
      /* 테두리: 두께 형태 색상 */
      border: 25px solid navy;
      /* 마진 영역의 두께 */
      margin: 25px;
    }
  </style>
</head>
<body>
  <h2>Box Model</h2>

  <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
</body>
</html>
```

<img src="https://github.com/cjy0019/TIL/blob/master/images/boxmodel.PNG?raw=true" style="zoom:50%;" />



## width/height 프로퍼티

- width와 height 프로퍼티는 요소의 너비와 높이를 지정하기 위해 사용된다. 
- 이 때 지정되는 요소의 너비와 높이는 **콘텐츠 영역**을 대상으로 한다.

<span style=color:navy>이는 `box-sizing 프로퍼티`에 기본값인 **content-box**가 적용되었기 때문이다. box-sizing에 **border-box**를 지정하면 콘텐츠 영역, padding, border가 포함된 영역을 width/height 프로퍼티의 대상으로 지정할 수 있다.</span>

