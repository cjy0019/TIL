# 용어 정리

## DTD(Document Type Definition)

**DTD란?**

- 우리말로 문서 형식 정의라고 한다.
- DTD는 컴퓨터 용어로, SGML 계열의 마크업 언어에서 문서 형식을 정의하는 것이다. SGML을 비롯해 HTML, XHTML, XML 등에 쓰인다. (feat.위키백과)

**SGML**(Standard Generalized Mark up Language)

- 문서용 마크업 언어를 정의하기 위한 메타 언어

### DTD 선언 이유

- 어떻게 선언하느냐 에 따라 <u>브라우저의 렌더링 모드가 바뀜</u>
- DTD를 선언하지 않을 경우 브라우저의 표준 모드가 아니라 비표준 모드(Quirks mode)로 렌더링되어 크로스 브라우징에 어려움을 겪게 됨
- <strong>크로스 브라우징의 가장 기초는 표준 모드 준수이다!</strong>
- 웹 표준을 꼭 준수하자



### 문서의 타입

- Strict 타입 : 엄격한 규격으로 CSS 사용을 장려하기 위해 단계적으로 사라질 표현에 관한 태그(font 태그)와 속성을 배제한 문서 타입을 뜻한다.
- Transitional 타입 : 과도기적인 규격으로 표준이 정립되지 않은 때에 기존에 만들어진 문서들과의 호환성을 위해 사용됨
- Frameset 타입 : 현재는 거의 사용하지 않는 프레임셋(html 안에 html을 분리하는 것)을 구현하는 데 사용한다.

## attribute vs property

<h4> 1. attribute 란?</h4>


- attribute는 html 문서에서 elements에 <u>추가적인</u> 정보를 넣을 때 사용되는 요소
- 정적인 속성 그 자체를 의미

<h4> 2. property 란?</h4>


- html DOM 안에서 attribute를 '가리키는' 표현
- 동적인 속성을 의미

<h4> 3. attribute 와 property를 구분하는 기준</h4>


- ex) <code>&lt;h1 class = "headline"&gt;</code> 에서 class 정보는 필수가 아닌 추가 요소

- ex) <code>font-size=16px / color="red"</code> 등의 속성은 처음부터 가지고 있는 특성이고 변경이 가능




## HTML5 이전

- HTML5 이전의 doctype은 SGML 기반이라 뒤에 DTD 참조 URL이 들어가야 했다.
- <span style=color:pink>HTML5의 경우 SGML에 기반을 두지 않아서 DTD 참조가 필요 없고, 최소한의 코드 작성이 기본 방향이라 매우 간단히 선언할 수 있다.</span>



## doctype 종류별 선언

```html
HTML 4.01 Strict
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

HTML 4.01 Transitional
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">

HTML 4.01 Frameset
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" http://www.w3.org/TR/html4/frameset.dtd">

XHTML 1.0 Strict
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

XHTML 1.0 Transitional
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

XHTML 1.0 Frameset
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">

XHTML 1.1
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">

HTML5
<!DOCTYPE html>
```

**DTD 선언은 태그가 아니기 때문에 </!DOCTYPE html> 이렇게 닫는 부분이 없다**



### 웹 표준에 있어서 DTD는 가장 먼저 선언되어야 한다



## front-end 개발자가 나아가야 할 방향


- 사용자에게 도움이 되는 웹사이트를 개발하는 것을 목적으로 해야 한다.

- SEO(검색엔진 최적화)란 검색엔진이 콘텐츠를 이해하고 제공하도록 돕는 것

  [SEO reference](https://support.google.com/webmasters/answer/7451184?hl=ko)

- OG(Open Graph) : Facebook이 웹 사이트에 더 풍부한 메타 데이터를 제공하기 위해 발명한 프로토콜

  [OG 상세](https://ogp.me/)

- Semantic 요소를 의식하며 코딩해야 한다. HTML은 기본 프리젠테이션 스타일 기반이 아니라 나타낼 데이터를 기반으로 코딩해야 한다. '어떻게 보여져야 하는가?'에 대한 답은 CSS를 통해 얻을 수 있다.

- *내가 나타낼 데이터를 가장 잘 설명하는 태그 요소는 무엇인가?*  항상 고민해보자 (div는 차선이다!!)
