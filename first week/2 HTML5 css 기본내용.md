<h1>Day2 &#9989;</h1>

<h2>INTERNET 서비스들</h2>

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



<h2>
    웹 접근성
</h2>

<blockquote>The power of the Web is in its universality. access by everyone regardless of disability is an essential aspect.<br>
<br>"웹의 힘은 보편성에 있습니다. 장애와 관계없이 모든 사람들이 접속하는게 필수되어야 합니다."
<br> - Tim Berners Lee -
</blockquote>



<h2>HTML의 탄생</h2>

- HTML5 탄생 전, HTML 최초의 버전은 1993년 최신 버전은 1999년에 발표.

- 2004년 애플, 모질라, 오페라 소트웨어(vendor[^1])가 공동으로 설립한 WHATWG[^2]가 W3C와 별개로 Web Application 1.0 과 Web Forms 2.0을 만듦

  [^1]:.제조사
  [^2]: Web Hypertext Application Technology Working Group

- 2007년 W3C가 공개적으로 XHTML2.0의 실패를 인정하고 새롭게 HTML을 개발하기로 결정하고 WHATWG 표준안을 대부분 수용하여 HTML5가 탄생.



<h2>HTML5에 추가된 내용</h2>

- 콘텐츠 모델 : 명확한 정보 구조 설계를 위해 카테고리를 정의하여 각 요소별로 비슷한 성격을 가지고 있는 것끼리 그룹화한 것
  해당 요소가 어떤 콘텐츠를 담고 있는 지에 대한 포괄적인 개념
  각 HTML 요소는 콘텐츠 모델에 맞는 콘텐츠를 가지고 있어야한다
- 섹셔닝 루트 : 섹셔닝 루트에 속하는 요소는 <code>&lt;section&gt;</code> 이나 <code>&lt;section&gt;</code> 요소와 같이 장이나 절과 같은 계층 구조로 구분되지 않고 독립적인 콘텐츠로 분리되기 때문에 아웃라인에 영향을 주지 않음
- 메타데이터 콘텐츠 : 메타데이터는 문서의 정보를 포함하는 메타데이터, 스타일 표현을 위한  요소, <code>&lt;style&gt;</code>행동을 설정하는 <code>&lt;script&gt;</code> 요소들을 나타냄.
- 플로우 콘텐츠 :  메타데이터 콘텐츠 요소 중 일부를 제외하고 문서 본문에 해당하는 body 요소에 들어가는 대부분의 요소들이 플로우 콘텐츠 모델에 속하며, 이 중에서 <code>&lt;area&gt;&lt;meta&gt;&lt;link&gt;&lt;style&gt;</code> 요소는 조건부로 플로우 콘텐츠가 됨.
- 섹셔닝 콘텐츠 : 섹셔닝 콘텐츠는 대부분 HTML5에서 새롭게 추가된 요소들이며, 제목과 그 내용을 포함한 범위를 지정하는 콘텐츠를 나타냄. 모든 섹셔닝 콘텐츠는 헤딩과 아웃라인을 가짐.
- 헤딩 콘텐츠 : 헤딩 콘텐츠는 섹션의 제목을 나타냄. 문서의 아웃라인을 고려하여 사용해야 함.
- 프레이징 콘텐츠 : 프레이징 콘텐츠는 문서의 텍스트를 나타내며, 그 텍스트를 문단 내부 레벨로 마크업하는 요소들임. 프레이징 콘텐츠가 모여 문단을 구성함.
- 임베디드 콘텐츠 : 임베디드는 '포함된' 이라는 뜻을 가지고 있고 문서 안에 외부 리소스 또는 HTML이 아닌 다른 언어로 표현되는 콘텐츠를 말함.
- 인터랙티브 콘텐츠 : 인터랙티브 콘텐츠는 사용자가 어떤 기능을 조작할 수 있는 콘텐츠를 말함. 
- 팰퍼블 콘텐츠 : 기존 콘텐츠 모델에 새롭게 추가된 개념으로 구체적으로 보여지고 이해할 수 있는 콘텐츠 요소를 말하며, 최소한 하나 이상의 요소가 존재해야 하고 이때 해당 요소는 숨김 상태여서는 안 됨.
- 스크립트 지원 요소 : 스크립트 지원 요소는 요소 자체가 어떤 정보를 표현하지는 않지만 사용자에 대한 기능 등에 해당하는 스크립트를 지원하는 데 사용됨.
- 아웃라인 알고리즘 : 웹 페이지의 정보 구조를 판별할 수 있는 개념으로 목차와 비슷함.
구성 요소 : 헤딩, 섹셔닝 콘텐츠, 섹셔닝 루트 요소
- <strong>HTML5의 API</strong> : 자바스크립트 기술을 좀 더 편리하게 이용할 수 있도록 다양한 API를 지원하고 있으며 HTML5에 추가된 API는 오프라인 웹 구현을 위한 API, 실시간 커뮤니케이션 API, 파일/하드웨어 접근 API, GUI를 위한 API 등이 있다.



<h2>CSS3</h2>

- CSS Level 3는 CSS Level 2.1과 달리 모듈 단위로 개발되고 있으며, 표준화가 모듈 단위로 진행되고 있음. 이 중 몇몇 모듈은 현재 Recomendation(권고안) 단계에 있으며, Working Draft(초안) 단계에 머물러 있는 모듈도 있음. <del>따라서 엄밀히 CSS3는 틀린말이고 상용화를 위해 쓰이는 용어임.</del>



<h2>클래스 작명법</h2>

<ul>
    <li>pascal case - ex) MainContent</li>
    <li>camel case - ex) mainContent</li>
    <strong><li>kebab case - ex) main-content</li></strong>
    <li>snake case - ex) main_content</li>
</ul>


<h2>CSS 네이밍 방법론</h2>

<ol>
    <li>SMACSS(Scalable and Modular Architecture for CSS)</li>
    <li>OOCSS(Object Oriented CSS)</li>
    <li>BEM(Block, Element, Module)</li>
    <ul>
        <li>개발, 디버깅, 유지보수를 위해 가능한 명확하게 네이밍하는 것을 목표로 한다</li>
        <li>소문자와 숫자만을 조합한다</li>
        <li>조합은 하이픈(-)으로 연결</li>
        <li>모든 것이 클래스이고 중첩된 것은 없다</li>
        <b>블럭</b>
        <li>형태(small, red)가 아닌 목적(menu, button)에 맞게 결정한다(header,search-form)</li>
        <li>환경에 영향을 받으면 안됨(여백,위치설정 없음)</li>
        요소(element)
        <li>block__element형태로 사용</li>
        수식어(modifier)
        <li>블록이나 요소의 모양(color,size), 상태(disabled,checked)를 정의</li>
    </ul> 
</ol>



<h2>&lt;link&gt;</h2>

- 해당 문서와 외부 소스(external resource) 사이의 관계를 정의할 때 사용한다.
- 요소는 빈 태그이고 속성만을 포함한다.
- 주로 외부 스타일 시트를 연결할 때 사용된다.
  - CSS 적용 방식
  - <strong>   1. external</strong>
    2. embedded(internal)
    3. inline



<h2> src vs href</h2>

- <p> href : 웹 리소스의 위치를 지정하여 현재 요소 또는 현재 문서와 정의 된 대상의 관계를 정의함.
      <br>브라우저는 이 자원이 스타일 시트이고 페이지의 파싱이 일시 중지되지 않음을 말함. 
  </p>

- <p> src: 요소 정의 위치의 현재 문서에 리소스를 포함시킴. <br>브라우저가 발견하면 브라우저가 파일을 페치, 컴파일 및 실행할 때까지 페이지로드 및 처리가 일시정지됨. 
  </p>

  

<h2>em vs rem

</h2>

- em / rem : 모두 길이가 유연한 가변 단위로, 디자인에 설정된 폰트 크기에 따라 브라우저에 의해 픽셀값으로 변환됨
- 어디에 있는 font-size 속성 값인지에 따라 차이가 발생
  - em : 해당 단위가 사용되고 있는 요소의 font-size 속성 값이 기준이 됨
  - rem : 'r'은 root, 즉 최상위 요소를 font-size 속성 값을 의미하고 HTML의 최상위 요소<code>html</code>을 의미

<strong>px 대신 em을 쓰는 이유?</strong>

- px단위를 사용하면 폰트 크기가 고정되기 때문에 창 크기가 작은 모바일 기기로 볼때도 같은 크기로 화면에 표시됩니다. 결국 작은 화면안에 작은 글씨로 표시된다. 따라서 모바일 기기에서 접속을 고려할 경우 em을 쓰는게 좋다.



<h2>Stylesheet 소스</h2>

<p> 1. user agent stylesheet : 웹 브라우저마다 기본적으로 정해놓은 스타일
    <br>2. user defined stylesheet : 사용자 입장에서 제작자의 css를 수정한 스타일
    <br>3. author defined stylesheet : 제작자가 external 이든 internal 이든 웹 사이트의 기본을 구성하는 css


<h2>웹 폰트</h2>

기존에는 운영체제마다 폰트가 달랐기 때문에 같은 웹 페이지가 다르게 렌더링 되는 현상이 발생했다. 이를 해결하고자 텍스트를 표시하는 대신 이미지로 대체하였었다. 그러나 이 과정에서 노이즈가 발생했고 이를 해결할 수단으로 웹폰트가 등장했다.

-> 웹폰트는 CDN(외부서버에 있는 컨텐츠를 가져와 사용하는 것)으로 외부서버에 문제가 생기면 해당 페이지에도 문제가 생길 수 있다.




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




<h2> VSCODE 에서 빈태그(empty tag) 자동닫기</h2>

![emptytag](https://user-images.githubusercontent.com/33951916/87429083-40668300-c61e-11ea-837c-80504ff13b6c.PNG)

1. 설정에서 Emmet : Syntax Profiles 검색!
2.  settings.json에서 편집 선택!

![emptytag_auto](https://user-images.githubusercontent.com/33951916/87429087-4197b000-c61e-11ea-9690-8dcb0442e0f8.PNG)

3. <code>"emmet.syntaxProfiles":{ "html": "xhtml"}</code> 추가!!

