<h1>Day11&#9989; Grid 정리</h1>

## q vs blockquote

인용임을 나타내는 태그에는 q와 block quote가 있다.

- 인용문의 출처는 cite 속성으로 나타내고 cite 속성은 선택사항이고 <u>브라우저에서는 보이지 않는다</u>
- q는 문단에서 <span style=color:red>인라인요소</span>이고 blockquote <span style=color:blue>블럭요소</span> 이다
- q요소의 기본모양은 인용문구를 큰 따옴표로 감싼게 됨
- blockquote 요소의 기본모양은 양쪽에 여백이 있는 것



<h2>address</h2>

address 요소는 가까운 HTML 요소의 사람, 단체, 조직 등에 대한 연락처 정보를 나타낸다

- 기존 명세에서는 문서 작성자의 연락처만 나타내는 요소였지만 최신 명세에는 임의의 연락처도 포함할 수 있다.
- <span style=color:yellow>연락처 외의 정보를 담아서는 안된다</span>
- 일반적으로 &lt;footer&gt; 요소안에 포함시킨다.



<h2>footer</h2>

- <a href="https://help.apple.com/voiceover/mac/10.15/">VoiceOver</a> 스크린 리더는 랜드마크 로터에서 푸터의 랜드마크 역할을 표현하지 못하는 문제가 있다.
- <span style=color:yellow>&lt;footer&gt;에 role="contentinfo"를 추가한다</span>



<h2>small</h2>

- 일반적으로 덧붙이는 글이나, <span style=color:yellow>저작권과 법률 표기 등</span>의 작은 텍스트를 나타낸다
- 기본 상태에서 <code>small</code>은 자신의 콘텐츠를 한 사이즈 작은 글꼴(small에서 x-small 등)로 표시하지만 글씨크기를 스타일상 작게둘 필요는 노노



<h2>CSS Grid&#128680;</h2>

<b>CSS Grid는 Container와 Item 이라는 두 가지 개념으로 구분되어 있음</b>
container는 item을 감싸는 요소로 흔히 알고있는 개념과 비슷하다

<h3 style=color:blue>Grid Container의 속성</h3>

|         속성          |                             의미                             |
| :-------------------: | :----------------------------------------------------------: |
|        display        |                    그리드 컨테이너를 정의                    |
|  grid-template-rows   | 명시적 행(Track)의 크기를 정의 <span style=color:red>(ex grid-template-rows: 100px 100px)</span> |
| grid-template-columns |                명시적 열(Track)의 크기를 정의                |
|  grid-template-areas  |            area의 이름을 참조해서 템플릿을 만든다            |
|     grid-template     |                           단축속성                           |
|     grid-row-gap      |              행과 행 사이의 간격을 정의(gutter)              |
|    grid-column-gap    |                  열과 열 사이의 간격을 정의                  |
|    grid-auto-rows     |                  암시적인 행의 크기를 정의                   |
|   grid-auto-columns   |                  암시적의 열의 크기를 정의                   |
|     align-content     |                  그리드 콘텐츠를 수직 정렬                   |
|    justify-content    |                  그리드 콘텐츠를 수평 정렬                   |
|      align-items      |                 그리드 아이템들을 수직 정렬                  |
|     justify-items     |                 그리드 아이템들을 수평 정렬                  |

<h3 style=color:blue>Grid Item Properties</h3>

|       속성        |                             의미                             |
| :---------------: | :----------------------------------------------------------: |
|  grid-row-start   |              그리드 아이템의 행 시작 위치 지정               |
|   grid-row-end    |               그리드 아이템의 행 끝 위치 지정                |
| grid-column-start |              그리드 아이템의 열 시작 위치 지정               |
|  grid-column-end  |               그리드 아이템의 열 끝 위치 지정                |
|     grid-area     | 영역 이름을 설정할 때 사용<span style=color:red> (ex grid-are:header;)</span> |
|    align-self     |                단일 그리드 아이템을 수직 정렬                |
|   justify-self    |                단일 그리드 아이템을 수평 정렬                |
|       order       | 그리드 아이템의 <span style=background-color:yellow>배치순서</span>를 지정 |
|      z-index      |              그리드 아이템의 쌓이는 순서를 지정              |

<h3 style=color:blue>Grid 기타</h3>

- grid-template-rows/ columns: fr(fraction, 비율) 이라는 단위를 사용할 수 있다 
- grid-template-areas 속성을 사용할 때 . 을 이용해서 빈 칸을 나타낼 수 있다

<img src="https://heropy.blog/images/screenshot/css-grid/grid-template-areas-2.jpg" style="zoom: 50%;" />

- grid-auto-rows 암시적 정의 속성으로 그리드 칸이 존재하지 않더라도 알맞게 자동으로 배치됨

<img src="https://heropy.blog/images/screenshot/css-grid/grid-auto-rows-1.jpg" style="zoom:50%;" />

- grid-auto-flow 어떤 플로우로 배치할 지 정하는 알고리즘? 이라고 생각한다

<img src="https://heropy.blog/images/screenshot/css-grid/grid-auto-flow-1.jpg" style="zoom:50%;" />

- <b>justify-content vs justify-items</b>

<img src="https://heropy.blog/images/screenshot/css-grid/justify-content-1.jpg" style="zoom:50%;" />

(justify-content)

<img src="https://heropy.blog/images/screenshot/css-grid/justify-items-1.jpg" style="zoom:50%;" />

(justify-items) : 자신이 속한 수평(가로줄) 속에서 배치가 됨.

[이미지 및 출처]: heropy.blog

