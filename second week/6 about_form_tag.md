# Day6✅

##  마크업 할 때 선형화 구조를 잘 이해하자

- ex) 로그인(제목) -> 아이디 -> 아이디 input -> password -> password input -> 로그인 버튼

<h2>Section 태그</h2>

<span style=color:pink>section</span> 태그는 테마별로 연관된 콘텐츠를 한데 묶어서 더 큰 논리적인 단위를 형성할 수 있게 도와주며 하나의 페이지 안에서 주제가 다른 영역을 구분짓거나 하나의 글을 부분으로 나누기도 한다. 주로 heading과 함께 사용한다. 

<strong>Q) 섹션요소는 heading을 꼭 붙여야하는가? </strong>

- 디자인 상 **section heading**이 없다 할지라도 section 제목이 없는 것은 아니다
- 보이지 않게 할 수 있다. 
  ex) a11y-hidden 클래스로 사라지게 할 수 있다 스크린 리더를 통해 정보 접근을 허용하게 한다

## fieldset

&lt;fieldset&gt; 요소는 웹 양식의 여러 컨트롤과 레이블(label)을 묶을 때 사용합니다.

- fieldset은 HTML 양식 속에서 그룹을 만들 수 있고 legend 요소로 그룹의 설명을 제공할 수 있다. 가능한 넣어주는게 좋다 필요하다면 숨김가능
- 여러 특성을 지정할 수 있는데 그 중 중요한 것은 form요소의 id를 받을 수 있는 form특성으로 form 바깥의 fieldset 요소를 양식에 포함할 때 사용해야한다.
- display:block이 기본 값


<h2>
    label
</h2>

- label은 폼의 양식에 이름을 붙이는 태그이다
- 주요 속성은 **for**인데 양식의 **id**의 값이 같으면 연결된다
- label 요소는 브라우저에 의해 일반적인 텍스트로 렌더링 되지만, 사용자가 마우스를 클릭할 경우 label요소와 연결된 요소를 곧바로 선택할 수 있어 사용자 편의성에 큰 도움이 된다.



<h2>이미지 vs 텍스트 이미지</h2>

1. 웹에서 텍스트를 다룰 때 일반적인 시스템 폰트를 사용하면 크기를 키웠을 떄 이쁘지않다
2. 따라서 이미지를 이용해서 텍스트를 다루는 일이 많이 늘어났다
3. 과거에는 일러스트레이터로 텍스트를 입력해 이미지로 올려서 웹사이트에 다뤄도 큰 문제가 없었다.문제로 용량과 선명도를 들 수는 있다.(확대했을 때 선명도 매우 저하됨)
4. 그러나 가장 큰 치명적인 단점은 웹표준에 도움이 되지 않는다. 이미지로만 이루어진 검색엔진이 인식하지 못한다.

## form 

1. form 태그는 웹 페이지에서의 입력 양식을 의미한다.
2. 텍스트 필드에 글자를 입력하거나, 체크박스나 라디오 버튼을 클릭하고 제출 버튼을 누르면 <i>백엔드 서버</i>에 양식이 전달되어 정보를 처리함
3. 일반적인 경우에 fieldset과 같이온다

### form attribute 종류

- ~~name - 폼의 이름, 입력된 데이터를 묶어서 서버로 보내준다(HTML4 부터 사용 중단)~~
- action - 폼 데이터가 전송되는 백엔드 url
- method - 폼 전송 방식(GET/ POST)
- accept-charset : 스페이스로 구분한, 서버가 허용하는 문자 인코딩의 목록 **기본값은 페이지 인코딩과 같다**
- autocomplete: 입력 요소가 자동완성된 값을 기본값으로 가질 수 있는지 나타낸다
  - *off* : 브라우저가 각 항목에 자동으로 값을 채워 넣지 않는다
  - *on* : 사용자의 과거 입력값에 기반하여 브라우저가 자동으로 값을 채워 넣음.
- novalidate: 지정한 경우 양식의 유효성 검증을 건너뛴다

## input

- input 요소는 웹 양식에서 사용자의 데이터를 받을 수 있는 **대화형 컨트롤러**를 생성합니다.
- input 태그의 required 속성은 폼 데이터가 서버로 제출되기 전 반드시 채워져 있어야 하는 입력 필드를 명시한다.
- required 속성은 불린 속성으로 해당 속성을 명시하지 않으면 속성 값이 자동으로 false 값을 가진다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&amp;fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNncO5%2Fbtqwi1g1R8p%2FKKL2b3TlSRLnKSVmXC4Ekk%2Fimg.png" style="zoom:67%;" />

#### [Type] 

*input의 동작 방식은 <code style=color:skyblue>type</code>특성에; 따라 현격히 달라진다. 기본값은 text이다.*

- button : 기본 행동을 갖지 않고 value를 레이블로 사용하는 푸시 버튼
- checkbox : 단일 값을 선택할 수 있는 체크 박스
- color: 색을 지정할 수 있는 컨트롤러
- date : 날짜를 지정할 수 있는 컨트롤
- datetime-local : 날짜와 시간을 지정할 수 있는 컨트롤(시간대는 지정할 수 없음)
- email : 이메일 주소를 편집할 수 있는 필드, 텍스트 입력필드처럼 보이지만 유효성 검증 매개변수가 존재함
- file : 파일을 지정할 수 있는 컨트롤 accept를 사용하면 허용하는 파일 유형을 지정할 수 있다.
- hidden : 보이지 않게 해줌
- image : src 특성에 지정한 이미지로 나타나는 시각적 제출 버튼
- month : 연과 월을 지정할 수 있는 컨트롤
- number : 숫자를 입력하는 컨트롤러 spinner를 보여준다
- password : 한줄 텍스트 필드로 값은 obscured함
- range : 정확한 값을 필요로 하지 않을 때, 기본 값이 중간 값인 범위 위젯으로 표시됨
- <img src="https://www.jqueryscript.net/images/Custom-Range-Input-Plugin-jQuery.jpg" style="zoom:50%;" />
- reset : 폼을 기본 값으로 리셋시키는 버튼 ~~NOT RECOMMENDED~~
- search : 한 줄의 텍스트 필드로 줄 바꿈은 자동으로 제거됨. 필드를 지우는 데 활용 가능한 삭제 아이콘이 포함될 수 있다.
- submit : 제출을 위한 버튼 폼이다.
- tel : 전화번호를 입력받는 컨트롤이다.
- text : 기본 값으로 한줄 텍스트 필드이다 줄바꿈은 자동으로 제거됨
- url : URL을 입력할 수 있는 필드이다. 텍스트 input 같지만 유효성검사 파라미터를 가지고 있고 동적인 키보드를 지원

<span style="color:red">태</span><span style="color:pink" style>그</span>


1. 다음과 같이 글자 별로 다른 색으로 디자인을 적용하고 싶다면 <u>각각 단어에 span을 적용해준다.</u>
2. **text-indent는 블록 상자에만 가능하다**
3. 레이아웃 배치를 할 때 최적의 구조를 생각해보자 normal-flow를 움직이지 않으면 그게 가장 좋다
4. label 과 placeholder에 기입된 내용은 달라야 한다

[폼확인site]: https://formspree.io/

