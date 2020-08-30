# git add

## git staging

- 깃이 파일의 변경 내역을 저장하는데 곧바로 저장하는 것이 아니라 **"스테이징"**이라는 단계를 거친다
- 스테이징은 변경사항 중에서 **"저장하고 싶은 부분만 선택해 임시로 저장"**하는 개념이다.

```bash
git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)
  
  index.html
```

폴더에는 index.html 파일이 있는데 아직 깃이 트래킹하지 않아서 'Untracked files' 목록에 있다.

```bash
git add index.html
```

```bash
git status

Changes to be committed:
	new file: index.html
```

index.html 파일은 이렇게 커밋 직전 상태로 변경된다.



### git status 옵션

- `git status -s` : 상태를 간략하게 확인하기

| 문자 | 설명                                                         |
| :--: | ------------------------------------------------------------ |
| ???  | Git 프로젝트 디렉터리에 새로운 파일이 추가되었으나, Untracked인 파일이다 |
|  A   | 새로운 파일이 추가된 후 git add 명령을 통해 Staged 상태가 된 파일이다. |
|  M   | 앞자리는 공백, 뒷자리는 M 인 경우 워킹 디렉터리의 파일을 수정했지만 git add 하지 않은 not Staged 상태를 말한다. |
|  M   | 워킹 디렉터리에서 파일을 수정하여 Modified 상태인 파일을 git add로 Staging Area에 등록한 staged 상태를 말한다. |
|  MM  | 수정 후 git add 상태에서 Commit 하지 않고 다시 한 번 수정 후 git add 하지 않은 상태로 첫번째 수정 내역은 staged 상태이지만, 다시 수정한 내역은 git add 되지 않은 상태이다. |



### git add 옵션

```bash
git add <파일 이름>
git add *
git add *.*
git add .
```

**`git add .`** 개발하면서 절대 사용하면 안되는 옵션이라고 생각한다. 얼핏 파일명을 지정하지 않아도 되니까 편해 보이지만 어떤 내용이 커밋에 포함되는지가 완전히 감춰진다는 면에서 정말 좋지 않은 습관이라고 생각된다!



 ## git add -p

- 일반적으로는 `git status`로 파일 목록을 보고 원하는 파일만 `git add FILENAME`만 하는데 더 편한 방법이 git add -p이다.

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

  modified:   math.js
```

- 위처럼 `math.js`라는 파일을 수정했을 때 이를 스테이징하려고 `git add math.js`하거나 `git add .`을 할 수 가 있다.
- 스테이징하려고 하는 것은 파일 내의 변경 사항이지 파일이 아니기 때문에 git add math.js도 좋은 방식은 아니다.
- 그래서 스테이징을 하는 변경 사항을 확인하면서 작업하는 것이 좋고 실수를 방지할 수 있다.
- **`git add -p`**를 하면 modified 된 파일의 수정 부분을 단위 별로 나누어서 추가할지 안할지를 물어본다.

<img src="https://github.com/cjy0019/TIL/blob/master/images/gitadd.PNG?raw=true" alt="gitadd.PNG" style="zoom:50%;" />

- 현재 main.js는 스테이지에 올라가 있는 상태이다. 이 상태에서 내용을 추가해주면

<img src="https://github.com/cjy0019/TIL/blob/master/images/gitdiff.PNG?raw=true" alt="gitdiff.PNG" style="zoom:67%;" />

- `git diff`를 통해 어떤 내용이 더 추가되었는지 알 수 있다. 

![gitaddp.PNG](https://github.com/cjy0019/TIL/blob/master/images/gitaddp.PNG?raw=true)

- 마지막으로 `git add -p`를 사용하면 파일의 수정 부분을 단위별로 나누어서 스테이징 할 것인지 물어보게 된다.
- 여기서 보이는 변경사항의 하나의 단위를 <span style=color:blue>hunk</span>라고 부른다
- 보통 `y`를 누르면 해당 hunk를 스테이징에 추가하고 `n`을 누르면 추가하지 않고 `q`를 입력하면 `add`과정을 종료한다.

## git add - p의 장점

- 스테이지에 추가하기 전에 변경사항을 눈으로 확인할 수 있다. 이 과정에서 원하지 않은 부분을 제거할 수 있다.
- 커밋을 훨씬 논리적인 단위로 나눌 수 있다.
- untracked 파일은 -p를 할 때 나오지 않는다. 그래서 새로운 파일을 추가하는 행위를 의식적으로 할 수 있어서 실수를 줄여준다.