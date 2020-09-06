# sprite image

## 이미지 스프라이트(image Sprite)란?

- 배경 이미지를 적용할 경우 각각의 요소에 들어가는 배경 이미지를 낱개로 만들지 않고 비슷한 성격의 이미지를 하나의 파일로 제작 후 `background-position`을 이용하여 배경 이미지를 배치하는 방법이다.
- *주로 고정적으로 사용하는 이미지에 사용된다*
- 게임 개발의 2D 그래픽 프로세스에서 전통적으로 많이 사용해 온 방식이기도 하다.

<span style=color:red>**사용하는 이유는??**</span>

- 이미지가 많은 웹 페이지는 여러 서버에서 클라이언트의 `GET` 요청을 로드하고 생성하는데 시간이 오래 걸릴 수 있다.
- 이미지 스프라이트를 사용하면 서버 요청수가 감소하고 대역폭이 절약된다.
- 즉 **HTTP 요청(Request) 횟수를 줄일 수 있다는 것이다.**



## example

1. 

![daum_sprite.png](https://github.com/cjy0019/TIL/blob/master/images/daum_sprite.png?raw=true)

Daum의 경우 다음과 같은 이미지를 사용하고 있다.

2. 

![naver_sprite.png](https://github.com/cjy0019/TIL/blob/master/images/naver_sprite.png?raw=true)

Naver의 경우에도 메인 화면에서 다음과 같은 이미지를 사용하고 있다.



## 사용법

1. 먼저 그래픽 편집기를 사용해서, 이미지 파일에 포함된 특정 요소의 위치와 크기를 확인한다.
2. HTML 문서의 본문에 스프라이트 이미지를 표시할 `<div>`요소를 계층적으로 구성한다.

```html
<div id="container">
     <div class="sprite"></div>
</div>
```

3. CSS의 `background-image`프로퍼티와 `background-position`프로퍼티를 이용해서 스프라이트 이미지를 설정할 수 있다.

```css
width:52px;
height:52px;
background-image : url("spr_naver_01.png");
background-position: -136px -66px;
```

4. ![whale.PNG](https://github.com/cjy0019/TIL/blob/master/images/whale.PNG?raw=true)

- 원하는 이미지만 출력할 수 있게 된다.