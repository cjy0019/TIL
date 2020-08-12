<h1>Day4</h1>

<h3>
    ARIA(Accessible Rich Internet Applications)
</h3>

장애가 있는 사람들이 웹 컨텐츠 및 애플리케이션을 보다 쉽게 이용할 수 있도록 하는 방법을 정의합니다.

<code>aria-hidden="true"</code>요소에 추가 하면 해당 요소와 모든 하위 요소가 접근성 트리에서 제거 된다. 스크린 리더 전용 텍스트라고 할 수 있다

<ul>
    <li>아이콘이나 이미지와 같은 순전히 장식적인 내용</li>
    <li>반복되는 텍스트와 같은 복제 된 내용</li>
    <li>메뉴와 같은 오프 스크린 또는 축소된 컨텐츠</li>사용하면 좋다
</ul>

<h2>Position</h2>

<ul>
    <h5>
        position:static<br>
    </h5>
    <li>모든 태그들은 처음에 <code>position:static</code>상태이다</li>
    <li>차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓인다(normal flow형태로)</li>
    <h5>
        position:relative<br>
    </h5>
    <li>태그의 위치를 살짝 변경하고 싶을 때 position:relative를 사용한다</li>
    <li>top right bottom left(offset) 속성을 이용해 위치를 조절</li>
    <li>top bottom right left가 적용되지 않기 때문에 무시할 때도 사용한다</li>
    <h5>
        position:absolute<br>
    </h5>
    <li>자신의 상위 컨텐츠를 기준으로 절대적 위치를 잡는다.</li>
    <li>포토샵의 레이어처럼 float와 비슷하게 부유하는 것처럼 됨.</li>
    <li>레이어 형태로 뜨게되면 부모요소의 영역을 차지하지 ㅇ낳게 된다.-> 영역을 차지하지 않으면서 배치하고 싶은 곳에 배치 시킬 수 있다.</li>
    <li>relative가 static인 상태를 기준으로 주어진 픽셀만큼 움직였다면</li>
    <li>absolute는 <strong>position:static 속성을 가지고 있지 않은 부모를 기준으로 움직인다</strong></li>
    <li>static 속성을 가지고 있지 않은 부모를 계속해서 찾아가다 html을 기준으로 판단한다</li>
    <li>만약 부모중에 포지션이 relative, absolute, fixed인 태그가 없다면 가장 위의 태그가 기준이 된다.</li>
    <li>absolute가 되면 div여도 더는 w:100%가 아니다</li>


<h2>display 속성</h2>

<ul>
    <li>css display 속성은 웹페이지 상에서 엘리먼트들이 어떻게 보여지고 다른 엘리먼트와 어떻게 상호 배치되는지를 결정한다.</li>
    <h4>
        inline
    </h4>
    <li>display 속성이 inline 으로 지정된 엘리먼트는 전후 줄바꿈 없이 한줄에 다른 엘리먼트들과 나란히 배치된다</li>
    <li>width와 height 속성을 지정해도 무시된다</li>
    <li>margin을 지정할 수는 있으나 inline요소 내부에 텍스트나 콘텐츠가 존재하는 영역이외에는 실제 inline 영역의 값으로 인정받지 못한다.</li>
    <li>padding은 좌우공간과 시각적인 부분이 모두 적용되지만 공간은 차지하지 않는다</li>
    <h4>
        inline-block
    </h4>
    <li>inline-block은 말그대로 inline 특징과 block의 특징을 모두 가진 요소이다</li>
    <li>inline 요소의 배치특성을 가지면서 영역특성은 block특성을 갖는다. 따라서 배치는 수평으로 가고 height width를 지정해 줄 수 있다.</li>
    <h5>
    문제점    
    </h5>
    <li>li태그를 inline-block으로 지정해주면 li태그간에 공백문자가 생겨서 원치 않는 공백이 발생하게 된다. 원래 li는 수직으로 배열되는 block요소 였기 때문에 수직으로 콘텐츠를 내려주던 줄바꿈 문자가 수평으로 변하면서 공백처리 된다. 이 공백문자가 li와 함께 ul태그의 자식요소로 인식되면서 실제로 index도 공백문자의 수만큼 늘어나는 문제가 있다. css로 공백을 해결해 주기 위해서 li의 부모요소의 ul font-size를 0으로 지정해준다.</li>
    <li>줄바꿈이 이루어지지 않는다</li>
    <li>block 처럼 width와 height를 지정할 수 있다</li>
    <li>만약 w, h 를 지정하지 않은 경우 inline과 같이 컨텐츠만큼 영역이 잡힌다</li>
</ul>


<h2>tabindex</h2>

<ul>
    <li>음의 정숫값<code>(tabindex=-1)</code>은 연속 키보드 탐색으로 접근할 수 없으나 JavaScript나 시각적으로는 포커스 가능함을 뜻한다.</li>
    <li><code>tabindex=0</code>은 기본값으로, 요소에 연속 키보드 탐색으로 접근할 수 있으며 그 순서는 문서 소스 코드의 순서에 따른다는 것을 나타낸다.</li>
</ul>

<h2>a11y</h2>

<ul>
    <li>a11y는 accessibility를 의미한다</li>
    <li>웹 접근성에 장애를 가진 사람들을 위한 방법이다</li>
    <li>이미지를 백그라운드 처리 후에 텍스트로 이미지에 대한 대체 텍스트가 필요한 경우나 시각적인 요소를 설명하기 위한 대체 텍스트가 필요한 경우에 <strong>대체 텍스트를 시각적으로는 감추고자 할때 사용하는 요소</strong></li>
    <li>a11y-hidden 클래스를 적용할 요소가 table에 caption일 경우 사용하자</li>
</ul>

<h2>Negative margins</h2>

<ul>
    <li>음수 마진은 문서 내의 정상적인 흐름을 건들이지 않는다</li>
    <li>요소를 이동하기 위해 음수 마진을 사용하면 그 뒤에 오는 모든 요소들도 같이 이동하게 된다</li>
    <li><code>float</code>이 적용되면 다르게 동작할 수 있음</li>
    <h5>
        static 요소에 음수마진을 사용하는 경우<br>
    </h5>
    <li><code>static 요소는 일반적으로 float이 적용되지 않는 요소라고 정의하면 음수 마진을 주면 그 방향으로 요소가 이동한다</code></li>
    <li><code>margin-top:-20px</code>이면 20px 위로 이동하게 된다</li>
    <li>하지만 <code>bottom/right</code>에 음수 마진을 사용하면 원소를 오른쪽이나 아래로 이동하는게 아니라 다음에 오는 요소를 끌어당기게 된다</li>
    <li>음수 마진을 적용하는 요소에 width를 주지 않고, left/right에 음수 마진을 사용하게 되면 엘리먼트의 width를 넓히는 효과가 나타나게 된다</li>
</ul>

<h2>clip-path</h2>

<ul>
    <code>clip-path</code> 속성은 요소의 클리핑 범위를 지정한다. 클리핑 범위안의 부분은 보여지고 바깥은 숨겨진다<br>
    <li><code>polygon()</code>속성을 사용하여 원하는 모양을 만들 수 있는데 좀 더 쉽게 적용하려면 Clippy를 사용할 수도 있다</li>
</ul>



