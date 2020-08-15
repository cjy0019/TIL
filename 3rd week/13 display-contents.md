<h1>Day13&#9989;</h1>

<h2>background-size</h2>

- auto: 이미지의 크기를 유지한다
- length: 값을 두 개 넣으면 첫번째 값이 가로 크기, 두번째 값이 세로 크기이다. 값을 한 개 넣으면 <span style=text-decoration:underline>가로크기</span>이고 세로 크기는 원본 이미지의 가로 세로 비율에 맞게 자동으로 정해진다.
- cover: '중앙비율' div 영역 안에 백그라운드 이미지가 빈 틈 없이 매워지게 하는 가장 효과적인 방법 이미지의 일부가 잘리는 단점이 존재함
- contain: '원본비율' 이미지 전체가 보여지도록 설정이 된다 div의 크기에 따라서 이미지가 전체에 꽉 들어차지 못할수도 있다.



<h2>text-indent</h2>

- <span style=color:yellow>블록 레벨</span> 태그 내용의 왼쪽에 들여쓰기를 지정한다.
- a 같은 인라인 레벨에 적용하고 싶다면 display를 블록으로 주자
- inline 요소에는 적용되지 않는다



[grid calculator]: http://gridcalculator.dk/	""그리드 생성기""



<h2>display:contents</h2>

- display CSS 속성은 요소를 블록과 인라인 요소 중 어느 쪽으로 처리할지와 플로우, 그리드, 플렉스등을 정의 할 때 사용한다.
- display는 형식적으로는 요소의 내부와 외부 디스플레이 유형을 설정한다. 외부는 플로우 레이아웃에 요소가 참여하는 방법을 나타내고 내부 디스플레이는 자식의 레이아웃을 설정.
- display: contents - 이 요소는 이 자체로 특정한 박스를 만들지 않는다. 그들은 그들의 pseudo-box와 그들의 자식 박스에 의해 대체되어진다. 

유용한 이유?

- 과거에는 css로 스타일을 적용할 수 있도록 HTML을 마크업 해왔다. 이로 인해 div가 무지막지하게 나오게 됨. 그러나 이 속성을 사용하면 container를 사라지게 하고 DOM에서 다음 단계의 하위 요소를 생성해서 사용함.(IE/Edge 호환문제)

