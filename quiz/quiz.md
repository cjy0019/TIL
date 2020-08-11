<h1>quiz</h1>

<h2>margin 겹침</h2>

```
블록의 top 및 bottom 마진은 때로는 가장 큰 마진으로 결합 또는 상쇄 된다.
쉽게 말해서, 어떤 두 개 이상의 블록 요소의 상하 마진이 겹칠 때 한쪽 값만 적용하는 브라우저의 렌더링 방식이다.
```

마진 상쇄가 일어나는 3가지 상황

1. 인접 형제 박스 간 상하 마진이 겹칠 때

<img src="https://media.vlpt.us/post-images/raram2/97e16a40-121f-11ea-aaba-65695302c179/01-margin-collapsing-sibling-case.png" style="zoom: 33%;" />

2. 빈 요소의 상하 마진이 겹칠 때

빈 요소란 높이가 0인 상태의 블럭 요소를 말한다. 

- height/ min-height/padding/border 등 상하로 늘어나는 프로퍼티 값을 명시로 주지 않거나 내부에 inline 콘텐츠가 존재하지 않는 요소 이 경우엔 경계가 없으므로 더 큰값으로 상쇄한다.

<img src="https://media.vlpt.us/post-images/raram2/ffac75c0-121f-11ea-aaba-65695302c179/02-margin-collapsing-emptybox-case.png" style="zoom: 33%;" />



마진 병합 예외

- 박스가 <code>position:absolute</code>일 때
- float: left/right 된 상태
- display : flex | grid 일 때 내부 item

[출처]: https://velog.io/@raram2/CSS-%EB%A7%88%EC%A7%84-%EC%83%81%EC%87%84Margin-collapsing-%EC%9B%90%EB%A6%AC-%EC%99%84%EB%B2%BD-%EC%9D%B4%ED%95%B4



<h2>baseline 문제</h2>

<img src="https://lh6.googleusercontent.com/8VjiT5ETvPugZvKRjBGr6r8yPgxJzUrcdsmbRBhMmn6vhT5BTAerPG8rd-fI4-VCGCjaD6joJwG849jsI0jpRFXvkcvNfJNrCf0D0kSjypEIy15xGrVx7KOanfNY=w450" style="zoom: 80%;" />다

다음 코드에서 이미지 아래에 2px 정도의 baseline이 남아 배경색이 표시되는 문제가 있다. 이를 해결하기 위한 두 가지 방법을 사용했다. 방법에 맞는 코드는?

답: block, middle

img 태그가 inline의 속성을 가지고 있기 때문에 생기는 문제로 inline-block은 해결할 수 없다.



<h2>focus</h2>

focus를 기본적으로 받을 수 있는 태그는?

a태그 button태그 input태그



<h2>clearfix</h2>

group에 float를 적용하게 되면 부모인 main이 자식 요소인 group을 알 수 없게 되어 높이를 잃어버리고, 뒤쪽에 오는 다른 요소들에게도 float이 영향을 끼치게 되기 때문에 clearfix를 사용하여 float을 해제하고 부모가 자식의 높이를 인지할 수 있도록 해야 한다.



<h2>명시도</h2>

!important가 있더라도 명시도 점수가 높은 쪽이 우선 적용된다.



<h2>반응형에서 max-width:100%</h2>

이유는?

이미지가 원본사이즈 이상으로 커지지 않게 하기 위해서(원본사이즈 이상으로 이미지가 커지게 되면 이미지의 선명도에 문제가 생긴다.)



<h2>picture 태그</h2>

img태그가 무조건 있어야 한다.