# form 태그

`<form>`태그는 웹 페이지에서의 입력 양식을 의미한다. 로그인 창, 회원가입 창 등이 이에 해당된다.

텍스트 필드에 글자를 입력하거나, 체크박스, 라디오 버튼을 클릭하고 submit 버튼을 누르면 백엔드 서버에 양식이 전달되어 정보를 처리하게 된다.

간단히 입력 양식 전체를 감싸는 태그라고 할 수 있다. 일반적으로 `<fieldset>`과 함께 사용된다.



## form attribute 종류

- <del>name</del> :  양식의 이름, 서버로 보내질 때 이름의 값으로 전송된다. 하지만 HTML4부터 사용이 중단되어 대신 id를 사용한다.
- action : 양식 데이터를 처리할 프로그램의 URI. 만약 `<button>`이 제출 버튼인 경우, action 특성보다 우선하게 된다.
- method : 양식을 제출할 때 사용할 HTTP 메서드.
  - post : POST 메서드. 양식 데이터를 body에 담아 전송한다.
  - get : GET 메서드. 양식 데이터를 action URL과 ? 구분자 뒤에 이어 붙여서 전송한다.
  - dialog : 양식이 `<dialog>`안에 위치한 경우, 제출과 함께 대화 상자를 닫는다.

- accept-charset : 스페이스로 구분한, 서버가 허용하는 문자 인코딩의 목록 **기본 값은 페이지 인코딩과 같다**

- autocomplete: 입력 요소가 자동완성된 값을 기본값으로 가질 수 있는지 나타낸다
  - *off* : 브라우저가 각 항목에 자동으로 값을 채워 넣지 않는다
  - *on* : 사용자의 과거 입력 값에 기반하여 브라우저가 자동으로 값을 채워 넣음.



## form 태그 내부 input

- input 요소는 웹 양식에서 사용자의 데이터를 받을 수 있는 **대화형 컨트롤러**를 생성합니다.

- input 태그의 required 속성은 폼 데이터가 서버로 제출되기 전 반드시 채워져 있어야 하는 입력 필드를 명시한다.
- required 속성은 불린 속성으로 해당 속성을 명시하지 않으면 속성 값이 자동으로 false 값을 가진다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&amp;fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNncO5%2Fbtqwi1g1R8p%2FKKL2b3TlSRLnKSVmXC4Ekk%2Fimg.png" width="40%">

### Type

input의 동작 방식은 type 특성에 따라 현격히 달라진다. 기본 값은 text이다.

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
- password : 한 줄 텍스트 필드로 값은 obscured함
- range : 정확한 값을 필요로 하지 않을 때, 기본 값이 중간 값인 범위 위젯으로 표시됨

<img src="https://www.jqueryscript.net/images/Custom-Range-Input-Plugin-jQuery.jpg" width="40%" />

- eset : 폼을 기본 값으로 리셋시키는 버튼 ~~NOT RECOMMENDED~~
- search : 한 줄의 텍스트 필드로 줄 바꿈은 자동으로 제거됨. 필드를 지우는 데 활용 가능한 삭제 아이콘이 포함될 수 있다.
- submit : 제출을 위한 버튼 폼이다.
- tel : 전화번호를 입력받는 컨트롤이다.
- text : 기본 값으로 한줄 텍스트 필드이다 줄바꿈은 자동으로 제거됨
- url : URL을 입력할 수 있는 필드이다. 텍스트 input 같지만 유효성검사 파라미터를 가지고 있고 동적인 키보드를 지원



## fieldset

`<fieldset>`요소는 웹 양식의 여러 컨트롤과 레이블(label)을 묶을 때 사용합니다.

- fieldset은 HTML 양식 속에서 그룹을 만들 수 있고 legend 요소로 그룹의 설명을 제공할 수 있다. 가능한 넣어주는게 좋다 필요하다면 숨김 가능
- 여러 특성을 지정할 수 있는데 그 중 중요한 것은 form요소의 id를 받을 수 있는 form특성으로 form 바깥의 fieldset 요소를 양식에 포함할 때 사용해야 한다.
- `display : block`이 기본 값



## label


- label은 폼의 양식에 이름을 붙이는 태그이다
- 주요 속성은 **for**인데 양식의 **id**의 값이 같으면 연결된다
- label 요소는 브라우저에 의해 일반적인 텍스트로 렌더링 되지만, 사용자가 마우스를 클릭할 경우 label요소와 연결된 요소를 곧바로 선택할 수 있어 **사용자 편의성에 큰 도움이 된다.**