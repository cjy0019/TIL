# HTML 개요

## INTERNET 서비스들

<ul>
    <li>Telnet</li>
    <li>IRC</li>
    <li>email</li>
    <li>Archie</li>
    <li>Usenet</li>
    <li>Gopher</li>
    <li>FTP</li>
    <li>WWW</li>
</ul>



<h2>W3C</h2>

- W3C는 회원기구, 정직원, 공공기관이 협력하여 웹 표준을 개발하는 국제 컨소시엄
- 웹의 모든 잠재력을 이끌어내기 위해서 가장 기본적인 웹 기술은 상호 간의 호환성이 있어야 함
- 어떤 소프트웨어나 하드웨어에서도 웹에 접근할 수 있어야 한다는 것

  참고:  [W3C 접속](https://www.w3.org/)

  책 추천:

 <img src="https://wikibook.co.kr/images/cover/l/9788992939119.jpg" style="zoom:50%;" />



## 웹 접근성


<blockquote>The power of the Web is in its universality. access by everyone regardless of disability is an essential aspect.<br>
<br>"웹의 힘은 보편성에 있습니다. 장애와 관계없이 모든 사람들이 접속하는게 필수되어야 합니다."
<br> - Tim Berners Lee -
</blockquote>


## HTML의 탄생

- HTML5 탄생 전, HTML 최초의 버전은 1993년 최신 버전은 1999년에 발표.

- 2004년 애플, 모질라, 오페라 소트웨어(vendor[^1])가 공동으로 설립한 WHATWG[^2]가 W3C와 별개로 Web Application 1.0 과 Web Forms 2.0을 만듦

  [^1]:.제조사
  [^2]: Web Hypertext Application Technology Working Group

- 2007년 W3C가 공개적으로 XHTML2.0의 실패를 인정하고 새롭게 HTML을 개발하기로 결정하고 WHATWG 표준안을 대부분 수용하여 HTML5가 탄생.



## <span style=color:pink>HTML4</span> 아웃라인 vs <span style=color:skyblue>HTML5</span> 아웃라인 알고리즘

- 문서의 구조, 즉 `<body></body>`사이에 있는 것의 <span style=color:blue;font-weight:bold;>의미론적 구조</span>는, 페이지의 내용을 사용자에게 전달하는 데 중요한 토대가 된다.
- <span style=color:pink>HTML4</span>에선 헤딩 요소 자체가 아웃라인을 만들었다.
- <span style=color:skyblue>HTML5</span>에서는 반면 많은 Semantic 태그들이 등장하면서 명시적으로 아웃라인을 구성할 수 있게 되었다.



## 명시적 아웃라인 vs 암묵적 아웃라인

- HTML4와 HTML5의 가장 큰 차이라고 할 수 있다.
- 명시적 아웃라인은 `<section>,<article>`등의 요소로 직접 묶어서 아웃라인을 설정하는 것을 말한다.
- 암묵적인 아웃라인은 `heading`요소를 사용하여 그 아래에 있는 요소들이 아웃라인을 구성하도록 하는 것을 말한다.



<h2>HTML5에 추가된 내용</h2>

- 콘텐츠 모델
  
  - 보다 명확하고 Semantic한 구조 설계 및 구성을 위해 개념이 추가 되었다.
  - 어떤 요소에 어떤 콘텐츠를 포함해야 하는지 어떤 요소가 어떤 요소를 포함할 수 있는지 정의한 것이다.
  
  - 명확한 정보 구조 설계를 위해 카테고리를 정의하여 각 요소별로 비슷한 성격을 가지고 있는 것끼리 그룹화한 것
  
  - 각 HTML 요소는 콘텐츠 모델에 맞는 콘텐츠를 가지고 있어야한다
  
  
  
- 섹셔닝 루트 : `<body>,<blockquote>,<figure>,<fieldset>,<td>,<details>`

  - HTML5 전용 아이템이다.
  - 즉 위의 요소들은 하위의 요소로 섹셔닝 요소가 들어간다고 하더라도 섹셔닝루트(body) > 섹셔닝 루트(fieldset)는 하위 아웃라인을 포함시키지 않는 속성을 가짐으로, 하위 섹셔닝은 이루어지지 않는다.
  - **해당요소는 독립된 콘텐츠로 간주되어 전후의 콘텐츠 아웃라인에는 영향을 미치지 않는다**

  

- 섹셔닝 콘텐츠 : `<section>,<article>,<nav>,<aside>` 

  - 위의 요소들은 요소 자체가 의미를 가지며, 하나의 아웃라인을 만든다.

  - 대부분 HTML5에서 추가된 내용이다.
  - 명시적 개요를 생성하는 개요 컨테이너이다.
  - 헤딩을 함께 사용하면 헤딩 수준이 자동으로 바뀐다.

  <span style=color:red>섹셔닝 콘텐츠를 사용하면 브라우저의 개요 알고리즘이 헤딩 수준을 적절하게 보정한다.</span>

  ```html
  <body>
      <h1>제목1</h1>
      <h2>제목2</h2>
      
      <article>
      	<h3>
              제목3-1
          </h3>
      </article>
      
      <article>
      	<h3>
              제목3-2
          </h3>
      </article>
  </body>
  ```

  ```html
  1. 제목1
  	1. 제목2
  	2. 제목3-1
  	3. 제목3-2
  ```

  -> article 태그를 한단계 내리고 싶다면 아래와 같이 바꿔야 함

  ```html
  <body>
      <h1>제목1</h1>
      <h2>제목2</h2>
  	 
      <h3>제목3-1</h3>
      <div></div>
      
      <h3>제목3-2</h3>
      <div></div>
  </body>
  ```

  

- 메타데이터 콘텐츠 : 메타데이터 콘텐츠 카테고리에 속한 요소는 문서의 표현이나 동작을 수정하거나, 다른 문서를 가리키는 링크를 설정하거나, 기타 '대역 외 정보'를 전달한다.

  - `<base>`,<del>`<command>`</del>,`<link>,<meta>,<script>,<style>,<title>`

  

- 플로우 콘텐츠 :  플로우 콘텐츠 카테고리에 속한 요소는 보통 텍스트나 내장 콘텐츠를 포함한다.

  

- 헤딩 콘텐츠 : 헤딩 콘텐츠는 섹션의 제목을 나타냄. 문서의 아웃라인을 고려하여 사용해야 함.

  - `<h1>~<h6>,<hgroup>`

  

- 프레이징 콘텐츠 : 프레이징 콘텐츠는 문서의 텍스트를 나타내며, 그 텍스트를 문단 내부 레벨로 마크업하는 요소들임. 프레이징 콘텐츠가 모여 문단을 구성함.

  

- 임베디드 콘텐츠 : 임베디드 콘텐츠는 다른 리소스를 가져오거나, 콘텐츠를 다른 마크업 언어나 네임스페이스로부터 문서에 삽입한다.

  - `<audio>,<canvas>,<embed>,<iframe>,<img>,<object>,<video>`

  

- 인터랙티브 콘텐츠 : 사용자와의 상호작용을 위해 특별하게 설계된 요소를 포함한다.

  - `<a>,<button>,<details>,<embed>,<iframe>,<label>,<select>,<textarea>`

  

- 팰퍼블 콘텐츠 : 기존 콘텐츠 모델에 새롭게 추가된 개념으로 구체적으로 보여지고 이해할 수 있는 콘텐츠 요소를 말하며, 최소한 하나 이상의 요소가 존재해야 하고 이때 해당 요소는 숨김 상태여서는 안 됨.

  

- 스크립트 지원 요소 : **스크립트 지원 요소**는 문서의 렌더링 결과에 바로 기여하지 않는 요소로, 대신 스크립트 코드를 직접 포함 또는 명시하거나, 스크립트가 사용할 데이터를 지정하는 방식으로 지원하는 요소이다.

  - `<script>,<template>`

  

- <strong>HTML5의 API</strong> : 자바스크립트 기술을 좀 더 편리하게 이용할 수 있도록 다양한 API를 지원하고 있으며 HTML5에 추가된 API는 오프라인 웹 구현을 위한 API, 실시간 커뮤니케이션 API, 파일/하드웨어 접근 API, GUI를 위한 API 등이 있다.




## &lt;link&gt;

- 해당 문서와 외부 소스(external resource) 사이의 관계를 정의할 때 사용한다.
- 요소는 빈 태그이고 속성만을 포함한다.
- 주로 외부 스타일 시트를 연결할 때 사용된다.
  - CSS 적용 방식
  -   **1. external**
    1. embedded(internal)
    2. inline



## src vs href

- `src` 및 `href` 속성은 이미지, CSS, HTML, 기타 웹 페이지 또는 JavaScript 파일과 같은 일부 외부 엔티티를 포함하는데 사용한다.

href  

- 웹 리소스의 위치를 지정하여 현재 요소 또는 현재 문서와 정의 된 대상의 관계를 정의함.
- 리소스를 페이지에 추가하지 않고 리소스에 대한 링크를 제공하기 위해 사용한다.

src

- 요소 정의 위치의 현재 문서에 리소스를 포함시킴.
- 브라우저가 발견하면 브라우저가 파일을 페치, 컴파일 및 실행할 때까지 페이지로드 및 처리가 일시정지됨.




<h2> 용어 정리</h2>

<p>
    1. ~ : Tilde(틸드)<br>
    2. ^ : Caret(캐럿)<br>
    3. @ : At Sign(엣 사인)<br>
    4. * : Asterisk(아스테리스크)<br>
    5. ` : back tick(백 틱)<br>
    <p>
        6. 파편화: 사용자 운영체제(OS)나 브라우저 종류별로 웹 기술의 지원 수준이 천차만별이다 일괄된 경험을 <br>제공해야하는 이슈발생<br>
</p>
    7. woff(Web Open Font Format) : OTF와 TTF의 무단배포 등의 문제 등을 해결하기 위해 모질라와 오페라, MS에서 제안한 웹폰트 파일 형식. 과거에는 TTF(트루타입)의 형태를 많이 사용했지만 용량이 너무 크기 떄문에 woff와 eot가 등장. 
</p>