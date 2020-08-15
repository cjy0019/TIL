# Day12&#9989;

## Media Query

<span style=color:yellow>반응형의 핵심 부분!</span>

미디어 쿼리는 웹 브라우저가 HTML 문서의 실제 내용물을 표시하는 영역인 <b>뷰포트</b>를 조/정할 수 있다. 
대표적으로 <span style=color:yellow>랜드스케이프 모드</span>나 <span style=color:yellow>포트레이트</span>등 화면 모드에 따라서 컨텐츠를 배치할 수 있다.
(<span style=text-decoration:underline>익스플로러8에서는 지원하지 않는다</span>)

*viewport 속성 중 user-scalable: yes 가 기본 값으로 화면 확대/축소 여부를 결정함 

1. HTML 내에서 정의

```html
<link rel="stylesheet" media="screen and (max-width:800px)" href="css파일명"> 
/*링크 태그사용*/
```

2. style 태그 내에서 정의

```html
<style>
	@import url(CSS파일경로) screen and (min-width:0px) and (max-width:800px);
</style>
```

3. CSS 내에서 정의

```css
@media (only또는not) 미디어타입 (and) 조건{
/css 코드
}
```



## responsive image를 사용하는 이유

<img src="https://mdn.mozillademos.org/files/12940/picture-element-wide.png" style="zoom:50%;" />

<span> 노트북이나 태블릿처럼 화면이 넓은 기기에서는 잘 작동하지만 모바일 환경으로 가져왔을 때 문제가 생긴다 </span>

![](https://mdn.mozillademos.org/files/12936/non-responsive-narrow.png)

이처럼 문제가 생길 수가 있다. 헤드는 괜찮지만 모바일 기기에서는 화면 높이를 너무 많이 차지하게 된다

<b>개선책</b>

1. 모바일에서 사이트를 볼 때 이미지의 중요한 부분을 자른 이미지로 보여 주는 방법 보통 <b>아트 디렉션 문제</b>라고 부른다. 이미지의 의도를 제대로 전달하기 위해서 기기에 따라 핵심을 확대하거나 잘라서 보여주는 방식을 사용 해야한다.
2.  모바일 환경에서는 페이지에 큰 이미지를 포함시킬 필요가 없다. 이것은 <b>해상도 전환 문제</b>라고 부른다. 벡터 이미지와 달리 래스터 이미지는 가로와 세로가 <span style=color:red>가로 픽셀들과 세로 픽셀</span>로 구성되어 있어서 확대시 깨져 보인다. 대역폭을 낭비하는 것으로 볼 수 도 있다. <span style=color:blue>포토샵 등에서 이미지 파일을 저장할 때 반드시 웹용으로 저장해서 크기를 최소화하자!</span> 

[출처]: https://developer.mozilla.org/ko/



<h2>&lt;picture 태그&gt;</h2>

- 매체 따라 그림의 방향, 크기, 이미지 형식 따위에 변화를 주고자 할 때 주로 사용한다.

```html
<picture>
	<source srcset="/media/examples/batman.jpg" media="(min-width: 800px)">
    <img src="/media/example/spiderman.jpg"/>
</picture>
```



<h2>git fork vs git clone</h2>

fork는 다른 사람의 깃허브에서 내가 어떤 부분을 수정하거나 추가 기능을 넣고 싶을 때 내 레포에 해당 레포를 그대로 복제하는 기능이다

- fork한 저장소는 원본과 연결되어 있다.
- original 레포에 새로운 커밋이 생기면 그대로 내 레포에 반영된다.



clone은 특정 레포를 내 local에 복사하여 새로운 저장소를 만드는 것이다. 

- 원본 저장 레포의 커밋 등의 로그를 보지 못한다.



## 기타

transform: translateX(-100%) -> 왼쪽으로 이동할 때 사용하는 기법 left 오프셋을 주는 것보다 성능 면에서 뛰어남