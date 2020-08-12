<h1>Day3&#9989;</h1>

<h2>Box Model</h2>
<ul>
    <li>브라우저가 html문서를 읽고 파싱할 때 DOM tree가 구현됨</li>
    <li>그러나 tree 형태 보다 Box Model이 보기 편리함</li>
</ul>



<h4> 박스 모델 입문</h4>

<ul>
    <li>문서의 레이아웃을 계산할 때, 브라우저의 렌더링 엔진은 표준 CSS 기본 박스 모델에 따라 각각의 요소를 사각형 박스로 표현함</li>
    <li>하나의 박스는 아래와 같이 네 부분으로 이루어짐</li>
</ul>

![박스모델 이미지 by MDN](https://media.prod.mdn.mozit.cloud/attachments/2014/09/29/8685/0930aa361239ef7b22a8da798410a855/boxmodel-(3).png)

<ul>
    <li><strong>콘텐츠 영역(content area)</strong>: 콘텐츠 경계가 감싼 영역으로, 글이나 이미지, 비디오 등 요소의 실제 내용을 포함</li>
    <li>box-sizing의 기본값인 <code>content-box</code>인 경우 콘텐츠 영역의 크기를 width, min-width, max-width, height, min-height, max-height 속성을 이용해 명시적으로 설정 가능</li>
    <li><strong>패딩 영역(padding area)</strong>:padding edge가 감싼 영역으로, 콘텐츠 영역을 요소의 안쪽 여백까지 포함하는 크기로 확장가능 padding-top, right, bottom, left 속성 갖는다</li>
    <li><strong>테두리 영역(border)</strong>: 테두리 경계가 감싼 영역으로, 안쪽 여백 영역을 요소의 테두리까지 포함하는 크기로 확장. 영역의 크기는 테두리 박스 너비와 테두리 박스 높이이 <code>box-width</code>, <code>box-sizing:border-box</code>라면 테두리 영역의 크기를 width,min-width, max-width, height, min-heihgt, max-height 속성을 명시적으로 설정할 수 있음 </li>
    <li><strong>마진 영역(margin)</strong>: 바깥 여백 경계 margin edge 가 감싼 영역으로, 테두리 요소를 확장해 요소와 인근 요소 사이의 빈 공간까지 포함하도록 만듭니다. 영역의 크기는 바깥 여백 박스 너비와 바깥 여백 박스 높이입니다. 바깥 여백 영역의 크기는 <code>margin-top, margin-right, margin-bottom, margin-left</code>와 단축 속성인 margin이 결정.</li>
    <li>content-box는 요소의 너비를 100 픽셀로 설정하면 콘텐츠영역이 100 픽셀 너비를 가지고, 테두리와 안쪽 여백은 이에 더해집니다.</li>
<li>border-box는 테두리와 안쪽 여백의 크기도 요소의 크기로 고려합니다. 너비를 100 픽셀로 설정하고 테두리와 안쪽 여백을 추가하면, 콘텐츠 영역이 줄어들어 총 너비 100 픽셀을 유지합니다. 대부분의 경우 이 편이 크기를 조절할 때 쉽습니다.</li>
</ul>
<h1> 요소 정렬 이슈! </h1>

<h3>margin을 이용한 가운데 정렬</h3>

<h4><code>margin</code>이란?</h4>

<ul>
    <li>음수값 쓸 수 있다.</li>
    <li>border와 바깥과의 여백을 의미</li>
    <li><code>margin-top margin-right margin-bottom margin-left 속성 사용가능</code></li>
    <li>단축속성으로 <code>margin 위 오른쪽 아래 왼쪽</code>로 사용가능</li>
    <li><code>margin 위 [오른쪽&왼쪽] 아래</code></li>
    <li><code>margin [위&아래][오른쪽&왼쪽]</code></li>
    <li><strong>단, 폭의 연산이 불가능하면 가운데 정렬을 할 수 없다.</strong></li>
    <li>margin 0 auto는 양쪽에 여백을 계속적으로 주는 형태이기 때문에 <del>좋지는 않은(?)</del>방식이다</li>
    <li><code>margin:0 auto</code>를 사용하기 전에 <code>*,*::after,*before{box-sizing: border-box}</code>를 통해 요소들을 보더박스 상태로 만들어주는 것이 좋다</li>
</ul>


<h3>float를 활용한 레이아웃</h3>

<h5>flexbox 레이아웃을 사용해서 간단하게 정렬을 구현할 수 있지만 IE 크로스브라우징을 고려한다면 float property의 사용법도 알아야 한다.</h5>

선형화 이슈를 해결하기 위해 CSS2에서 table태그를 사용하기 시작했는데 퍼포먼스가 최악이었다. 그 대안으로 normal flow를 벗어나서 배치해보려는 노력으로 float를 사용하게 되었다고 한다. 또한 float는 원래 아웃라인을 위한 용도가 아니기 때문에 특성에 의한 버그를 처리하기 위해 추가로 필요로 되는 작업들이 있다.

<img src="https://poiemaweb.com/img/float.png" alt="float 이미지" style="zoom:70%;" />

<p><pre>
    - float 프로퍼티는 해당 요소를 다음 요소 위에 떠 있게(부유하게) 한다. 즉 Normal flow(위에서 아래로 차곡차곡 블럭이 쌓이는 것)에서 벗어나게 된다.떠 있다(float)는 의미는 요소가 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽에 이동하는 것이다. float 프로퍼티를 사용할 때 <U>요소의 위치를 고정시키는 position 프로퍼티의 absolute를 사용하면 안된다.(단, float된 요소는 text요소는 가리지 못해 자신의 영역만큼 텍스트를 밀어내게 된다)</U>     
    - float 프로퍼티를 사용하지 않은 블록 요소들은 수직으로 정렬된다. <code>float:left;</code> 프로퍼티를 사용하면 왼쪽부터 가로 정렬되고, <code>float:right;</code> 프로퍼티를 사용하면 오른쪽부터 가로 정렬된다.
    - float 프로퍼티는 좌측, 우측 가로 정렬만 할 수 있다. 중앙 가로 정렬은 margin 프로퍼티를 사용해야 한다.</p></pre>
<iframe width="878" height="494" src="https://www.youtube.com/embed/xara4Z1b18I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


[float속성 이해를 도와주는 애니메이션이다]

<ul>
    <li>두 블럭(block)요소가 수직으로 쌓여 있을 때</li>
    <li>width 프로퍼티를 선언하지 않은 block 요소에 <code>float</code>이 선언 되면 inline 요소와 같이 content에 맞게 최소화된다.(인라인 요소가 되는 것은 아니다)</li>
    <li>이 때 아래쪽에 존재하던 float를 선언하지 않은 다른 블럭요소는 <code>width:100%</code>를 유지하면서 첫번째 박스 옆으로 붙게 된다.</li>
</ul>




<h2>float의 문제와 해결 방법</h2>

float를 설정하면서 width를 설정해주지 않았다면 자동으로 박스내부의 컨텐츠 넓이만큼으로 크기가 설정되어 부유된다. 부유되면 부모박스가 자식박스가 가지고 있던 높이 값을 잃어버리게 된다. 이로 인해 아웃라인이 무너지게 된다.

<u>해결방법</u>

- float 된 요소 다음으로 오는 요소 박스에 clear:both를 지정해주면 float의 영향 밖에 자리를 잡는다. clear는 float된 요소의 height값 만큼의 마진을 주게 작동한다.
- :: 가상요소 선택자를 이용해 마지막 자식요소에 빈 컨텐츠와 clear:both, display:block 속성을 사용하여 해결할 수 있다.





<h4>float 프로퍼티가 선언된 요소와 float 프로퍼티가 선언되지 않은 요소간 margin이 사라지는 문제</h4>

<ul>
    <li>차례대로 정렬된 것처럼 보이지만 사실은 float 프로퍼티가 선언된 요소가 다음 요소 위에 떠 있는 상태이다. 따라서 두 요소간의 margin은 제대로 표현되지 않는다.</li>
    <li>이 문제를 해결하기 위해서는 float 프로퍼티를 선언하지 않은 요소에 <code>overflow:hidden</code>프로퍼티를 선언하는 것이다.</li>
    <li><code>overflow:hidden은 부모요소가 잃어버렸던 자식요소를 찾게 도와준다. 즉, BFC를 읽어들여 크기를 설정하게 된다.</code></li>
    <li>BFC(Block Formatting Context)는 그 안에 만들어진 모든 요소를 포함한다.</li>
    <li>BFC는 레이아웃 안의 작은 레이아웃이라고 생각하면 된다. BFC 내부의 모든 요소는 이 블록안에 속하게 된다. 내부 상태가 float이라도 마찬가지이다.</li>
    <li>float의 문제를 해결하는 다른 방법은 가상요소를 이용해 clearfix클래스를 따로 선언하는 것이다.주의 할점은 가상요소로 만들어지는 것은 <code>span</code>과 같이 inline 값을 가지고 있기 때문에 <code>display:block</code>을 선언해주는 것이 중요하다. </li>
</ul>

<h3>flex</h3> (display 속성의 값이다)

<ul>
    <p>
        Flexbox는 모던 웹을 위하여 제안된 기존 layout보다 더 세련된 방식의 니즈에 부합하기 위한 CSS3의 새로운 레이아웃 방식. 직계자식만 영향을 준다
    </p>
    <li>Flexbox 레이아웃은 <strong>flex item</strong>이라 불리는 복수의 자식 요소와 이를 내포하는 <strong>flex-container</strong>부모 요소로 구성된다.</li>
    <li><code>display:flex</code>를 선언한다.</li>
    <li><code>flex-direction</code>속성은 flex 컨테이너의 주축(main axis)방향을 설정한다. 기본값은 <code>flex-direction:row;</code>이다. 좌에서 우로 수평 배치된다. reverse는 우에서 좌로 수평 배치</li>
    <li><code>flex-direction:column;</code>위에서 아래로 수직 배치된다. reverse는 아래에서 위로 수직 배치된다.</li>
    <li><code>flex-wrap:nowrap</code>이 기본값이다. flex-item을 개행하지 않고 1행에 배치한다.</li>
    <li>그러나 flex-item들의 width의 합계가 flex 컨테이너의 width보다 큰 경우 flex 컨테이너를 넘치게 된다. 이때 <code>overflow: auto;</code>를 지정하면 가로 스크롤이 생기며 컨테이너를 넘치지 않는다.</li>
    <li><code>flex-wrap:wrap 과 wrap-reverse</code>의 차이</li>
    <li><code>justify-content</code>는 flex-container의 main axis를 기준으로 flex-item을 수평정렬한다. <code>justify-content:flex-start</code> 좌측을 기준으로 정렬하는 기본값이다. flex-end는 우측을 기준으로 정렬한다. center는 중앙</li>
</ul>

![](https://t1.daumcdn.net/cfile/tistory/996784405C7DBBEE23)

<ul>
    <li>align-items는 flex container의 수직 방향으로 정렬한다. 기본값은 stretch로 꽉찬 높이를 갖게된다. </li>
</ul>

