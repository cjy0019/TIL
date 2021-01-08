# JavaScript ?

## 1. JavaScript의 탄생

- 1995년, 웹 브라우저 시장을 지배하던 넷스케이프 커뮤니케이션즈는 브라우저에서 동작하는 경량 프로그래밍 언어를 도입함.
- 그 결과, 브렌던 아이크는 자바스크립트를 개발하게 된다.
- 1996년 3월, 모카(Mocha) 로 불리었고 9월엔 라이브스크립트(LiveScript)로 바뀌었다가 12월에 최종적으로 JavaScript라고 불리우게 된다.



## 2. Ajax

- 1999년, 자바스크립트를 이용해 서버와 브라우저가 **비동기(asynchronous)** 방식으로 데이터를 교환할 수 있는 **Ajax(Asynchronous Javascript And XML)가 XMLHttpRequest**라는 이름으로 등장함
- 이전의 웹페이지는 html 태그로 시작해서 html 태그로 끝나는 온전한 HTML 코드를 전송 받아 웹 페이지 전체를 렌더링 하는 방식으로 동작함. 화면이 전환되면 새로운 HTML을 받아 처음부터 다시 렌더링했기 때문에 비효율적이었다.
- 그러나! Ajax의 등장은 혁신이었다. 변경할 필요가 없는 부분은 다시 렌더링하지 않고, 서버로부터 필요한 데이터만 전송 받아 **변경해야 하는 부분만 렌더링 할 수 있게 됨**.
- 이로써 웹 브라우저에서도 데스크톱 애플리케이션과 유사한 성능과 부드러운 화면 전환이 가능해짐



## 3. 웹 페이지 vs 웹 애플리케이션

- 조금 애매하지만 정리해보자!
- **웹 사이트**는 해당 웹의 컨텐츠로 정의된다고 할 수 있다. 즉, 웹 사이트 안에 있는 컨텐츠들이 본질이다.
  즉, 사용자가 할 수 있는 것은 페이지를 돌면서 정보 및 컨텐츠를 일방적으로 얻어 가는 것이 유일하다.
  예로는 뉴스 사이트, W3C 사이트 등을 들 수 있다. **정보제공의 성격이 강함!!**
- **웹 애플리케이션**은 사용자와 상호작용한다. 웹 애플리케이션은 사용자와 상호작용해서 사용자의 입력을 활용하여 글을 작성하거나 사진을 올리고 입력을 처리하여 보여준다. 즉 **자바스크립트**가 필수적이다. 구글의 gmail이나 VScode, Slack이 대표적이다. JavaScript와 Electron으로 만들어짐!
  ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile28.uf.tistory.com%2Fimage%2F9925234E5C5FE8FE19CF80)



## 4. JavaScript 엔진

### 종류

- **V8** : 오픈소스로 구글에서 개발함. C++로 작성되었고 크롬, Node.js에서 사용된다
- **SpiderMonkey** : 최초의 자바스크립트 엔진으로 브렌던 아이크에 의해 개발됨. firefox에서 사용되고 있다.
- **Rhino** : 모질라 재단에서 운영하며 전체가 자바로 개발됨
- **JavaScriptCore** : 니트로라는 이름으로도 알려져 있고 애플이 사파리를 위해 개발함.



## 5. JavaScript 실행 환경

모든 브라우저는 자바스크립트를 해석하고 실행할 수 있는 **자바스크립트 엔진**을 내장하고 있다.
브라우저 뿐만 아니라 **Node.js**도 자바스크립트 엔진을 내장하고 있다.



## 6. Node.js VS 브라우저 환경

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



## 7. JavaScript의 특징

- 자바스크립트는 HTML,CSS와 함께 웹을 구성하는 요소 중 하나로 **웹 브라우저에서 동작하는 유일한 프로그래밍 언어이다.**
- 자바스크립트는 개발자가 별도의 컴파일 작업을 수행하지 않는 **인터프리터 언어**이다.
- 자바스크립트는 명령형(imperative), 함수형(functional), 프로토타입 기반(prototype-based) 객체지향 프로그래밍을 지원하는 멀티 패러다임 프로그래밍 언어이다.



[출처 poiemaweb](https://poiemaweb.com/fastcampus/javascript)