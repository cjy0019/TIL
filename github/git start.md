# git vs github

## git vs github



### 깃(git)  

- 컴퓨터 파일의 변경 사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 **분산 버전 관리 시스템**
- 로컬에서 관리되는 버전 관리 시스템(VCS : Version Control System)

### 깃 허브(github)

- 깃 허브(github) : 분산 버전 관리 툴인 깃을 사용하는 프로젝트를 지원하는 **웹 호스팅 서비스**
- 클라우드 방식으로 관리되는 VCS
- 자체 구축이 아닌 빌려쓰는 클라우드 개념

### 

## git config 설정(계정 설정)

- git을 설치하면 git의 사용 환경을 적절하게 설정해야한다. 설정 내용은 git을 업그레이드해도 유지된다.

```bash
$ git config --global user.name "cjy0019"
$ git config --global user.email cjy0029@naver.com
```

프로젝트 마다 다른 `Email`을 사용하고 싶다면 `--local` 옵션을 사용한다.

```bash
$ git config --list

core.editor=vim
core.pager=cat
user.email=cjy0029@naver.com
user.name=cjy0019
remote.origin.url=https://github.com/cjy0019/TIL.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*

```

`git config --list`를 사용해서 여러 설정들을 확인할 수 있다.



## editor

- `git commit`명령어를 사용해서 커밋을 할 때 해당 커밋이 어떤 변경을 포함하는지 설명을 담아야한다. 이 때 본인이 사용하기 쉬운 editor를 설정해서 사용하는 것이 편리하다.

```bash
$ git config --global core.editor notepad
```

```bash
$ git config --global core.editor "vim"
```

- 위 명령어를 통해 텍스트 편집기를 vi나 메모장으로 바꿀 수도 있다.

