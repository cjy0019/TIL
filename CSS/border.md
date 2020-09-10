# border

- `CSS`에서 박스 `div`나 여러 요소에 테두리 스타일을 줄 수 있는 것이 바로 `border`속성이다.

![box.png](https://github.com/cjy0019/TIL/blob/master/images/box.png?raw=true)

- 기본적으로 모든 요소는 사각형의 형태를 띄고 있다.
- 따라서 테두리 또한 역시 네 개의 방향을 가지고 있다.



## border를 구성하는 세가지 요소

- border는 각 변마다 선의 `width`, `style(선의 형태)`, `color(선의 색상)`를 지정할 수 있다.



### 선 굵기(border-width)

- 선의 굵기는 `px`이나 `em`등의 단위를 쓸 수 있고, 보통은 `px`을 많이 사용한다.

```css
div {
    border-top-width : 3px;
}
```

- `border-방향-요소` 방식으로 작성한다.



### 선의 형태(border-style)

```css
div{
    border-right-style : dotted;
}
```



#### border-style 기능 속성

- `none` : 선을 없앤다. 대부분 요소의 기본 값이다.
- `solid` : 실선의 형태로 적용됨
- `dotted` : 점선의 형태로 적용됨
- `dashed` : 바느질선 같은 형태로 적용됨.
- `double` : 이중 선의 형태로 굵기가 `3px`이상이 되어야 볼 수 있다.
- `groove` :  입체적으로 선을 홈이 들어간 것처럼 보여준다. 최소 `2px`은 되어야 확인 가능
- `ridge` : `groove`와 비슷하지만, 음영 값이 반대라 선이 돌출되어 보인다.
- `inset` : 요소 전체가 안으로 들어가 보인다.
- `outset` : inset의 반대이다. 요소 전체가 밖으로 돌출되어 보인다.
- `inherit` : 부모의 속성을 상속받습니다.



### 선의 색상(border-color)

- 선의 색상을 결정한다.

```css
div{
    border-bottom-color : #aaa;
}
```



## 단축 속성

- 만약 요소의 상단에 3px 굵기의 빨간 점선을 넣고 싶다면 다음과 같이 작성한다.

```css
div {
    border-top-width: 3px;
    border-top-style: dotted;
    border-top-color; red;
}
```

- 하지만 매우 비효율적이기 때문에 단축 속성을 사용한다.

```css
div{
    border-top: 3px dotted red;
}
```



#### width 단축 속성

```css
div{
    border-width: 3px 2px 1px 2px;
}
<!-- top 부터 시작해서 시계방향으로 회전한다 -->
```



## border-radius

- `border-radius`는 테두리를 둥글게 만드는 속성이다.
- 8개의 속성 값을 넣어야 하지만 값이 같다면 단축 속성으로 가능하다.
- 속성의 값에는 `px,%` 등 길이 단위를 넣는다.
- 8군데의 길이는 다음과 같다.

<img src="https://github.com/cjy0019/TIL/blob/master/images/borderradius.png?raw=true" alt="borderradius.png" style="zoom: 67%;" />

```css
border-radius : top-left-x top-right-x bottom-right-x bottom left-x / top-left-y top-right-y bottom-right-y bottom left-y 
```



#### 동작 방식

![borderradius1.gif](https://github.com/cjy0019/TIL/blob/master/images/borderradius1.gif?raw=true)

- `radius`이라는 말 그대로 네 부분의 모서리에 대해 radius를 설정 해주는 방식이라고 생각하면 된다.
- 값을 주는 방법의 하나로 `%`를 사용하는 경우가 있는데, 이 때 `0%`의 기준은 보더 박스의 가로와 세로에 대한 내부원의 반경에 대한 백분율이다.
- 즉 `0%`는 90도의 각이 되는 것이다.

[border-radius generator](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Background_and_Borders/Border-radius_generator)