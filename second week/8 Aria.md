# Day8

## ARIA

Accessible Rich Internet Applications, ARIA은 장애를 가진 사용자가 웹 콘텐츠와 웹 어플리케이션에 더 쉽게 접근할 수 있는 방법을 정의하는 여러 특성을 말합니다.



## aria-label

- 요소의 목적을 시각적으로 표시할 때 많이 사용된다
- 텍스트 레이블이 화면에 표시되지 않을 때 사용한다 텍스트와 함께 사용되면 aria-label 값만 사용됨

<img src="https://developers.google.com/web/fundamentals/accessibility/semantics-aria/imgs/aria-label.jpg?hl=ko" style="zoom: 80%;" />

- <code>aria-labelledby</code>를 사용하면 어떤 요소의 레이블로서 DOM에 있는 다른 요소의 ID를 지정할 수 있다.

<img src="https://developers.google.com/web/fundamentals/accessibility/semantics-aria/imgs/aria-labelledby.jpg?hl=ko" style="zoom: 80%;" />

- <code>aria-labelledby</code>는 레이블 지정 가능한 요소 뿐 아니라 어떤 요소에서든 사용할 수 있다.
- <code>aria-labelledby</code>의 경우엔 레이블을 지정하는 대상이 레이블을 지정하는 주체를 참조



<h2>role</h2>

ARIA는 특정 요소가 담당하는 역할을 기준으로 role 속성에 지정할 수 있는 몇 가지 속성 값을 정의하는데 이를 <strong>ontology</strong>를 부여한다고 표현합니다.

- 예를 들어 &lt;nav role="navigation"&gt;과 같이 사용하여 스크린리더가 이 영역을 쉽게 이동하도록 만들 수 있다.
- 종류

-> banner: 특정 문서가 아닌 전체 사이트 영역을 지정 <u>헤더나 로고</u>

-> application: 웹 애플리케이션에 사용되는 영역을 지정

-> complementary: 페이지의 메인 섹션을 보완하는 영역을 지정

-> contentinfo: 메인 콘텐츠의 정보를 지정 <u>페이지 하단의 저작권 정보 표시</u>

-> form: 웹 폼을 지정, 검색 엔진일 경우에는 대신 search를 사용



<h2>TAB-INDEX</h2>

사용자가 키보드로 페이지를 내비게이션 할 때 어떤 순서로 이동할 지를 지정할 수 있는 방법이다.

- 이미지 맵 영역들인데 다른 요소에도 포커스가 될 수 있게 tabindex 속성을 주고 자바스크립트로 focus() 명령을 실행해 해당 영역으로 포커스가 이동하게 할 수 있다.
- 이 기법을 사용하면 tabindex를 적용한 요소들도 키보드로 내비게이션할 때 노출이 되므로 tabindex=-1으로 프로그램적으로만 포커스를 줄 수 있다.
- tabindex="1" 문서 안에서 가장 먼저 포커싱된다. 자연스러운 마크업을 거스르는 것이기 때문에 주의해야한다.
- tabindex="0" div, span 과 같은 요소들도 초점을 받을 수 있도록 만들어준다.
- tabindex="-1" 키보드 포커싱을 받을 수 있는 요소도 포커싱 **받을 수 없도록** 만들어준다.



## Time tag

- 용도 : <strong>일반 텍스트로 보이는 날짜와 시간 정보를 HTML에게 알려주기 위해 사용</strong>
- 특히 Time 태그 에서 <span style="color:red">datetime 속성</span>은 time 요소의 날짜와 시간 데이터를 기계가 읽을 수 있는 형태로 알려준다
- 즉 우리가 표시하는 시간을 <span style="color:blue">기계가 읽을 수 있는 날짜로 표시하기 위해 datetime을 사용한다</span>
- 사용법

&lt;time datetime="YYYY-MM-DDThh:mm:ssTZD|PTDHMS&gt;"

Time Zone Designator는 표준 시간 지정자를 의미하고 Z는 그리니치 표준시를 의미한다.

&lt;time datetime="2020-07-23T:07:15:15+09:00"&gt;이라고 했다면 UTC+09:00은 서울 타임존에 있는 2020년 07월 23일 07시 15분 15초를 가르킨다.
