
<h2>text-transform</h2>

    text-transform 속성은 문자를 바꿔서 표시해준다
<ul>
    <li><code>none</code>기본값으로 텍스트를 html 코드에 있는 그대로 읽는다</li>
    <li><code>capitalize</code>각 단어의 첫번째 문자를 대문자로 만듦</li>
    <li><code>uppercase</code>모든 문자를 대문자로 바꾼다</li>
    <li><code>lowercase</code>모든 문자르 소문자로 바꿈</li>
</ul>

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





<h2>clip-path</h2>

<ul>
    <code>clip-path</code> 속성은 요소의 클리핑 범위를 지정한다. 클리핑 범위안의 부분은 보여지고 바깥은 숨겨진다<br>
    <li><code>polygon()</code>속성을 사용하여 원하는 모양을 만들 수 있는데 좀 더 쉽게 적용하려면 Clippy를 사용할 수도 있다</li>
</ul>





[^[1\]]: 자연스럽게 흘러가는 배치를 뜻

ㅌ