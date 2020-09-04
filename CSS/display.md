# display

- CSS의 display 속성은 그 값에 따라서 웹페이지를 보고 있는 사용자에게 특정 요소를 어떻게 보여줄지 결정한다.



### display 속성 값의 종류

일반적으로 다음 네 가지 속성을 많이 사용한다.

- none
- block
- inline
- inline-block



## display:none vs visibility:hidden

**공통**

- 둘 다 요소를 보이지 않게 하는 하는 속성이라는 점에서 공통점을 가지고 있다.

**차이점**

- `display:none`은 화면 상 어떤 영역을 차지하지 않고 완전히 삭제된 것처럼 보이게 한다.
- `visibility:hidden`은 해당 요소가 보이지 않을 뿐 요소가 존재하는 영역은 확실히 보이게 된다.



```html
<style>
    .display-none{ display : none}
    .invisible{ visibility : hidden}
</style>

<div class = "display-none">1</div>
<div>2</div>

<div class = "invisible">3</div>
<div>4</div>
```

```result
2

4
```



## display:block

- 일반적으로 블록 엘리먼트는 무엇가를 담는 그릇의 의미를 가지고 있다고 볼 수 있다.

**<블록 요소 리스트>**

`<adress> , <article> , <aside> , <audio> , <blockquote> , <dd>, <div> , <dl>, <fieldset>, <figcaption> , <figure>, <footer>, <form>, <h1>, <header>, <hgroup>, <hr> , <ol>, <p>, <pre>, <section> , <table> , <ul> 등`

### 특징

1. 다른 블록 엘리먼트와 인라인 엘리먼트 모두를 적재가능하다.
2. 일반적으로 블록엘리먼트는 새로운 줄에서 시작한다.(`width : 100%`)
3. 크기를 사용자가 지정할 수 있다.
4. vertical-align과 text-align이 작동하지 않는다.



## display:inline

- 일반적으로 데이터를 제공하는 요소들이 inline 엘리먼트이다.

**`<인라인 요소 리스트>`**

`<a> , <abbr> , <b> , <br>, <button>, <canvas>, <cite> , <code> , <del> , <em> , <i> , <iframe>, <img> , <label> , <map> , <mark> , <picture> , <progress> , <q> , <script> , <select> , <small> , <span> , <strong> , <sub> , <svg> , <template> , <time> , <u> 등`

### 특징

1. 다른 인라인 엘리먼트는 적재가 가능하지만 다른 블록 엘리먼트는 적재할 수 없다.
2. 일반적으로 인라인 요소는 전 엘리먼트 바로 옆에 붙어서 시작한다.(줄바꿈이 일어나지 않는다.)
3. `width, height`를 지정해도 무시된다.
4. 일반적으로 사용자가 크기를 지정할 수 없다. 컨테츠에 맞게 생성된다.
5. `vertical-align`과 `text-align`이 모두 작동한다.
6. `padding`은 좌우 공간과 시각적인 부분이 모두 적용되지만 공간은 차지하지 않는다.
7. `margin`을 지정할 수는 있으나 inline 요소 내부에 텍스트나 콘텐츠가 존재하는 영역 이외에는 실제 inline 영역의 값으로 인정받지 못한다.



## display:inline-block

- inline-block은 말 그대로 inline 특징과 block의 특징을 모두 가진 요소이다
- inline 요소의 배치 특성을 가지면서 영역 특성은 block특성을 갖는다. 
- 따라서 배치는 **수평**으로 가고 `height width`를 지정해 줄 수 있다.

### 특징

- 줄 바꿈이 이루어지지 않는다.
- `block`처럼 `width`와 `height`를 지정할 수 있다.
- 만약 `width,height`를 지정하지 않은 경우 inline과 같이 컨텐츠 만큼 영역이 잡힌다.

### 문제점

- `<li>`태그들을 `inlline-block`으로 지정해주면 `<li>`간에 공백 문자가 생겨서 원치 않는 공백이 발생하게 된다. 원래 `<li>`는 수직으로 배열되는 `block`요소 였기 때문에 수직으로 콘텐츠를 내려주면 **줄 바꿈** 문자가 수평으로 변하면서 공백 처리된다.

**해결**

- 임시적으로 해결하기 위해서 `<li>`의 부모 요소인 `<ul>`요소의 `font-size`를 0으로 지정해준다.