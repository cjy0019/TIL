# Flex

- Flex(플렉스)는 Flexible Box, Flexbox라고 부르기도 한다.
- Flexs는 레이아웃 배치 전용 기능으로 고안되었다.
- 따라서 기존의 float, inline-block 등의 기존 방식보다 훨씬 **강력하고 편리하다.**



## 호환성?

<img src="C:\Users\cjy00\Desktop\TIL\images\caniuse.PNG" style="zoom:50%;" />

**<span style=color:blue>인터넷 익스플로러에서도 지원이 될까?</span>**

- "Can I use" 닷컴에서 보면 IE 10과 11은 부분 지원임을 알 수 있다.
- 그러나, **MS(microsoft)는 2020년 11월 30일 기준으로 **에 대한 지원을 완전 종료한다고 발표했다.
- 따라서 더 이상 다음과 같은 걱정은 하지 않아도 된다.



## 사용법

Flex 레이아웃을 만들기 위한 기본적인 HTML 구조는 다음과 같다.

```html
<div class = "container">
    <div class="item">helloflex</div>
    <div class="item">abc</div>
    <div class="item">flexworld</div>
</div>
```

- **부모 요소**인 `div.container`를 `Flex Container`라고 부르고 **자식 요소**인 `div.item`들을 `Flex Item`이라고 부른다.

<img src="https://studiomeal.com/wp-content/uploads/2020/01/02.jpg" alt="img" style="zoom: 50%;" />

## Flex의 속성

- 컨테이너에 적용하는 속성
- 아이템에 적용하는 속성



### 컨테이너에 적용하는 속성

#### display:flex

- 가장 먼저 Flex 컨테이너에 `display:flex;`를 적용한다.

```css
.container{
    display : flex;
}
```

<img src="https://studiomeal.com/wp-content/uploads/2020/01/03.jpg" alt="img" style="zoom:50%;" />

- 아이템들이 배치된 방향의 축을 **메인축(Main Axis)**라고 한다.
- 메인축과 수직인 축을 **교차축(Cross Axis)**라고 부른다.

- Flex 아이템들은 가로 방향으로 배치되고 자신이 가진 내용물의 `width`만큼만 차지하게 된다.(`inline` 처럼)
- `height`속성은 컨테이너의 높이만큼 늘어난다.



##### display : inline-flex

![img](https://studiomeal.com/wp-content/uploads/2020/01/08-1.jpg)

- 마치 `inline-block`처럼 동작한다.



#### flex-direction

```css
.container{
    flex-direction : row;
    flex-direction : column;
    flex-direction : row-reverse;
    flex-direction : column-reverse;
}
```

- 아이템들이 배치되는 축의 방향을 결정하는 속성이다.
- 메인축의 방향을 가로 또는 세로로 할지 정한다.

**row(기본값)**

- 아이템들이 가로 방향으로 배치된다.

**row-reverse**

- 아이템들이 역순으로 가로 배치된다.

**column**

- 아이템들이 세로 방향으로 배치된다.

**column-reverse**

- 아이템들이 역순으로 세로 배치된다.



#### flex-wrap

- 컨테이너가 더 이상 아이템들을 한 줄에 담을 수 없을 때 줄바꿈을 결정해주는 속성이다.

```css
.container{
    flex-wrap : nowrap;
    flex-wrap : wrap;
    flex-wrap : wrap-reverse;
}
```

**nowrap(기본값)**

- 줄바꿈을 하지 않고 넘치면 삐져 나간다.

**wrap**

- 줄바꿈을 한다.

**wrap-reverse**

- 줄바꿈을 하면서 아이템을 역순으로 배치한다.
- 아래 있던 아이템이 위로가고 위에 있는 아이템이 아래로 내려간다.



#### flex-flow

- 앞서 설명한 `flex-direction`과 `flex-wrap`을 한번에 지정할 수 있는 단축 속성이다.
- **기본적으로 헷갈릴 수 있기 때문에 `flexbox`를 생성하면 동시에 `flex-flow : row nowrap`을 명시해주고 코딩을 하는 것이 도움된다.**

```css
.container{
    flex-flow: row wrap;
}
```



#### justify-content(메인축 방향 정렬)

```css
.container{
    justify-content: flex-start;
}
```

**flex-start(기본값)**

- 아이템들을 시작점으로 정렬한다.
- 만약 `flex-direction`이 `column`이라면 위쪽부터이다.

**flex-end**

- 아이템들을 끝점으로 정렬한다.

**center**

- 아이템들을 가운데로 정렬한다.

**space-between**

- 아이템들간 사이에 균일한 **간격**을 만들어준다.

**space-around**

- 아이템들의 둘레에 균일한 **간격**을 만들어준다.

**space-evenly**

- 아이템들의 사이와 양 끝에 균일한 간격을 만들어준다.

<img src="https://studiomeal.com/wp-content/uploads/2020/01/10-1.jpg" alt="img" style="zoom:50%;" />



#### align-items(수직축 방향 정렬)

```css
.container{
    align-items: stretch;
}
```

**stretch(기본값)**

- 아이템들이 수직축 방향으로 끝까지 늘어난다.

**flex-start**

- 아이템들이 시작점을 시작으로 정렬한다.
- `flex-direction`이 row이면 위쪽,`column`일 때는 왼쪽이다.

**flex-end**

- 아이템들을 끝으로 정렬한다.

**center**

- 아이템들을 가운데로 정렬한다.

**baseline**

- 아이템들을 텍스트 베이스라인 기준으로 정렬한다.



#### <span style=color:skyblue>align--content</span>

- `flex-wrap: wrap`이 설정된 상태에서, 행이 2줄 상이 되었을 때 수직축을 정렬하는 속성이다.

- 두줄(아니면 그 이상)을 한 꺼번에 정렬한다고 생각하면 된다.



## Flex 아이템에 적용하는 속성들

#### flex-basis

`flex-basis`는 Flex 아이템의 기본 크기를 설정한다.(`flex-direction`이 row 일 때는 너비, `column`일 땐 높이)

```css
.item{
    flex-basis : auto;
    flex-basis : 50%;
    flex-basis : 300px;
}
```

- `flex-basis`의 값으로는 우리가 `width, height`등에 사용하는 단위의 수가 들어갈 수 있다.
- `width`와 다른점은 `width`는 무조건 그 크기에 맞게 적용되는데 `flex-basis`는 설정 크기보다 작으면 늘어나고 더 크다면 컨텐츠의 길이만큼을 유지한다.



#### flex-grow(유연하게 늘리기)

- `flex-grow`는 아이템이 `flex-basis`의 값보다 커질 수 있는 지를 결정하는 속성이다.

```css
.item{
    flex-grow: 1;
}
```

- `flex-grow`에 들어가는 숫자는 아이템들의 **`flex-basis`**를 제외한 여백 부분을 `flex-grow`에 지정된 숫자 비율로 나누어 가진다는 의미이다.

```css
/* 1:2:1의 비율로 세팅할 경우 */
.item:nth-child(1) { flex-grow: 1; }
.item:nth-child(2) { flex-grow: 2; }
.item:nth-child(3) { flex-grow: 1; }
```



#### flex-shrink(유연하게 줄이기)

- `flex-shrink`는 아이템이 `flex-basis`보다 작아질 수 있는지를 결정한다.

```css
.item{
    flex-basis: 150px;
    flex-shrink: 1; /* 기본값 */
}
```

- `flex-shrink`를 0으로 세팅하면 아이템의 크기가 작아지지 않기 때문에 고정폭의 컬럼을 쉽게 만들 수 있다.



#### align-self

- `align-items`의 아이템 버전이다.

```css
.item{
    align-self: auto;
}
```

- 기본값은 auto로, 기본적으로 `align-items`설정을 상속 받는다.



## 배치 순서

#### order

- 아이템들의 시각적 나열 순서를 결정한다.
- "시각적 순서일 뿐", HTML 자체의 구조를 바꾸는 것은 아니다.
- 접근성과 `order`는 아무 관련이 없다.



#### z-index

- `z-index`는 z축을 정렬하는 속성이다.
- 숫자가 **클 수록** 위로 올라온다.

```css
.item:nth-child(2) {
	z-index: 1;
	transform: scale(2);
}
/* z-index를 설정 안하면 0이므로, 1만 설정해도 나머지 아이템을 보다 위로 올라온다 */
```

