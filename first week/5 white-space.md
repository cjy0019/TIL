<h1>Day5✅</h1>

<h2>display</h2>

<ul>
    <strong>display:inline;</strong>
    <li>대표적으로 &lt;span&gt;이라는 태그의 성질로 content크가 만큼만 점유하고 한 라인에 붙는다</li>
    <li>단점: width/height 적용 불가, margin/padding-top,bottom 적용 불가, line-height 적용 불가</li>
    <strong>display:inline-block;</strong>
<li>중요한 성질 자체는 inline과 비슷하지만 inline의 단점들을 커버</li>
<li>width/height 적용 가능, margin/padding 적용 가능, line-height 적용 가능</li>
<li>단 inline-block끼리 공백이 생기는데 상위 div에 font-size:0을 적용한다</li>
</ul>

<h2>font-family</h2>
<ul>
    <li><code>font-family</code>글꼴 집합이다 즉 여러개의 글꼴을 모아놓은 것이다</li>
    <li>만일 글꼴을 하나만 지정하면 사용자의 컴퓨터에 그 글꼴이 없을 때 기본값으로 표시가 된다</li>
    <li>이는<strong>family-name</strong>과 <strong>generic-family</strong>로 나뉜다</li>
    <ul>
        <li>family-name은 글꼴이름으로 arial, verdana, 나눔고딕, 궁서, 굴림 등을 나타낸다</li>
        <li>generic-family는 모양이 비슷한 글꼴들의 그룹이고 Serif(바탕체), Sans-serif(고딕체), Cursive(필기체) 등을 나타낸다</li>
    </ul>
</ul>

<h2>border-radius</h2>

<ul>
    <li><code>border-radius:1em</code>모든 귀를 나타냄</li>
    <img src="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3650/23ca97bf00fc8a3e9f0da344a8018d57/corner1.png"  />
    <li><code>border-radius: 1em 2em</code>첫 번째 값은 좌상 및 우하귀, 두 번째는 우상 및 좌하귀를 나타냄</li>
    <img src="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3651/2e15a8b51bf36f2dfaa414bdd1e4647e/corner2.png"/>
    <li><code>border-radius: 1em 2em 3em</code>첫 번째 값은 좌상귀, 두 번째는 우상 및 좌하귀 세 번째는 우하귀를 나타낸다</li>
    <img src="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3652/3b711371db73a4167346ab6123d60c6c/corner3.png"/>
    <li><code>border-radius: 1em 2em 3em 4em</code>네 값은 각각 좌상, 우상 우하, 좌하귀를 나타냄 시계방향!</li>
    <img src="https://media.prod.mdn.mozit.cloud/attachments/2012/07/09/3653/7f0722de752664d4324b5d5784113db5/corner4.png"/>
</ul>



<h2>text-transform</h2>

    text-transform 속성은 문자를 바꿔서 표시해준다
<ul>
    <li><code>none</code>기본값으로 텍스트를 html 코드에 있는 그대로 읽는다</li>
    <li><code>capitalize</code>각 단어의 첫번째 문자를 대문자로 만듦</li>
    <li><code>uppercase</code>모든 문자를 대문자로 바꾼다</li>
    <li><code>lowercase</code>모든 문자르 소문자로 바꿈</li>
</ul>


<h2>white-space</h2>

<img src="https://user-images.githubusercontent.com/51959017/87776638-0cc86a80-c863-11ea-92e1-be0c52c5d486.png" style="zoom: 67%;" />

분홍색 영역은 position:absolute 이고 기준으로 삼는 부분은 하얀색의 header영역이기 때문에 wrap되어 벗어나지 못하고 밀려 내려오는 것을 알 수 있다.

<img src="https://user-images.githubusercontent.com/51959017/87777229-156d7080-c864-11ea-87c9-110fad58570b.png" style="zoom:67%;" />

이 때 white-space:nowrap을 이용하여 기준영역밖으로 벗어날 수 있게 해준다.

<ul> 요소 안에 공백 처리를 어떻게 할지 지정하는 속성
    <li>normal : 기본값, 공백을 여러개 넣어도 공백 1개만 표시, 글이 길어지면 텍스트가 자동 줄바꿈</li>
    <li>nowrap : 공백을 여러개 넣어도 1개만 표시, 텍스트가 길어도 줄바꿈 되지 않고 같은 줄에 표시</li>
    <li>pre: 연속 공백을 유지 줄 바꿈은 &lt;br&gt;에서만 일어남</li>
    <li>pre-wrap: 연속 공백 유지. 줄 바꿈은 개행 문자와 &lt;br&gt; 요소에서 일어나며, 한 줄이 너무 길어서 넘칠 경우 자동으로 줄을 바꿉니다.</li>
    <li>다음 차이점을 제외하면 pre-wrap과 동일합니다.
연속 공백이 줄의 끝에 위치하더라도 공간을 차지합니다.
연속 공백의 중간과 끝에서도 자동으로 줄을 바꿀 수 있습니다.
유지한 연속 공백은 pre-wrap과 달리 요소 바깥으로 넘치지 않으며, 공간도 차지하므로 박스의 본질 크기(min-content, max-content)에 영향을 줍니다.</li>
</ul>

[이미지 출처]: https://github.com/kym123123/TIL/blob/master/2ndsweek/2020-07-17.md




<h2>text-decoration</h2>

<ul>
    글씨 장식은 모드 하위 요소에 적용된다
    <li>자식 요소는 부모가 적용한 장식을 제거할 수 없습니다</li>
    <li>그러나 부모요소가 text-decoration:underline을 설정하고 자식요소가 text-decoration:overline하면 위아래 모두 줄이 그어지는 것을 볼 수 있다</li>
</ul>

<h5>ex) 간단하게 a 태그의 장식 없애는 예제</h5>

1. &lt;a href="https://naver.com"&gt;&lt;/a&gt;
2. a:visited{color:black; text-decoration:none;}
3. a:hover{color: blue; text-decoration: underline;}



<h2>text-shadow</h2>

text-shadow: h-shadow vshadow blur color | none | initial

<ul>
    <li>h-shadow 필수 지정. 수평 그림자 위치 길이값(px,em 등) 양수 값을 지정하면 <strong>박스 오른쪽에 그림자가 드리워지고</strong> 음수 값은 박스 왼쪽에 그림자가 드리워짐</li>
    <li>v-shadow 필수 지정. 수직 그림자 위치(px,em 등) 양수 값은 박스 위쪽에 그림자가 드리워지며, 음수 값은 박스 아래쪽에 blur 선택 지정, 그림자의 흐림 반경</li>
    <li>blur 선택 지정 그림자의 흐림 반경, 길이값 0으로 지정하면 그림자가 진하고, 숫자가 높아지면 흐릿해짐</li>
</ul>



<h2>background-position
</h2>

1. background-position: pixel과 %로 원하는 위치만큼 이동시킬 수 있다.

2. multi-background: 멀티 백그라운드에서는 나중에 배치된 상자가 위로 올라온다



<h2>transition-timing-function</h2>

<ul>
    CSS속성의 시작과 끝을 지정(전환 효과)하여 중간 값을 애니메이션
    <li><code>transition-property</code>전환 효과를 사용할 속성 이름 기본값 all</li>
    <li><code>transition-duration</code>전환 효과의 지속시간을 설정 1000ms=1s</li>
    <li><code>transition-timing-function</code>타이밍함수 지정 기본값은 ease</li>
    <ul>
        &lt;타이밍 함수 종류&gt;
        <li>ease : 빠르게-느리게</li>
        <li>linear : 일정하게</li>
        <li>ease-in : 느리게-빠르게</li>
        <li>ease-out : 빠르게-느리게</li>
        <li>ease-in-out : 느리게-빠르게-느리게</li>
        <li>cubic-bezier : 자신만의 값을 정의</li>
        <li>steps(n) : n번 분할된 애니메이션</li>
    </ul>
    <li>transition-delay : 몇초 뒤에 실행하게 될지 정하는 속성</li>
</ul>



<h2>transform</h2>

요소의 변환 효과를 지정

<ul>
    &lt;2D 변환 함수&gt;
    <li>translate(x,y) : 이동(x축 y축)</li>
    <li>scale(x,y) : 크기(x축 y축) 확대할 때 사용</li>
    <li>rotate(degree) : 회전(각도deg)</li>
    <li>skew(x-deg,y-deg) : 기울임(비튼다)</li>
</ul>


    position은 어떤 값을 배치하고 끝낼 때 사용한다 반면 transform은 계속해서 변화하는 값에 사용한다
    즉, :hover를 사용할 때는 transform:translate가 더 적절함
<ul>
    &lt;3D 변환함수&gt;
    <li> 2D 변환과 같은 함수를 가지는 데 z축이 추가된다 단 z축은 우리눈과 같은 방향이기 때문에 perspective 뷰로만 확인할 수 있다</li>
    <li>rotate3d(x,y,z,a)</li>
    <li>perspective(n) : 원근법(거리)</li>
</ul>

backface-visibility : 3D 변환으로 회전된 요소의 뒷면을 숨긴다

transform-origin: 시작점을 설정한다. 웹에서 x축 y축이 반전되어 보인다
transform-style: 3D변환 요소의 자식요소도 3D변환을 사용할지 결정함 기본값:flat 
값:preserve-3d 자식요소의 3d변환이 이루어짐

<h4>perspective vs transform:perspective()</h4>

관찰 대상이 여러개면 부모요소에 perspective를 주고 관찰 대상이 하나면 transform:perspective()를 관찰대상에만 준다







[^[1\]]: 자연스럽게 흘러가는 배치를 뜻

