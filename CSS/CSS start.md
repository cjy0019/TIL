# CSS 개요

## CSS3

- CSS Level 3는 CSS Level 2.1과 달리 모듈 단위로 개발되고 있으며, 표준화가 모듈 단위로 진행되고 있음. 이 중 몇몇 모듈은 현재 Recomendation(권고안) 단계에 있으며, Working Draft(초안) 단계에 머물러 있는 모듈도 있음. <del>따라서 엄밀히 CSS3는 틀린말이고 상용화를 위해 쓰이는 용어임.</del>



## 클래스 작명법

<ul>
    <li>pascal case - ex) MainContent</li>
    <li>camel case - ex) mainContent</li>
    <strong><li>kebab case - ex) main-content</li></strong>
    <li>snake case - ex) main_content</li>
</ul>



## CSS 네이밍 방법론

- SMACSS(Scalable and Modular Architecture for CSS)

- OOCSS(Object Oriented CSS)

- BEM(Block, Element, Module)

  - 개발, 디버깅, 유지보수를 위해 가능한 명확하게 네이밍하는 것을 목표로 한다

  - 소문자와 숫자만을 조합한다

  - 조합은 하이픈(-)으로 연결

  - 모든 것이 클래스이고 중첩된 것은 없다

    

    **블럭(block)**

  - 형태(small, red)가 아닌 목적(menu, button)에 맞게 결정한다(header,search-form)

  - 환경에 영향을 받으면 안됨(여백,위치설정 없음)

    

    **요소(element)**

  - block__element형태로 사용

    

    **수식어(modifier)**

  - 블록이나 요소의 모양(color,size), 상태(disabled,checked)를 정의



## em vs rem

- em / rem : 모두 길이가 유연한 가변 단위로, 디자인에 설정된 폰트 크기에 따라 브라우저에 의해 픽셀값으로 변환됨
- 어디에 있는 font-size 속성 값인지에 따라 차이가 발생
  - em : 해당 단위가 사용되고 있는 요소의 font-size 속성 값이 기준이 됨
  - rem : 'r'은 root, 즉 *최상위 요소*를 font-size 속성 값을 의미하고 HTML의 최상위 요소<code>html</code>을 의미



### px 대신 em을 쓰는 이유?

- px단위를 사용하면 폰트 크기가 고정되기 때문에 창 크기가 작은 모바일 기기로 볼때도 같은 크기로 화면에 표시됩니다. 결국 작은 화면안에 작은 글씨로 표시된다. 따라서 모바일 기기에서 접속을 고려할 경우 em을 쓰는게 좋다.



## stylesheet 소스

1. user agent stylesheet : 웹 브라우저마다 기본적으로 정해놓은 스타일
2. user defined stylesheet : 사용자 입장에서 제작자의 css를 수정한 스타일
3. author defined stylesheet : 제작자가 external 이든 internal 이든 웹 사이트의 기본을 구성하는 css



## 웹 폰트

- 기존에는 운영체제마다 폰트가 달랐기 때문에 같은 웹 페이지가 다르게 렌더링 되는 현상이 발생했다. 이를 해결하고자 텍스트를 표시하는 대신 이미지로 대체하였었다. 그러나 이 과정에서 노이즈가 발생했고 이를 해결할 수단으로 **웹폰트**가 등장했다.

- 웹폰트는 CDN(외부서버에 있는 컨텐츠를 가져와 사용하는 것)으로 외부서버에 문제가 생기면 해당 페이지에도 문제가 생길 수 있다.