# white-space

`white-space` 는 스페이스와 탭, 줄바꿈, 자동줄바꿈을 어떻게 처리할지 정하는 속성이다.



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