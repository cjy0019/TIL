# font

## font 속성

- `font`속성은 글자의 폰트를 정의하는 속성인데, 여러 기능을 동시에 가지고 있는 속성이기도 하다.
- 6개의 세부적인 글꼴 관련 속성을 `font`라는 하나의 속성에 한번에 쓸 수 있다.



### font-style

- 글꼴의 스타일로, 주로 이탤릭체(기울여 표시)를 설정하기 위해 사용한다.
  - `normal` : 기본으로 브라우저에서 기본 값으로 설정되어 있는 글꼴이 나온다.
  - `italic` : 기울임꼴이다.
  - `oblique` : 기울임꼴이다.
  - `initial` : 기본값으로 설정한다.
  - `inherit` : 부모 요소의 속성 값을 상속 받는다.

#### italic vs oblique

- `italic`과 `oblique`는 화면에 거의 똑같은 모양인 <u>이탤릭체</u>로 표기된다.
- HTML에서는 `<i>`태그로 이텔릭체를 표시하지만 `Semantic`하지 않기 때문에 css를 활용하는게 낫다.

`italic`은 흘려 쓴 서체(활자)이며, 그래서 이탤릭체라고 한다.

`oblique`는 원래 서체가 기울어진 모양이라고 한다.



### font-weight

- 글꼴의 두께로, 미리 정의된 단어나 100~900 사이의 숫자를 통해 설정한다.
- 기본 값은 `normal`이다.
  - 100 : `lighter`
  - 200
  - 300
  - 400 : `normal`
  - 500
  - 600
  - 700 : `bold`
  - 800
  - 900 : `bolder`



### font-size

- 글자 크기로, `<font>`태그의 `size`속성과 효과가 같다.
- 그러나 <del>HTML5 부터 `<font>`태그 사용은 권장되지 않고, `CSS`를 사용해야 한다.
- `px`,`em`,`rem` 등의 단위와 `small`,`big` 등의 상수 크기를 사용할 수 있다.



### font-family

- 글씨 서체를 지정하는 속성이다. 

- 글씨체를 `돋움`으로 할 경우 아래와 같이 작성하면 된다.

  ```css
  body{
      font-family : "돋움"
  }
  ```

- 그러나 위와 같이 지정하는 경우는 별로 없다. 지정하는 서체는 웹 페이지를 방문하는 방문자가 해당 서체를 가지고 있어야 하기 때문이다.

- 대부분의 국내 사이트에서는 대안으로 서체를 선언해준다.

  ```css
  body{
      font-family : "돋움", dotum, "굴림", gulim, arial, helvetica, sans-serif;
  }
  ```

- 가장 먼저 `돋움`을 선언했다. 만약 컴퓨터에 '돋움' 폰트가 있다면 해당 페이지는 '돋움'으로 출력이된다.

- 만약 '돋움' 서체가 없다면, 그 다음 선언된 서체를 찾는다.

- `돋움` ~ `helvetica` 까지 찾게 된다. 모두 없다면 `sans-serif`를 만나게 된다.

- 여기서 `sans-serif`는 서체 이름이 아니고 서체의 종류를 나타내는 문구이다.

- 앞선 모든 서체가 없다면, `sans-serif`형태의 서체를 적용하라는 선언이다.



#### 서체의 종류

- `Serif` 

  - 셰리프 형태의 서체는 글씨에 꺾쇠가 붙어져 있다. 

  ![serif.png](https://github.com/cjy0019/TIL/blob/master/images/serif.png?raw=true)

  - 이 셰리프는 줄의 연속성을 주게 되어, 보는 사람들에게 가독성을 높여준다.
  - 주로 서적의 본문이나 신문 인쇄물에서 자주 사용하게 되는 서체 형태이다.
  - 영어로는 `Georgia, Times New Roman`, 한글 서체로는 `바탕체, 궁서체, 명조체`

- `Sans-Serif`

  - 산셰리프에서 `Sans`는 "없음"을 뜻하는 프랑스어로 셰리프가 없는 글씨체를 말한다.
  - 국내에서는 `고딕체, 돋움, 굴림, 나눔 고딕` 영어 서체로는 `Arial, Helvetica`
  - 산세리프는 세리프에 비해 깔끔하고 세련되기 때문에 잡지와 같은 매체에서 사용된다.

- `Monospace`
  - `모노스페이스`라는 서체 형태는 고정 폭 서체이다.
  - 만약 `Aid`라는 글씨를 썼을 때 A와 i의 글씨 폭이 다른데 `모노스페이스`의 서체는 폭이 거의 같다.
  - 이런 서체는 주로 오타 없이 글자들간의 구분이 쉬워야 하는 코딩에서 주로 사용된다.
  - 한글은 보통 폭이 동일하여 영어만 존재하는데 `Courier New, Consolas, Monaco`가 해당됨
- `Cursive`
  - 커시브 형태는 커브가 많이 들어간 필기체 같은 형태를 말한다.
  - 커브가 심한 경우 가독성을 떨어트릴 수 있고, 비영어권에서는 글씨를 이해 못할 수도 있다.
- `Fantasy`
  - 일반적인 서체가 아닌, 개성 있고 장식성이 많은 서체를 나타낸다.
  - 많이 꾸며지기 때문에 글의 본문 보다는 제목에 좀 더 어울린다.



### font-variant

- 이 속성은 대소문자에 대한 스타일로, 대소문자가 있는 영어권에서 사용하는 속성이다.

- 소문자를 작은 대문자 형태로 표현할 수 있다.

  ```css
  p{
      font-variant : small-caps;
  }
  ```

  - `normal` : 기본적인 형태로 표현한다.
  - `small-caps` : 소문자를 작은 대문자 형태로 보여준다.
  - `inherit` : 상위 요소의 값을 상속 받는다.