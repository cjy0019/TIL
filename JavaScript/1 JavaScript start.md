# JavaScript 환경

## 1. JS 실행 환경

모든 브라우저는 자바스크립트를 해석하고 실행할 수 있는 자바스크립트 엔진을 내장하고 있다.
브라우저 뿐만 아니라 **Node.js**도 자바스크립트 엔진을 내장하고 있다.
<span style=color:pink>즉, 브라우저에서 동작하는 코드는 Node.js 환경에서도 동일하게 동작한다.</span>

## 2. Node.js VS 브라우저 환경

### 사용 목적

&#128641;브라우저는 <span style= color:pink>HTML, CSS, JS를 실행해 웹페이지를 브라우저 화면에 렌더링하는 것이 목적</span>

🚂 Node.js는 <span style= color:pink>외부에서 JS 개발 환경을 제공하는 것이 주된 목적이다.</span>

❝ 따라서 브라우저와 Node.js 모두 자바스크립트의 코어인 ECMAScript를 실행할 수 있지만 브라우저와 Node.js에서 추가로 제공하는 기능은 호환되지 않는다 ❞

&#128641; 브라우저는 <span style= color:pink>HTML 요소를 선택하거나 조작하는 기능으 집합인 DOM API를 기본적으로 제공함</span>

🚂 브라우저 외부에서 개발 환경을 제공하는 것이 주목적인 Node.js는 <span style= color:pink>HTML 요소를 파싱해서 객체화한 DOM을 직접 다룰필요가 없기 때문에 제공하지 않는다.</span>

🚂 Node.js에서는 파일을 CRUD할 수 있는 파일 시스템을 기본을 제공하지만 브라우저는 제공하지 않는다.

&#128681; 결론 

- 브라우저는 ECMAScript와 DOM, BOM, Canvas, XMLHttpRequest, Fetch, requestAnimationFrame, SVG, Web Storage, Web Component, Web worker와 같은 <span style= color:pink>클라이언트 사이드 Web API를 지원</span>
- Node.js는 클라이언트 사이드 Web API를 지원하지 않고 ECMAScript와 <span style= color:pink>Host API</span>를 지원한다.