# DAY 1&#9989;

## Git vs GitHub


- 깃(Git) :  컴퓨터 파일의 변경 사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 **분산 버전 관리 시스템**

- 깃 허브(GitHub) : 분산 버전 관리 툴인 깃을 사용하는 프로젝트를 지원하는 **웹 호스팅 서비스**


## Git 사용 순서(기본)
1. 디렉토리를 생성한 후 터미널에서 <code>$git init</code> 입력 -> __로컬 저장소__

2. 변경된 파일에 대해 <code>$git add 파일명</code> 을 입력하여 스테이지에 올린다

3. 확정된 버전에 관해서 <code>$git commit -m(메시지) "확정 버전에 대한 설명"</code> 입력해준다

4. 하지만, 아직 원격 저장소에는 반영되지 않았다

  

  ***원격 저장소 연동하기***

5. <code>$git remote add origin 원격 서버 주소</code> 입력한다

    - origin 이라는 이름으로 리모트 저장소가 등록되었다는 의미임
    - <code>$git remote remove origin</code> 을 통해 저장소를 삭제할 수 있다

6. 마지막으로 <code>$git push 원격 저장소 별칭 현재 브랜치 이름</code>
    ex) <code>$ git push origin master</code> 입력하여 원격 저장소에 PUSH 해준다



## CLI 명령어 정리

- **현재 작업 중인 폴더 확인**
  <code>$pwd</code> : print working directory
- **폴더 생성**
  <code>$mkdir</code> : make directory
  <code>$mkdir css js</code>로 css js 폴더 동시에 생성가능
- **파일 생성**
  <code>$touch</code>
- **디렉토리 이동**
  <code>$cd</code>
- **파일 목록 출력**
  <code>$ls</code> : list segments
  -a 숨겨진 목록을 모두 출력
  -la 숨겨진 목록을 포함하고 모든 목록을 출력할 때 권한 소유자, 그룹, 크기 등 상세 정보 표시
- **파일 내용 확인**
  <code>$cat</code>
- **&&**
  명령어 사이에 &&을 넣으면 차례대로 실행
  ex) <code>$mkdir images && cd images</code> : images 폴더 만들고 images 폴더로 이동
- **rm**(remove) : 파일을 삭제함
  **sudo**(super user do) : 관리자 권한으로 실행한다는 말이고 -rf(강제)는 옵션

## remove vs delete

- delete : 존재 자체가 제거됨
- remove : 어딘가에 존재는 하지만 해당 영역에서 사라짐

#

<h2> DTD(Document Type Definition)</h2>

<strong> DTD란?</strong>

- SGML 계열의 마크업 언어에서 문서 형식을 정의하는 것


<strong> 선언 이유</strong>

- 어떻게 선언하느냐 에 따라 브라우저의 렌더링 모드가 바뀜
- DTD를 선언하지 않을 경우 브라우저의 표준 모드가 아니라 비표준 모드(Quirks mode)로 렌더링되어 크로스 브라우징에 어려움을 겪게 됨
- <strong>크로스 브라우징의 가장 기초는 표준 모드 준수이다!</strong>
- <strong>웹 표준을 꼭 준수하자</strong>

# <span style=color:pink>commit message structure</span>

```bash
type : subject

body(옵션)

footer(옵션)
```

- **type ** : 어떤 의도로 커밋했는지 type에 명시한다. 
- **subject** : 최대 50글자가 넘지 않도록 하고 마침표는 찍지 않는다. 영문으로 표기하는 경우 동사를 가장 앞에 두고 대문자 표기!!
- **body** : 긴 설명이 필요한 경우에 작성함. 무엇을 왜 했는지 작성한다. 최대 75자
- **footer** : issue tracker ID를 명시하고 싶은 경우에 작성

## <span style=color:pink>type</span>

1. feat : 새로운 기능 추가

2. fix : 버그 수정

3. docs : 문서의 수정

4. style : (코드의 수정 없이) 스타일만 변경

5. refactor: 코드를 리팩토링

6. conf: configuration

   ![](https://raw.githubusercontent.com/legend80s/commit-msg-linter/master/assets/demo-4-compressed.png)

   출처 : https://github.com/legend80s/commit-msg-linter

## Licenses

- GNU License : 자유 소프트웨어 재단(FSF)에서 만든 자유 소프트웨어 라이선스다. 미국의 리처드 스톨만(Richard Stallman)이 GNU-프로젝트로 배포된 프로그램의 라이선스로 사용하기 위해 작성했다.

    ① 컴퓨터 프로그램을 어떤 목적으로든지 사용할 수 있다 

    ② 컴퓨터 프로그램의 복사를 언제나 프로그램의 코드와 함께 판매 또는 무료로 배포할 수 있다 

    ③ 컴퓨터 프로그램의 코드를 용도에 따라 결정할 수 있다 

    ④ 변경된 컴퓨터 프로그램 역시 프로그램의 코드와 함께 자유로이 배포할 수 있다' 라는 조항을 명시하고 있다

  

- MIT License : MIT 라이선스(MIT License)는 미국 매사추세츠 공과대학교(MIT)에서 해당 대학의 소프트웨어 공학도들을 돕기 위해 개발한 라이선스다. MIT 라이선스를 따르는 소프트웨어를 개조한 제품을 반드시 오픈 소스로 배포해야 한다는 규정이 없으며 GNU 일반 공중 라이선스의 엄격함을 피하려는 사용자들에게 인기가 있다. 이 라이선스를 따르는 대표적 소프트웨어로 X 윈도 시스템이 있다.

<h2> attribute vs property</h2>

<h4> 1. attribute 란?</h4>


- attribute는 html 문서에서 elements에 <u>추가적인</u> 정보를 넣을 때 사용되는 요소
- 정적인 속성 그 자체를 의미

<h4> 2. property 란?</h4>


- html DOM 안에서 attribute를 '가리키는' 표현
- 동적인 속성을 의미

<h4> 3. attribute 와 property를 구분하는 기준</h4>


- ex) <code>&lt;h1 class = "headline"&gt;</code> 에서 class 정보는 필수가 아닌 추가 요소

- ex) <code>font-size=16px / color="red"</code> 등의 속성은 처음부터 가지고 있는 특성이고 변경이 가능

  

<h2> front-end 개발자가 나아가야 할 방향</h2>


- 사용자에게 도움이 되는 웹사이트를 개발하는 것을 목적으로 해야 한다.

- SEO(검색엔진 최적화)란 검색엔진이 콘텐츠를 이해하고 제공하도록 돕는 것

  [SEO reference](https://support.google.com/webmasters/answer/7451184?hl=ko)

- OG(Open Graph) : Facebook이 웹 사이트에 더 풍부한 메타 데이터를 제공하기 위해 발명한 프로토콜

  [OG 상세](https://blog.ab180.co/open-graph-as-a-website-preview/)

- Semantic 요소를 의식하며 코딩해야 한다. HTML은 기본 프리젠테이션 스타일 기반이 아니라 나타낼 데이터를 기반으로 코딩해야 한다. '어떻게 보여져야 하는가?'에 대한 답은 CSS를 통해 얻을 수 있다.

- *내가 나타낼 데이터를 가장 잘 설명하는 태그 요소는 무엇인가?*  항상 고민해보자 (div는 차선이다!!)
