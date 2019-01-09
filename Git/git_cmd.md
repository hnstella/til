# 유용한 Git 명령어 모음

## 최초 설정

### 사용자 설정

> git config --global user.name [name]

> git config --global user.email [email]

프로젝트마다 다른 정보를 사용하고 싶으면 --global 옵션 빼고 설정

### 편집기 설정

> git config --global core.editor "실행파일 경로"

ex) gVim 설정 : git config --global core.editor "'C:\Program Files (x86)\Vim\vim80\gvim.exe'"

### 설정 확인

> git config --list

## git show

> git show -s --date=short --pretty='format:%h ("%s", %ad)' <commit>

## git log - 커밋 히스토리 조회

### git -p

- 각 커밋의 diff 결과를 보여줌

### '-2'

- 최근 2개의 결과만 보여줌

> git log -p -2

### --stat

- 각 커밋의 통계 정보 조회

> git log --stat

### --pretty

- 히스토리 내용을 보여줄 때 여러가지 형식으로 보여줌

> git log --pretty=oneline
> 1c2e951be50ae7431a26c5c827312db63f79debd (HEAD -> dev, origin/master, origin/dev, master) 제목 수정
> d0ffd58d60478e88a86b168e59cd9c44a927c107 add README

> git log --pretty=format:"%h - %an, %ar : %s"
> 1c2e951 - hanakim, 7 days ago : 제목 수정
> d0ffd58 - hanakim, 7 days ago : add README

[git log --pretty=format 에 쓸 유용한 옵션](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0#pretty_format)

--graph 옵션 : 브랜치와 머지 히스토리를 보여주는 아스키 그래프 출력

> git log --pretty=format:"%h %s" --graph

코드에서 추가되거나 제거된 내용 중 특정 텍스트 포함되어 있는지 확인

> git log -S function_name

파일 경로로 검색하는 옵션

> git log -- path1 path2

[git log 주요 옵셤](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0#log_options)

## commit 하기 전, commit 할 때

### git diff

- whitespace 체크
- > git dif --chcck

## git status - 파일 상태 확인

> git status

짤막하게 확인하기

> git status -s

## .gitignore - 무시할 파일 설정

.gitignore 파일을 만들고 무시할 파일 패턴을 적는다.

- 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시한다.

- 표준 Glob 패턴을 사용한다. 이는 프로젝트 전체에 적용된다.

- 슬래시(/)로 시작하면 하위 디렉토리에 적용되지(Recursivity) 않는다.

- 디렉토리는 슬래시(/)를 끝에 사용하는 것으로 표현한다.

- 느낌표(!)로 시작하는 패턴의 파일은 무시하지 않는다.

[https://www.gitignore.io/api/eclipse](https://www.gitignore.io/api/eclipse)

## git diff - 파일 변경 내용 보기

기본적인 git diff는 Unstaged 상태인 것들만 보여준다.

Staging Area에 넣은 파일의 변경 부분 보기 : 저장소에 커밋한 것과 Staging Area에 있는 것을 비교

> git diff --staged

> git diff --cached

## git commit

메시지 인라인 첨부

> git commit -m "log message"

staging area 생략하기

> git commit -a

## git rm

Staging Area에서만 제거하고 워킹 디렉토리에 있는 파일은 지우지 않기

> git rm --cached FILENAME

## git add

### 변경되는 부분 확인하면서 추가하기

> git add -p

### add 취소하기

> git reset

# 링크

- [Git 명령어 정리](https://medium.com/@joongwon/git-git-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC-c25b421ecdbd)
