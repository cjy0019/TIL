# float

- 최신 기법인 *flex*와 *grid*를 활용하여 간단하게 레이아웃을 구현할 수 있지만 **IE 크로스브라우징** 이슈를 고려한다면 **`float`**의 사용법도 알아야한다고 생각한다.

- 예전에 선형화 이슈를 해결하기 위해 CSS2에서 `<table>`을 사용하기 시작했는데 퍼포먼스가 최악이었다.
- 그 대안으로 normal flow를 벗어나서 배치해보려는 노력의 일환으로 **`float`**가 등장했다.
- 그러나 원래 **`float`**는 원래 레이아웃 용도가 아니기 때문에 그 특성으로 인한 문제점들이 있었고 이를 처리해주기 위한 추가 작업들이 존재한다.

<img src="https://poiemaweb.com/img/float.png" alt="float 이미지" style="zoom:70%;" />



## 특징

- `float` 프로퍼티는 해당 요소를 다음 요소 위에 떠 있게(부유하게) 한다. 즉 `Normal flow(위에서 아래로 차곡차곡 블럭이 쌓이는 것)`에서 벗어나게 된다.
- 떠 있다(float)는 의미는 요소가 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽에 이동하는 것이다.
- `float`된 요소는 `text요소`는 가리지 못해 자신의 영역만큼 텍스트를 밀어내게 된다.
- `float` 프로퍼티를 사용하지 않은 블록 요소들은 수직으로 정렬된다.
- `float` 프로퍼티는 좌측, 우측 가로 정렬만 할 수 있다. 중앙 가로 정렬은 `margin` 프로퍼티를 사용해야 한다.

<iframe width="878" height="494" src="https://www.youtube.com/embed/xara4Z1b18I" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- 두 `block`요소가 수직으로 쌓여 있을 때 `width` 값을 주지 않은 `block` 요소에 <code>float</code>이 선언 되면 inline 요소와 같이 `content`에 맞게 최소화된다.(`inline` 요소가 되는 것은 아니다)

- 이 때 아래쪽에 존재하던 `float`를 선언하지 않은 다른 `block` 요소는 <code>width:100%</code>를 유지하면서 첫 번째 박스 옆으로 붙게 된다.

```html
<div class="box box1">123</div>
<div class="box box2">123</div>
<div class="box box3">123</div>
```

```css
.box{
  height: 100px;
}
.box1{
  background-color: tomato;
  float:left;
}
.box2{
  background-color: aqua;
}
.box3{
  background-color: yellow;
}
```

![float.PNG](https://github.com/cjy0019/TIL/blob/master/images/float.PNG?raw=true)



# inline-block vs float



## inline-block 정렬

[inline-block 특징 설명](https://github.com/cjy0019/TIL/blob/master/CSS/display.md)

```html
<div class="inline">
  <div class="inline-item a"></div>
  <div class="inline-item b"></div>
  <div class="inline-item c"></div>
</div>
```

```css
.inline{
  width: 500px;
  background-color: green;
}

.inline-item{
  width: 100px;
  height: 100px;
  display: inline-block;
}
.inline-item.a{
  background-color: orange;
}
.inline-item.b{
  background-color: orangered;
}
.inline-item.c{
  background-color: red;
}
```

![inline-block.PNG](https://github.com/cjy0019/TIL/blob/master/images/inline-block.PNG?raw=true)

- `inline`요소가 되었기 때문에 `Enter`를 공백으로 인식하고 띄어쓰기가 삽입되었다.
- `inline-block`요소이기 때문에 text를 입력해보면 하단에 행간을 위한 공간과 `font`에서 고유로 적용되어 있는 **`descent height`**영역이 포함되어 있기 때문에 공간이 생긴다.



### 해결책

1. 부모인 `.inline`에 `font-size:0`을 주면 공백이 사라진다. (그러나 브라우저에 따라서 적용이 안될 수 있음)

2. ```css
   <div class="inline-item a"></div><div class="inline-item b"></div><div class="inline-item c"></div> <!-- 공백을 다 붙여서 작성하는 법 -->
   ```

3. ```css
   .inline-item.a{
     background-color: orange;
   }
   .inline-item.b{
     background-color: orangered;
     margin : 0 -4px;
   }
   .inline-item.c{
     background-color: red;
   } 
   <!-- 중간요소에 negative margin 주기  -->
   ```

4. `vertical-align`속성을 이용해서 아래 공백을 지워주기
5. `float`이용하기

**결론 : 이런 문제를 해결하지 않아도 되는 UI에 사용하자**



## float 정렬

위와 똑같은 예제를 사용하므로 `html`코드는 생략!

```css
.float-item{
  width: 100px;
  height: 100px;
  float:left;
}
.float-item.a{
  background-color: orange;
}
.float-item.b{
  background-color: orangered;
}
.float-item.c{
  background-color: red;
}
```

![float-item.PNG](https://github.com/cjy0019/TIL/blob/master/images/float-item.PNG?raw=true)

- 여백 이슈는 해결되었지만 부모 높이를 잃어버리고 `height:0`이 되어버린다.

### 해결책

1. 부모 높이를 `height:100px`로 지정해준다. (1차원적인 해결책이고, 유지 보수에 큰 어려움이 따른다. )

2. **overflow:hidden**

   ```css
   <!--부모요소 .float -->
   .float{
     width: 500px;
     background-color: green;
     text-align:center;
     overflow: hidden;
   }
   ```

- `overflow:hidden`은 부모 요소가 잃어버렸던 자식 요소를 찾게 도와준다.
- 그 근거는 **`BFC`**에 있다.
- `overflow`가 적용된 요소에는 `BFC(Block Formatting Context)`가 새로 만들어진다.
- `BFC`는 `<body>`안에 있는 작은 또 다른 `<body>`라고 생각하면 된다. `<body>`는 내부의 모든 요소를 포함하려고 한다. 이처럼 `BFC` 내부의 모든 요소는 이 블록 안에 속하게 되는 것이다.
-  `float`상태이더라도 요소를 포함하게 한다.
- **그러나 만약 부모요소 크기가 고정되어 있는 상태에서 자식의 `width height`가 더 커진다면 잘려나온다.**

3.  **clearfix**라는 가장 보편적인 방법이다

```css
.clearfix::after{
    content:'';
    display:block;
    clear:both;
}
```

- <u>가상 요소로 인해 만들어지는 `content`는 `span`과 같은 `inline`값을 가지고 있기 때문에 `dipsplay:block`을 선언해주는 것이 중요하다.</u>
- `clear`는 취소와 같다고 생각하면 된다.

![overflowhidden.png](https://github.com/cjy0019/TIL/blob/master/images/overflowhidden.png?raw=true)