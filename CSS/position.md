# position

- CSS `position`속성은 문서 상에 요소를 배치하는 방법을 지정한다.
- <span style=color:red>`top, left, bottom, left`</span> 속성이 요소를 배치할 최종 위치를 결정한다.



## offset? 

- **`offset`**은 상대 주소의 개념이다.
- <span style=color:red>`top, left, bottom, left`</span> 값을 가진다.
- 기준이 되는 `element`가 있을 때 그 `element`의 가장 윗 지점이 `top : 0`이 되는 지점이다. 반대로 가장 아래 지점은 `bottom : 0`이 되는 지점이다.
- **기준이 되어줄 element가 있고 `offset`값을 지정한 `element`가 있다면 그 `element`의 <span style=color:tomato>가장 윗쪽이면서 가장 왼쪽인 모서리 꼭지점이 `offset`값에 맞게 위치한다.</span>**

### offset값의 단위

- `px`또는 `%`를 사용한다.
- `%`의 경우 `left,right`의 100%는 기준이 되는 element의 `width`값, `top, bottom`의 경우 100%는 기준이 되는 `element의 height`값이 된다.



```html
<style>
    .aa{ position:relative; width:200px; height:200px; border:1px solid black;}
    .bb{ position:relative; width:100px; height:100px; border:1px solid red; top:20px; left: 40px;}
</style>
<body>
    <div class="aa">
        <div class="bb">
        </div>
    </div>
</body>
```

<img src="https://github.com/cjy0019/TIL/blob/master/images/position.png?raw=true" alt="position.png" style="zoom: 67%;" />

- 이처럼 기준이 될 `element`에 상대적인 위치를 정하는 것이 `offset`이다.



## 위치 조정

- 일반적으로 `음수px`을 주면 바깥쪽으로 이동한다.
- 반대로 `양수px`을 주면 안쪽으로 이동한다.
- `top: 양수px`을 주면 아래로 이동하고, `top:음수px`을 주면 위로 이동한다.



## position의 기준점

### static

1. 문서의 흐름에 따른 기본 위치(기본값)
2. 즉, 모든 요소들은 처음에 `position:static`상태이다.
3. 차례대로 왼쪽에서 오른쪽, 위에서 아래로 쌓인다.
4. `top right bottom left`등 위치 속성은 무시된다.

### absolute

1. 자신의 상위 컨텐츠를 기준으로 절대적 위치를 잡는다.
2. 포토샵의 레이어처럼 또는 `float`처럼 부유하게 된다.
3. 레이어 형태로 부유하게 되면 부모요소의 영역을 차지하지 않게 된다. 
4. 즉 영역을 차지하지 않으면서 배치하고 싶은 곳에 마음대로 배치할 수 있다.
5. **(static이 아닌) 첫 번째 부모 요소 있으면 해당 부모 요소 기준.**
   - **부모 요소가 relative, absolute,fixed 속성 중 하나여야 한다. 즉, static이 아닌 모든 것이 기준이 된다.**

5. 만약 부모 요소가 **`static`**이 아닌 속성을 가지고 있지 않다면 계속해서 올라가다 `html`을 기준으로 움직인다.
6. `absolute`상태가 되면 `div`여도 더는 `width:100%`가 아니게 된다.

6. 스크롤 하면 위치가 변한다.

### relative

1. static일 때 해당 요소의 현재 기본 위치 기준
2. 요소의 위치를 살짝 변경할 때 주로 `position:relative`를 사용한다.
3. 정확한 위치는 `offset`을 기준으로 한다.

### fixed

1. 무조건 브라우저 창 기준이다.
2. 정확한 위치는 `offset`을 이용해 정한다.
3. 페이지 로딩이 늦는 원인이 될 수도 있으므로 각별히 사용하자.

### sticky

1. `relative`처럼 작동하다가, 스크롤 시 `top, left`값 위치 도달 시 거기에 고정된다.
2. 스크롤 상단 고정 메뉴를 만들 때 많이 사용된다.



## position : absolute 활용

### 중앙 정렬하기

```html
<div class="abs">가운데 정렬</div>
<span class="cent">스팬 가운데</span>
```

```css
.abs{
  padding : 50px;
  width: 300px;
  color; white;
  background-color:tomato;
  position: absolute;
  top: calc(50% - 50px);
  left: calc(50% - 150px);
  box-sizing: border-box;
}

.cent{
  position: absolute;
  top: calc(50% + 100px);
  left: calc(50% - 80px);
  box-sizing: border-box;
}
```

![center.PNG](https://github.com/cjy0019/TIL/blob/master/images/center.PNG?raw=true)



## width : 100% 만들기

```html
<div class="parent">
    <div class = "child">
    </div>
</div>
```

```css
.parent{
  width: 500px;
  height: 500px;
  border:5px solid red;
  position: relative;
}

.child{
  height: 200px;t
  background-color: skyblue;
  position: absolute;
  left: 0;
  right: 0;
}
```

<img src="https://github.com/cjy0019/TIL/blob/master/images/positionw100.PNG?raw=true" alt="positionw100.PNG" style="zoom:50%;" />

- 자식의 `width`를 설정하지 않고 `position:absolute`를 준다.
- 부모에게 기준점으로 `position:relative`를 지정해준다.
- 자식 요소에 `right:0 left:0`의 `offset`을 지정해주면 기준에 맞게 양쪽으로 쭉 늘어나는 것을 볼 수 있다.

