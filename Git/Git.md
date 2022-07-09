# Git

## Git 최초설정
Git 전역으로 사용자 이름과 이메일 주소를 설정
>GitHub 계정과는 별계

터미널 프로그램에서 아래 명령어 실행
|Code|기능|
|:--|:--|
|`git config --global user.name "본인이름"`|사용자 이름 설정|
|`git config --global user.email "본인이메일"`|사용자 이메일 설정|
|`git config --global init.defaultBranch "브랜치명"`| 기본 브랜치명 변경|
> "본인이름", "본인이메일"을 제외하고 작성하면 이름, 이메일 확인
---
## 프로젝트 생성 & Git관리 시작
원하는 위치에 원하는 이름으로 폴더 생성

`git init` 입력

폴더에 숨김 모드로 .git 폴더 생성
> 해당 폴더에 Git관리내역 저장됨

폴더안에 여러 파일 생성

`git status` 입력

|Code|기능|
|:--|:--|
|`git init`| 해당폴더 관리 시작|
|`git status`| 해당폴더 상태 확인|
---
## Git관리에서 특정 파일/폴더를 배제
* 포함할 필요가 없을 때
    * 자동으로 생성, 다운로드되는 파일들
* 포함하지 말아야 할 때
    * 보안상 민감한 자료들

폴더 안에 ***.gitignore*** 파일 생성
***.gitignore*** 파일안에 배제하고싶은 것을 형식에 맞추어 작성

[.gitignore 형식](https://dkswnkk.tistory.com/575)

---
## 프로젝트의 변경 사항들을 타임캡슐(버전)에 담기
`git status`로 변경사항 확인
> 추적하지 않는(untracked)파일 : Git의 관리에 들아간 적 없는 파일

|Code|기능|
|:--|:--|
|git add "파일명"|파일 하나 담기|
|git add .|모든 파일 담기|
> `git status`로 담긴것 확인

파일 변경 후

`git diff`로 변경내용 확인 가능

---
## 담은것 묻기
아래 명령어로 'commit'

`git commit`
* Vi 입력 모드로 진입(키보드만 이용)

|Code|기능|
|:--|:--|
|`i`|입력 시작|
|`ESC`|입력 종료|4
|`:q`|저장없이 종료(입력한 것 없을 시)|
|`:q!`|저장없이 강제종료|
|`:wq`|저장하고 종료|

커밋 메시지까지 함께 작성하기

`git commit -m "메세지"`

`git log` 로 확인

### Tip
`git commit -am "메세지"` 로 `git add` 없이 커밋 가능
> 단 새로 추가된(untracked)파일 없을 때 한정
---

## 과거로 돌아가기 
### reset
> 이력을 그 당시로 되돌리는 것, 돌아가려는 commit으로 repository가 재설정 됨 (해당 커밋 이후의 이력이 사라짐)

`git log` 를 통해 돌아갈 커밋의 해쉬 복사

`git reset "옵션" "커밋 해쉬"`

|옵션|기능|
|:--|:--|
|git reset --soft|원복된 이력 이후의 내용을 모두 유지|
|git reset --hard|원복된 이력 이후의 내용을 모두 삭제 후 초기화|
|git reset -merge|바로 이전 병합 취소|
|git reset --mixed|원복된 이력 이후의 내용을 모두 유지하지만 인덱스는 초기화 되므로 변경 내용을 다시 추가해야 함|

### revert
>이전 이력은 그대로 두고, 되돌릴 commit의 코드만 원복

>협업에는 revert를 사용

`git log` 를 통해 취소 할 커밋의 해쉬 복사

`git revert "커밋 해쉬"`

* 충돌이 일어나는 경우가 있어 수동으로 결정한 후 
`git revert --continue`가 필요할 수 있음

* `git revert --no-commit "커밋 해쉬"` 는 커밋을 하지 않음
    * `git reset --hard` 로 취소 가능
---
## Branch : 분기된 가지 (다른 차원)
* 프로젝트를 하나 이상의 모습으로 관리해야 할 때
    * 예) 실배포용, 테스트서버용, 새로운 시도용

* 여러 작업들이 각각 독립되어 진행될 때
    * 예) 신기능 1, 신기능 2, 코드개선, 긴급수정 ...
    * 각각의 차원에서 작업한 뒤 확정된 것을 메인 차원에서 통합

### 이 모든 것을 하나의 프로젝트 폴더에서 진행될 수 있도록 Branch를 만든다

---
## 여러 branch 만들기
|Code|기능|
|:--|:--|
|`git branch "브랜치명"`|"브랜치명"란 이름의 브랜치 생성|
|`git branch`|브랜치 목록 확인|
|`git switch "브랜치명"` |"브랜치명"브랜치로 이동|
|`git switch -c "브랜치명"`|"브랜치명"란 이름의 브랜치 만들고 이동|
|`git branch -d "브랜치명"`|"브랜치명"란 브랜치 삭제|
|`git branch -m "기존 브랜치명" "새 브랜치명"`|"기존 브랜치명"에서 "새 브랜치명"으로 브랜치명 변경|
|`git log --all --decorate --oneline --graph`|여러 브랜치의 내역을 편리하게 볼 수 있음|
---
## branch 합치기
### merge
>브랜치를 남겨두고 새 커밋을 생성, 따라서 `reset`으로 취소 가능

기준이 되는 브랜치로 이동

`git merge "합쳐질 브랜치명"`

### rebase
>브랜치 자체를 때어내어 붙임

옮길 브랜치로 이동

`git rebase "기준 브랜치"`
* "기준 브랜치"는 뒤쳐져 있는 상황
    * `merge`를 통해 기준을 맨 앞으로 이동
---
## branch 충돌 해결하기
>같은 위치에 다른 내용이 입력되어 있을 경우 충돌이 발생

### merge
사용자가 어떤 내용을 입력 할 것인지 선택

#### 당장 해결이 어려울 경우
`git merge --abort`로 중단

#### 해결 가능 시
충돌 부분 수정 뒤

`git add .`, `git commit`으로 병합 완료

### rebase
사용자가 어떤 내용을 입력 할 것인지 선택

#### 당장 해결이 어려울 경우
`git rebase --abort`로 중단

#### 해결 가능 시
충돌 부분 수정 뒤 `git add .`

`git rebase --continue`로 이어서 실행

모든 충돌이 해결 될 때까지 반복

---
## git stash
>작업중 다른 작업을 해야 할 때, 아직 마무리 하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령어/tracked, staged인 파일들 가능

|code|기능|
|:--|:--|
|`git stash`|스택에 새로운 stash 생성|
|`git stash list`|stash를 여러번 했을 경우 stash목록 확인|
|`git stash apply`|가장 최근의 stash를 가져온다|
|`git stash apply "stash 이름"`|"stash 이름"에 해당하는 stash를 가져온다|
|`git stash apply --index`|`--index`옵션을 통해 staged상태까지 불러온다|
|`git stash drop`|가장 최근의 stash를 제거한다|
|`git stash drop "stash 이름"`|"stash 이름"에 해당하는 stash를 제거한다|
|`git stash pop`|stash를 가져옴과 동시에 스택에서 제거한다|

`git stash show -p | git apply -R`

가장 최근의 stash를 사용하여 패치를 만들고 그것을 거꾸로 적용한다(stash 되돌리기)

`git stash show -p "stash 이름" | git apply -R`

"stash 이름"에 해당하는 stash를 이용하여 거꾸로 적용한다(stash 되돌리기)

---
## Checklist
형상관리 시스템은 왜 나오게 되었을까요?
> 개발 중 발생하는 산출물들이 변경됨으로써 변해가는 소프트웨어 형상을
체계적으로 관리가호 유지하기 위해서

git은 어떤 형상관리 시스템이고 어떤 특징을 가지고 있을까요? 분산형 형상관리 시스템이란 무엇일까요?
>git은 분산형 형상관리 시스템으로 빠른 속도와 오프라인 작업이 가능하다는 특징이 있다.
분산형 형상관리 시스템이란 개인이 작업한 이후 변경사항을 병합하는 형식의 시스템이다.

git은 어떻게 개발되게 되었을까요? git이 분산형 시스템을 채택한 이유는 무엇일까요?
> 비트키퍼의 자유이용이 제한되자 리누스 토르발스가 직접 버전 관리 시스템을 만들어야 겠다고 마음먹고 Git을 만들게 되었다.

git과 GitHub은 어떻게 다를까요?
> Git은 버전관리 프로그램이고, GitHub는 Git을 웹으로 이용 할 수 있게 만든 원격 저장소이다.

git의 clone/add/commit/push/pull/branch/stash 명령은 무엇이며 어떨 때 이용하나요? 그리고 어떻게 사용하나요?
>* clone : 저장소 복제
>* add : 파일을 스테이징
>* commit : 스테이징 된 파일을 히스토리에 기록
>* push : 로컬의 히스토리를 원격에 업로드
>* pull : 원격의 히스토리를 로컬에 가져오기
>* branch : 프로젝트를 하나 이상의 모습으로 관리하기 위해 다른 가지를 만듦
>* stash : 마무리 하지 않은 작업을 스택에 잠시 저장

git의 Object, Commit, Head, Branch, Tag는 어떤 개념일까요? git 시스템은 프로젝트의 히스토리를 어떻게 저장할까요?
>* git은 히스토리를 4개의 object로 관리한다.
>   * bold : git add할 때 생성된다. 파일 내용이 들어있다
>   * tree : git commit할 때 생성된다. 타입과 객체명, 파일명이 기록된다.
>   * commit : git commit할 때 생성된다. tree객체명, 부모commit객체명, author, committer, message를 기록한다.
>   * tag : git tag할 때 생성된다. commit 객체명, tag이름, tagger, message가 기록된다.
>* Commit : 
>* Head : 해당 브랜치의 마지막 커밋을 의미
>* Branch : 원래 코드에서 새로운 버전을 생성한 것
>* Tag : 커밋을 참조히기 쉽도록 이름을 붙이는 것, 한 번 붙인 태그는 브랜치처럼 위치가 이동하지 않고 고정된다.
>   * 일반 태그(Lightweight tag)
>       * 이름만 붙일 수 있다.
>   * 주석 태그(Annotated tag)
>       * 이름을 붙일 수 있다.
>       * 태그에 대한 설명 포함 가능
>       * 서명을 넣을 수 있다.
>       * 태그를 만든 사람의 이름, 이메일과 만든 날짜 정보도 포함 가능

리모트 git 저장소에 원하지 않는 파일이 올라갔을 때 이를 되돌리려면 어떻게 해야 할까요?
> git reset --hard <돌아갈 commit><br>
git push -f<br>
reset 사용하여 되돌아갈 commit으로 이동하여 강제로 원격 브랜치에 push

>git log --oneline //커밋기록 확인<br>
git revert <취소할 커밋> // 커밋을 취소<br>
git commit -m "revert message" <br>
push<br>
revert 사용하여 commit을 취소