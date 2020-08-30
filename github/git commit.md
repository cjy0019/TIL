# git commit

- 스테이징된 파일들을 로컬 저장소(Local Repository)로 등록을 해야한다. 그러기 위해서 `git commit`을 사용한다.
- `git commit`을 하면 현재 스테이징된 파일들을 그대로 **스냅샷**으로 찍어서 로컬 저장소에서 보관하게 된다.
- 이 스냅샷이 하나의 히스토리 기록이 된다고 할 수 있다.
- 기록을 이용하여 과거로 돌아갈 수 있고 미래로 갈 수 도 있고 다른 브랜치로 이동할 수 있는 기준점이 된다.

```bash
$ git commit -m "버전에 대한 설명"
```



## git commit -v

------

`git commit -v`도 `git add -p`와 마찬가지로 커밋하는 변경사항을 다시 한 번 확인하려는 의도이다.

- 코드를 올리는 과정에서 이러한 절차를 자주 넣어줌으로 실수할 확률을 크게 낮춰준다.

![gitcommitv.PNG](https://github.com/cjy0019/TIL/blob/master/images/gitcommitv.PNG?raw=true)

`git commit -v`를 하면 커밋메시지를 입력하는 화면 아래에 코드 diff가 한 번 더 나오게 된다. 작업을 하다보면 스테이지에 추가 후 바로 커밋할 때도 있지만, 복잡한 경우 이 두 과정의 시차가 있는 경우도 있다고 한다.

커밋을 하기 전에 `git diff --staged`로 확인할 수도 있지만 `git commti -v`로 보면 한 번 더 커밋하는 변경사항을 확인할 수 있다.



## commit message structure

------

```bash
type : subject

body(옵션)

footer(옵션)
```

- **type** : 어떤 의도로 커밋했는지 type에 명시한다.
- **subject** : 최대 50글자가 넘지 않도록 하고 마침표는 찍지 않는다. 영문으로 표기하는 경우 동사를 가장 앞에 두고 대문자로 표기한다.
- **body** : 긴 설명이 필요한 경우에 작성한다. 무엇을 왜 했는지 작성한다. 최대 75자
- **footer** : issue tracker ID를 명시하고 싶은 경우에 작성

## type

------

1. feat : 새로운 기능 추가

2. fix : 버그 수정

3. docs : 문서의 수정

4. style : (코드의 수정 없이) 스타일만 변경

5. refactor: 코드를 리팩토링

6. conf: configuration

![](https://raw.githubusercontent.com/legend80s/commit-msg-linter/master/assets/demo-4-compressed.png)

### example

```bash
$ git commit -m "feat : implement AVOD content reels"

$ git commit -m "fix : routing issue on the main page"

$ git commit -m "fix(player) : fix player initialization"

$ git commit -m "refactor(auth) : improve refresh token logic"
```



## Licenses

- GNU License : 자유 소프트웨어 재단(FSF)에서 만든 자유 소프트웨어 라이선스다. 미국의 리처드 스톨만(Richard Stallman)이 GNU-프로젝트로 배포된 프로그램의 라이선스로 사용하기 위해 작성했다.

  ① 컴퓨터 프로그램을 어떤 목적으로든지 사용할 수 있다 

  ② 컴퓨터 프로그램의 복사를 언제나 프로그램의 코드와 함께 판매 또는 무료로 배포할 수 있다 

  ③ 컴퓨터 프로그램의 코드를 용도에 따라 결정할 수 있다 

  ④ 변경된 컴퓨터 프로그램 역시 프로그램의 코드와 함께 자유로이 배포할 수 있다' 라는 조항을 명시하고 있다

- **MIT License** : MIT 라이선스(MIT License)는 미국 매사추세츠 공과대학교(MIT)에서 해당 대학의 소프트웨어 공학도들을 돕기 위해 개발한 라이선스다. MIT 라이선스를 따르는 소프트웨어를 개조한 제품을 반드시 오픈 소스로 배포해야 한다는 규정이 없으며 GNU 일반 공중 라이선스의 엄격함을 피하려는 사용자들에게 인기가 있다. 이 라이선스를 따르는 대표적 소프트웨어로 X 윈도 시스템이 있다.