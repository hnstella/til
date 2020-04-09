# branch 관리

## 리모트 저장소의 브랜치 받기

> git checkout -t [원격 저장소의 branch 이름]

- 저장소와 동일한 이름으로 가져오게 된다 (ex: origin/dev)

### 원격 저장소 브랜치 이름을 변경하여 가져오기

> git checkout -b [생성할 branch 이름][원격 저장소의 branch 이름]

## 로컬 브랜치 삭제

> git branch -d [branch]

## 브랜치 작업

### 브랜치 신규 생성

> git checkout -b dev_hana // 해당 branch로 포인터 옮김
> git add -p
> git commit -v
> git push origin dev_hana

merge request 후 처리

> git checkout master
> git merge dev_hana
