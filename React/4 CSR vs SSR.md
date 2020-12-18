# CSR vs SSR

## SSR

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/ssr_img.png?raw=true" width="65%"></p>

SSR은 Server Side Rendering의 약자이다. 전통적인 웹 애플리케이션은 SSR 방식을 채택해왔다.

렌더링 과정을 간단하게 설명하자면 유저가 클라이언트에서 유저가 도메인을 입력하면 DNS를 통해 IP주소를 가져오고 해당주소의 서버에 request를 보내고 연결된 서버에서 response를 받게된다. 유저는 브라우저가 렌더링된 화면을 보게된다. 이 때 response로 받은 파일은 기본적으로 HTML의 형태이다. 즉, 서버에서 렌더링이 완료된 것을 불러와 브라우저에서 뿌려주기만 하기 때문에 서버사이드 렌더링이라고 불린다. 

SSR은 데이터를 요청할 때마다 서버에서 처리 한 후 새로운 페이지에 대한 요청을 하는 방식으로 동작해왔다. 웹상에서 데이터와 기능이 복잡해지면서 SPA 개념이 생겨나게 되었다.



### SSR의 장점

- SSR은 View를 서버에서 렌더링해서 가져오므로 초기 로딩이 매우 짧다.
- SEO(Search Engine Optimization) 검색엔진 최적화에 유리하다. CSR처럼 미리 그려지지 않은 빈 HTML화면을 제공한다면 웹 검색엔진 크롤러 로봇이 내용을 해석하는데 어려움이 있다. 하지만 SSR은 서버에서 페이지를 제공할 때 컨텐츠가 미리 담겨오기 때문에 SEO관점에서 좋다.



### SSR의 단점

- 프로젝트의 구조가 복잡해진다.
- 개발 프로세스가 복잡하다.
- View를 변경할 때 마다 서버에 계속적으로 요청을 해야하므로 서버에 대한 부담이 크다. 정보가 많은 B2C 웹 서비스 등에는 서버 부담이 크다.



## CSR

<p align="center"><img src="https://github.com/cjy0019/TIL/blob/master/images/csr_img.png?raw=true" width="65%"></p>

CSR은 Client Side Rendering의 약자이다.

클라이언트 사이드 렌더링은 첫 로딩 때 서버에 요청을 보낸다. 서버에서는 응답으로 HTML을 넘겨주는데 이 때 빈 HTML화면을 넘겨준다. 필요한 서비스들은 스크립트에 의해 렌더링이 이루어진다. 즉, 첫 요청 시에 한페이지만 불러오고 페이지 이동시에 기존 페이지의 내부를 수정해서 보여주는 방식이다. 브라우저가 자바스크립트를 받아와 동적으로 렌더링합니다.

클라이언트 관점에서 첫 페이지를 로딩한 후 부터는 새로고침 없이 변화된 부분만 서버로부터 받아서 화면을 갱신한다.



### CSR의 장점

- 자연스러운 사용자 경험을 제공한다.
- 필요한 리소스만 부분적으로 로딩하므로 첫 로딩 이후에는 인터렉션이 즉각적이다.
- 서버의 템플릿 연산을 클라이언트로 분산시켰다.
- 컴포넌트별 개발에 용이하다.



### CSR의 단점

- Javascript 파일을 번들링 해서 한 번에 받기 떄문에 초기 구동 속도가 느리다.
- SEO관점에서 좋지 않다.



## 결론

### CSR

- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행되기 전까지는 화면이 보이지 않는다.
- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 화면이 보이면서 유저가 인터렉션이 가능해짐

### SSR

- JS가 전부 다운로드 되지 않아도 일단 화면은 보이지만 유저가 사용할 수 없다.
- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후 유저가 사용 가능하다.