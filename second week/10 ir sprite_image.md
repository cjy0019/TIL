# DAY 10&#9989; (ir기법 /sprite 이미지/)

## image replacement 기법

**1. Phark Method**

-의미있는 이미지의 대체 텍스트를 제공하는 경우

설정방법: 이미지로 대체할 엘리먼트에 배경이미지를 설정하고 글자는 text-indent를 이용하여 화면 바깥으로 (-9999px만큼 내어쓰기 하는법) 뺴내어 보이지 않게함

```css
.ir_pm{display:block; overflow:hidden; font-size:0; line-height:0; text-indent:-9999px}
```

<b>2. WA IR</b>

-의미있는 이미지의 대체 텍스트로 이미지가 없어도 대체 텍스트를 보여줄 때

설정방법: 이미지로 대체할 엘리먼트에 배경이미지를 설정하고 글자는 span태그로 감싼후 z-index:-1을 이용하여 화면에 안보이게 처리한다

```css
.ir_wa{display:block; overflow:hidden; position:relative; z-index:-1; width:100%; height:100%;}
```

**3. Leahy/Langridge Method**

-이미지로 대체할 엘리먼트에 배경이미지를 설정하고 padding-top의 값을 이미지 높이만큼 주어 글자를 밑으로 밀어내어 숨기는 방법

```css
button {display:block;overflow:hidden;width:49px;height:36px;padding:36px 0 0 0;border:0 none;background:url(btn_search.gif) no-repeat}

a {display:block;overflow:hidden;width:49px;height:0px !important;height:36px;padding:36px 0 0 0;background:url(btn_search.gif) no-repeat}
```

```html
<button>검색</button> 
<a href="#">검색</a>
```



<h2>CSS counter</h2>

<p>CSS counter를 사용하려면 먼저 counter-reset을 초기화 해야한다. <u>counter의 이름으로 none, inherit, initial은 사용이 불가하다.</u><code>counter()</code>함수는 counter(name)와 counter(name,style) 두가지 형태로 사용할 수 있다.</p>

```css
body {
  counter-reset: section;                     /* counter 이름을 'section'으로 지정합니다.
                                                 초깃값은 0입니다. */
}

h3::before {
  counter-increment: section;                 /* section의 카운터 값을 1씩 증가시킵니다. */
  content: counter(section);                  /* section의 카운터 값을 표시합다. */
}
```
