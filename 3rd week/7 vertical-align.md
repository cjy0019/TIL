<h1>Day7✅</h1>

<h2>title 속성의 바람직한 사용</h2>

title 속성의 정의

- title 속성은 요소에 대한 <span style="background-color:pink">조언 정보</span>를 나타낸다
- title 속성의 값은 <span style="background-color: #FFEF00">툴팁</span>으로 표시됨
- 요소에서 title 속성이 생략된다면 가장 가까운 부모 요소의 title 속성이 적용될 수 있음에 주의하자!

<strong>WCAG, KWCAG, NWCAG, NHN컨벤션 참고</strong>

공통적으로 제시

1. 링크 텍스트에 예고 없는 새 창을 표시해야 할 때, 추가적인 정보를 제공해야 할 떄 title 속성을 사용
2. 보조 기구에 따라 지원되지 않는 경우도 있기 때문에 주의를 기울여야 한다.
3. iframe 요소에 제목을 제공해야 할 때 title 속성을 사용합니다.
4. UI상 <span style="background-color: #ffa700">form 요소에 label 요소가 들어가기 어려울 때</span> title을 사용한다.



<h2>Framework vs Library</h2>

*프레임워크*

- 프레임워크는 '소프트웨어의 특정 문제를 해결하기 위해 상호 협력하는 클래스와 인터페이스의 집합이고 프로그래머가 완성시키는 작업을 해야한다'

- 객체 지향 개발을 하게 되면서 통합성, 일관성의 부족이 발생되는 문제를 해결할 방법중 하나이다.

  프레임워크의 특징

  - 특정 개념들의 추상화를 제공하는 <span style="background-color:#ffa700">여러 클래스 컴포넌트</span>로 구성됨

  - 컴포넌트들은 재사용이 가능함

    

*라이브러리*

- 단순 활용 가능한 도구의 집합을 말함.
- 개발자가 만든 클래스에서 호출하여 사용 클래스들의 나열로 필요한 클래스를 불러서 사용하는 방식을 취함.

**프레임워크는 전체적인 흐름을 스스로가 쥐고 있으며 사용자는 그 안에서 필요한 코드를 짜 넣으며 반면에 라이브러리는 사용자가 전체적인 흐름을 만들며 라이브러리를 가져다 쓰는 것이라고 할 수 있다**

<h2>calc()</h2>

<span style="color:pink">calc() 괄호 안의 식을 계산한 결과를 속성값으로 사용하게 해주는 함수</span>이다. 반응형이나 모바일 코딩을 하다 보면 %로 값을 주기가 애매한 것들이 있는데 이러한 것들을 calc함수로 지정해 줄 수 있다. 

*길이가 깔끔하게 떨어지지 않을 때 사용됨*

```css
font-size: calc(10px + 10px)
```

ex) width 값의 %를 나누기 애매할 경우에 사용함

```html
<ul class="list-with">
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
    <li>5</li>
    <li>6</li>
    <li>7</li>
</ul>
```

```css
.list_width>li{float:left; width:calc(100% / 7); height:56px; color: #fff; text-align:center}
.list_width>li:nth-child(odd){background:#333}
.list_width>li:nth-child(even){background:#999}
```



## Vertical-align

1 vertical-align 이란?

인라인 블록 등을 포함한 모든 인라인 요소의 수직 정렬을 위해서 사용된다. 하지만 블록 레벨에는 적용이 되지 않음

[참고]: http://blog.hivelab.co.kr/%EA%B3%B5%EC%9C%A0-vertical-align-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-1%EB%B6%80/



<h2>HTML의 img vs CSS의 background-img</h2>

두 방식 모두 목적은 같지만 존재하는 용도가 다르다

img 태그의 이미지 로드가 실패되면??

- broken image와 alt 텍스트가 보이게 된다
- SEO, 성능면에서 효율적이다

반면 background-image에 넣은 이미지가 에러나면??

- alt를 사용할 수 없고 결과적으로 broken-image도 어떤 테스트도 노출되지 않는다
- 따라서 더욱 img태그를 써야한다고 생각될 수도 있지만 컨텐츠 영역에서 있어도 없어도 그만인 이미지라면 굳이 텍스트나 이미지를 노출할 필요가 없다
- 순수하게 디자인을 용도로 사용한 이미지이기 때문이다

```
does this image help people in understanding my content better?
If the answer is yes - use img tag. If - no - set it as a background-image.
```



<h2>dl dt dd</h2>

HTML dl요소는 설명(definition) 목록을 나타낸다 

dl은 dt로 표기한 용어와 dd 요소로 표기한 설명 그룹의 목록을 감싸서 설명목록을 생성한다.

<strong>특이사항</strong>

- dl 요소의 자식으로 div 요소는 아무렇게나 작성할 수는 없다.
- HTML 5.2에서 dl의 콘텐츠 모델은 다음과 같음

<blockquote>Either: Zero or more groups each consisting of one or more dt elements followed by one or more elements, optionally intermixed with script-supporting elements. or one or more div elements, optionally intermixed with script-supporting elements.</blockquote>

<p>dl의 콘텐트 모델은 1개 이상의 dd 요소가 뒤따르는 1개 이상의 dt 요소들로 구성되는 0개 이상의 그룹 또는 1개 이상의 div 요소이다.
</p>

- **즉 dl 요소 안에 div로 dt와 dd를 감싸는 것은 가능하다 그러나 dl 내의 div는 dt와 dd외 다른 요소가 들어올 수 없다**
- dl 요소 내에 dt와 dd을 그룹핑한 div와 dt와 dd 요소는 서로 형제 노드 관계로 존재할 수 없다

