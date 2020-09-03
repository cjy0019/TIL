# margin



## margin 특징

- <u>음수값</u>(negative margin) 쓸 수 있다.
- border와 바깥과의 여백을 의미
- `margin-top/ margin-right/ margin-bottom/ margin-left` 속성 사용가능
- 단축 속성으로 <code>margin 위 오른쪽 아래 왼쪽</code>로 사용가능
- margin 위 [오른쪽&왼쪽] 아래
- `margin: 0 auto`를 사용해서 가운데 정렬 이슈를 해결하기도 한다.
- 단, 폭의 연산이 불가능하면 가운데 정렬을 할 수 없다. 즉, `margin : auto`를 사용하기전에 전체 `width`에 값을 주어야한다.
- `margin : 0 auto`는 양쪽에 여백을 계속적으로 주는 형태이기 때문에 <del>좋지는 않은(?)</del>방식이다
- `margin:0 auto`를 사용하기 전에 <code>*,*::after,*before{box-sizing: border-box}</code>를 통해 요소들을 보더박스 상태로 만들어주는 것이 좋다



## Negative margins(음수 마진)

- 음수 마진은 문서 내의 정상적인 흐름(document flow)를 건들이지 않고 normal flow 상태로 작동한다.
- 요소를 이동하기 위해 음수 마진을 사용하면, **그 뒤에 오는 모든 요소들도 같이 이동하게 된다**.
- 마진이 시작/끝나는 지점을 브라우저에게 속이는 것이라고 이해할 수 있다.
- `margin-top, margin-left`는 시작하는 지점을 빠르게 한다
- `margin-bottom, margin-right`는 끝나는 지점을 빠르게 한다.

![negative margin](https://t1.daumcdn.net/cfile/tistory/264930405836BA1F2A)



#### static 요소에 음수마진을 사용하는 경우

- static 요소의 `top/left`에 마진을 주면 그 방향으로 이동하게 된다.
- 하지만, `bottom/right`에 음수 마진을 사용하면 이동하는 것이 아니라, 요소 다음에 오는 요소를 끌어당기게 된다.
- **음수 마진을 적용하는 요소에 width를 주지않고, `left/right`에 음수 마진을 사용하면 `width`를 넓히게 되는 효과가 나타난다.**



## margin collapsing(마진 병합)

- 흔히 **마진 상쇄, 마진 겹침 현상**이라고도 불린다.

- 하지만 마진이 겹치게 되면 상쇄가 일어나기 때문에 영미권에서는 **'margin collapsing'**이라고 부른다.

  

### MDN의 설명

<blockquote>블록의 top 및 bottom 마진은 때로는 (결합되는 마진 중 크기가) 가장 큰 한 마진으로 결합 된다. -MDN</blockquote>

![](https://github.com/cjy0019/TIL/blob/master/images/negative_margin.png?raw=true)

- `margin collapsing`은 의도된 것이다! 즉, 꼭 피해가야할 문제(?)는 아니고, 잘 알면 유용하게 사용할 수 있다.
- 각 section에 `margin:20px`을 적용했다. Section1 `margin-bottom:20px`과 Section2 `margin-top:20px`이 더해져 40px이 되야하지만, 20px만 적용되었다.



## 예시

**.children 요소의 `margin : 50px`이 적용되지 않는 것으로 보여지는데 이 또한 마진 병합현상이고 이는 해결해서 사용하는 것이 좋다!**

```html
<body>
  <div class="parents">
    <div class="children">A</div>
    <div class="children">B</div>
  </div>
</body>
```

```css
.parents {
  background-color: black;
  width: 300px;
  margin: 0 auto;
}

.children {
  width: 200px;
  height: 200px;
  background-color: orangered;
  color: rgba(255, 255, 255, 0.2);
  font-size: 150px;
  text-align: center;
  margin: 50px;
}
```

![](https://github.com/cjy0019/TIL/blob/master/images/margin_collapsing1.PNG?raw=true)

### 해결책

#### 1. parents와 children 사이에 요소를 추가하기

```html
<body>
  <div class="parents">
    margin-collapsing
    <div class="children">A</div>
    <div class="children">B</div>
  </div>
</body>
```

- 간단히 텍스를 추가하면 구분선이 생겨 둘을 떨어트릴 수 있다(예시를 위한 해결책임!)



#### 2. parents에 padding을 주기

```css
.parents {
  background-color: black;
  width: 300px;
  margin: 0 auto;
  padding: 1px;
}
```

- 공간을 차지하고 있는 요소를 넣어줌으로써 부모와 자식간의 관계를 분리시킨다



#### 3. parents에 border를 주기

```css
.parents {
  background-color: black;
  width: 300px;
  margin: 0 auto;
  border: 1px solid transparent;
}
```

- 하지만 공간을 차지하고 있는 부분이기 때문에 의도한 바와는 다르게 디자인 될 수 있다.



#### 4.  children에 block이 아닌 다른 display 속성 값을 주기

```css
.children {
  width: 200px;
  height: 200px;
  background-color: orangered;
  color: rgba(255, 255, 255, 0.2);
  font-size: 150px;
  text-align: center;
  margin: 50px;
  display: inline-block; //******변경*******
}
```

- 그러나 parents와의 문제는 해결했지만, 자식요소들끼리 병합현상이 생긴다.



#### 5. parents에 overflow : hidden을 주기

```css
.parents {
  background-color: black;
  width: 300px;
  margin: 0 auto;
  overflow: hidden;
}
```

- `overflow : hidden`이 `parents`에 적용되면 새로운 BFC가 만들어지면서 자식요소의 마진 값을 표현해주게 된다.

#### overflow

- <span style=color:tomato>`overflow`는 새로운 문서를 시작하는 일이라고 생각할 수 있다.</span>
- `overflow`가 부여된 요소는 독립적인 문서로 지정되면서 '작은 `<body>`영역처럼 동작하게 된다.



### margin collapsing의 특징

- 인접해있는 두 박스가 온전한 **`block-level`** 요소일 경우에만 적용된다.(`inline, inline-block, table-cell, table-caption`등의 요소는 `block-level`이 아니다.)

- `margin-top / margin-bottom`에만 해당된다.

- 마진 값이 0이더라도 상쇄 규칙은 적용된다.

  

### margin collapsing 예외

- 박스가 `position: absolute`된 상태
- 박스가 `float: left/right`된 상태(clear 되지 않았을 때)
- 박스가 `display:flex`일 때 내부 flexbox의 아이템
- 박스가 `display:grid`일 때 내부 grid item

