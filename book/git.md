## [go to README](../README.md) <img src="https://img.shields.io/badge/README-018EF5?style=flat&logo=README&logoColor=white" /><br>
## [go to Markdown](markdown.md) <img src="https://img.shields.io/badge/Markdown-000000?style=flat&logo=Markdown&logoColor=white" />
## [go to Decoration](decorate.md) 🎨
# Git                      

## `git이란?`
git은 분산버전관리시스템으로 코드의 버전을 관리하는 도구

---

## `기본 명령어 - init`
- 특정 폴더를 git 저장소를 만들어 git으로 관리
    - .git 폴더가 생성
    - git bash에서는 (master)라는 표기를 확인
---

## `기본흐름`
1. 작업을 하고
2. 변경된 파일을 모아 (add)
3. 버전으로 남긴다 (commit)

- Git 파일은 modified, staged, committed로 관리
    - modified : 파일이 수정된 상태 (add 명령어를 통하여 staging area로) `1통`
    - staged: 수정한 파일을 곧 커밋할 것이라고 표시한 상태 (commit 명령어로 저장소) `2통`
    - committed : 커밋이 된 상태 `3통`
---

## `기본 명령어 - add`
```
$ git add <file>
```
- working directory상의 변경 내용을 staging area에 추가하기 위함
    - untracked / modified 상태의 파일을 staged로 변경
---

## `기본 명령어 - commit`
```
$ git commit -m '<커밋메시지>'
```
- staged 상태의 파일들을 커밋을 통해 버전으로 기록
- 커밋 메시지는 변경 사항을 나타낼 수 있도록 명확하게 작성해야 함
- 변경된 부분만 저장하기에 매우 크기가 작음
---

## `기본 명령어 - log`
```
$ git log
```
- 현재 저장소에 기록된 커밋을 조회
- 다양한 옵션을 통해 로그를 조회할 수 있음
```
$ git log -1                # 로그를 하나만 출력
$ git log --oneline         # 로그를 한 줄에 출력
$ git log -1 --oneline      # 하나의 로그를 한 줄에 출력
```
---

## `기본 명령어 - status`
```
$ git status
```
- Git 저장소에 있는 파일의 상태를 확인하기 위하여 활용
    - 파일의 상태를 알 수 있음
        - Untracked files
        - Changed not staged for commit
        - Changes to be committed
    - Nothing to commit, working tree clean
---

## `원격 저장소 - 설정`
```bash
$ git remote add origin URL
```
- URL을 origin이란 이름으로 대신

```bash
$ git remote -v
```
- 단축이름과 URL을 확인 가능
---
## `원격 저장소 - push / pull`
```bash
$ git push origin master
$ git pull origin master
```
- 원격 저장소로 변경 사항(commit)을 올림(push)
    - 원격 저장소는 로컬의 파일/폴더가 아닌 **버전(commit)** 을 관리
---

## `원격 저장소 - clone`
```bash
$ git clone <원격저장소주소>
```
- 원격 저장소를 복제하여 가져옴
    - clone : 원격 저장소 복제
    - pull : 원격 저장소 커밋 가져오기
---

## `Push 실패`
- 협업을 하다보면 아래의 메시지를 확인하게됨
<br>

![push_conflict](image/push_conflict.jpg)
- 이는 로컬과 원격 저장소의 커밋 이력이 다른 경우<br>

해결법<br>
1. 원격 저장소의 커밋을 로컬 저장소로 가져옴(pull)
2. 로컬에서 두 커밋을 병합(추가 커밋 발생)
    - <span style="color:#FF4848">동시에 같은 파일이 수정된 경우 merge conflict가 발생</span>
3. 다시 GitHub으로 push
---

## `gitignore`
- 프로젝트에서 버전 관리를 별도로 하지 않는 파일/폴더가 발생
- Git 저장소에 .gitignore 파일을 생성하고 해당 내용을 관리
- 작성 예시
    - 특정 파일 : a.txt
    - 특정 폴더 : /secret
    - 특정 확장자 : *.jpg
    - 예외 처리 : !b.exe
- <span style="color:#FF4848">주의! 이미 커밋된 파일은 반드시 삭제를 하여야 .gitignore로 적용</span>
## <div align=center>어떤 파일을 관리?</div>

- [개발 언어](https://github.com/github/gitignore)
    - 예시) 파이썬: venv/, 자바스크립트: node_modules/
- 개발 환경
    - 운영체제 (windows, mac, linux)
    - 텍스트 에디터 / IDE (visual studio code 등)
- [gitignore.io](https://gitignore.io) - .gitignore 파일 만든는 사이트
