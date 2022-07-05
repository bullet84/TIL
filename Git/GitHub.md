# GitHub
## 원격 저장소 사용하기
### GitHub 레포지토리 생성 후 복붙 명령어
`git remote add origin "원격 저장소 주소"`
* 로컬의 Git 저장소에 원격 저장소로의 연결 추가
    * 원격 저장소 이름에 흔히 origin 사용, 다른 것으로 수정 가능

`git branch -M main`
*기본 브랜치 명을 main 으로

`git push -u origin main`
* 로컬 저장소의 커밋 내역들 원격으로 push(업로드)
    * `-u` 또는 `--set-upstream` : 현재 브랜치와 명시된 원격 브랜치 기본 연결

### GitHub에서 프로젝트 다운받기
* `Download ZIP` : 파일들만, Git 관리내역 제외
* `Git clone` : Git 관리내역 포함 다운로드

원하는 위치에서

`git clone "원격 저장소 주소"`

---
## push 와 pull
### 원격으로 커밋 밀어 올리기(push)
`git push "원격저장소" "브랜치"`
> `git push -u`으로 대상 원격 브랜치가 설정된 경우 `git push`만으로 업로드 가능

### 원격의 커밋 당겨오기(pull)
`git pull`

### pull 할 것이 있을 때 push 하면?
**에러가 발생**
>로컬의 내용이 뒤쳐져 있기 때문

**pull 하는 두가지 방법**
* `git pull --no-rebase` : merge
* `git pull --rebase` : rebase

### pull 할 때 충돌이 발생할 경우
사용자가 선택하여 pull

### 로컬의 내역 강제 push
`git push --force`
>pull 하지 않고도 push 가능, 원격상 내용 날아갈 수 있음
---
## 원격의 브랜치 다루기
### 로컬에서 브랜치 생성 이후
`git push -u origin "새 브랜치명"`

`git branch --all`
>로컬 뿐 아니라 원격상의 브랜치도 보여줌

### 원격의 브랜치 로컬에 받아오기
`git fetch`
>로 원격의 변경사항 확인

`git switch -t origin/"원격의 브랜치명"`
>로컬에 같은 이름의 브랜치를 생성하여 연결하고 switch

### 원격의 브랜치 삭제
`git push "원격 이름" --delete "원격의 브랜치명"`