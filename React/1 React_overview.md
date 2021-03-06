

# React

<p align='left'><img src="https://github.com/cjy0019/TIL/blob/master/images/react-logo.png?raw=true" width="20%"></p>

## 개요

### 1. React의 역사

<p align="left"><img src="https://github.com/cjy0019/TIL/blob/master/images/facebook-logo.png?raw=true" width="20%"></p>

초기 리액트의 프로토타입 모델은 "FaxJS"라고 불리웠다. "FaxJS"는 페이스북의 소프트웨어 개발자 Jordan Walke에 의해 개발되었는데 Jordan이 리액트 또한 개발하였다. 리액트는 PHP를 위한 HTML 컴포넌트 라이브러리인 XHP에 영향을 받아 개발되었다. 2011년, 페이스북의 News Feed에 처음으로 구축되었고, 이어 2012년에 인스타그램에 도입되었다. 그리고 2013년 5월에 미국 JSConf에서 오픈소싱되었다.

네이티브 안드로이드, IOS, UWP 개발을 리액트로 가능하게한 리액트 네이티브는 2015년 2월, 페이스북의 React Conf에서 처음으로 발표되었다. 

2017년 4월 18일에 페이스북은 유저 인터페이스 구축을 위한 리액트 라이브러리의 새로운 핵심 알고리즘인 React Fiber를 발표했다. React Fiber는 리액트 라이브러리의 향후 기능 개선 및 기능 개발의 기초가 되었다. 

2019년 2월 React 16.8 버전이 공개되었고, React Hooks를 발표했다.



### 2. 왜 React를 생각했을까?

페이스북이 리액트를 만들기 전에도 Angular, Backbone, Knockout.js 등의 많은 프레임워크들이 존재했다. 그리고 이런 프레임워크들은 MVC패턴, 그리고 MVC에서 파생된 MVVM(View Model), MVW(Whatever)등의 패턴들로 이뤄져있다. 공통점은 모델인데 모델에 있는 값이 변하면 뷰에서도 이를 변화시켜야 한다. 일단 첫 화면을 보여주고 변화에 따라 필요한 곳을 바꿔준다. 하지만 변화(Mutation)를 시킴에 따라 어떤 DOM을 가져올지 어떻게 뷰를 업데이트 해줄지 정해야 하는데 복잡한 작업의 연속이다. 따라서 페이스북은 **Virtual DOM**이라는 개념을 생각해냈고 리액트로 구현하였다.



### 3. Virtual DOM

리액트의 주요 특징 중 하나는 Virtual DOM을 사용하는 것이다.**Virual DOM**에 앞서서 브라우저의 Workflow를 알아야한다.

<p align="center"><img src="https://poiemaweb.com/assets/fs-images/38-1.png" width = "70%"></p>



### 3.1 브라우저의 렌더링 과정

#### 1. DOM Tree 생성

- 브라우저가 HTML을 전달받으면, 브라우저는 HTML, CSS를 파싱하여 DOM과 CSSOM을 생성한다.

#### 2. Render Tree 생성

- 앞서 생성한 DOM Tree와 CSSOM Tree를 결합하여 새로운 Render Tree를 생성한다.

#### 3. Render Tree 생성 - 뒤에선 무슨 일이 일어나는지..

- Webkit 에서는 노드의 스타일을 처리하는 과정을 'attachment'라고 부른다. DOM 트리의 모든 노드들은 'attach'라는 메서드가 있다. 이 메서드는 스타일 정보를 계산해서 객체형태로 반환한다.
- 이 과정은 동기적(synchronous)작업이고, DOM트리에 새로운 노드가 추가되면 그 노드이ㅡ attach 메서드가 실행된다.

#### 4. 자바스크립트 파싱과 실행

- 렌더링 엔진으로부터 제어권을 넘겨받은 자바스크립트 엔진은 자바스크립트 코드를 파싱하기 시작한다. 렌더링 엔진이 HTML과 CSS를 파싱하여 DOM과 CSSOM을 생성하듯이 자바스크립트 엔진은 자바스크립트를 해석하여 **AST(Abstract Syntax Tree, 추상적 구문 트리)**를 생성한다. 그리고 AST를 기반으로 인터프리터가 실행할 수 있는 중간 코드(intermediate code)인 바이트코드를 생성하여 실행한다.

#### 5. Reflow

- 리플로우는 레이아웃 계산을 다시 하는 것을 말하고, 노드 추가/삭제, 요소의 크기/위치 변경, 윈도우 리사이징 등 레이아웃에 영향을 주는 변경이 발생한 경우에 한하여 실행된다.

#### 6. Repaint

- 리페인트는 재결합된 렌더 트리를 기반으로 다시 페인트를 하는 것을 말한다.



### 3.2 Virtual DOM 탄생이유

<iframe width="560" height="315" src="https://www.youtube.com/embed/BYbgopx44vo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

DOM API는 문제점이 있다. 동적 UI에 최적화되어 있지 않다는 것이다. 요즘 큰 규모의 웹 애플리케이션은 스크롤바를 내릴때마다 수많은 데이터가 로딩되는데 많은 요소들도 같이 로딩이 된다. 이 때 성능면에서 이슈가 발생한다. 

DOM 자체는 자바스크립트의 객체를 처리할 때의 성능과 별 차이없다. 하지만 위와 같이 DOM을 조작하면 6가지(간추린)의 일련의 과정이 실행되어 브라우저에 렌더링이 되어진다. 페이스북 같은 복잡한 SPA(Single Page Application)에서는 DOM 조작이 많이 발생한다. 즉, 그 만큼 브라우저는 많은 연산을 수행하게 되고 전체적인 성능에 영향을 미치게 된다. 즉, 이 때, 리플로우와 리페인트가 계속적으로 일어나는데 성능 이슈의 원인이 된다.

이를 해결하기 위해 고안한 것이 **Virtual DOM**이라고 할 수 있다. 뷰에 변화가 생기면 그 변화가 실제 DOM에 적용되기전에 가상의 Virtual DOM에 적용시키고 최종적인 결과를 실제 DOM으로 전달해준다.

**즉, 모든 변화를 묶어서 한번만 실제 DOM에 던져주게 되는 것이다. 결과적으로 리렌더링의 규모는 커지지만 브라우저 내에서 발생하는 연산의 양을 줄였다고 할 수 있다.** DOM을 조작하지 않을 수는 없기 때문에 DOM조작 횟수를 줄이는 방법으로 해결책을 제시한 것이다. 

DOM fragment를 사용해도 비슷한 효과를 줄 수 있지만, DOM fragment를 수동으로 관리해야하고 업데이트에 번거로움이 있기 때문에 비효율적이다.



### 4. React를 써야하는 이유

1. 앞서 설명한 것과 같이 Virtual DOM을 사용함으로써 DOM처리가 빠르다. 연산을 줄여 성능을 개선시켰다. (절대적으로 DOM<React는 아니다)
2. 서버와 클라이언트 사이드 렌더링 지원을 통해 브라우저의 초기 렌더링 딜레이를 줄이고 SEO 호환도 가능해졌다.
3. Component의 가독성이 높고, UI 수정 및 재사용성이 좋다. 
4. 단방향 데이터 흐름을 지향하기 때문에 관리하기 쉬운 애플리케이션을 만들 수 있다.



### 5. React의 단점

리액트는 프레임워크가 아니므로 라이브러리로서의 단점을 내포하고 있다.

1. View-orientedness는 리액트의 큰 단점중 하나이다. 즉 웹 프레임워크들이 MVC 또는 MVW등의 구조를 지향하는 것과 달리 리액트는 View만 담당한다. View 이외의 기능은 **써드파티 라이브러리를 이용하거나 직접 구현해야 한다.**
2. 그러나 리액트 라우터(react-router), axios, fetch, 리덕스(redux)나 MobX를 사용하여 단점을 채울 수 있다.

[참조 링크]( https://velopert.com/3236)

