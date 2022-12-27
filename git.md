# Git

## git이란?
git은 분산버전관리시스템으로 코드의 버전을 관리하는 도구

## 기본 명령어 - init
- 특정 폴더를 git 저장소를 만들어 git으로 관리
    - .git 폴더가 생성
    - git bash에서는 (master)라는 표기를 확인

## 기본흐름
1. 작업을 하고
2. 변경된 파일을 모아 (add)
3. 버전으로 남긴다 (commit)

## 기본 명령어 - add
```
$ git add <file>
```
- working directory상의 변경 내용을 staging area에 추가하기 위함
    - untracked / modified 상태의 파일을 staged로 변경

## 기본 명령어 - commit
```
$ git commit -m '<커밋메시지>'
```
- staged 상태의 파일들을 커밋을 통해 버전으로 기록
- 커밋 메시지는 변경 사항을 나타낼 수 있도록 명확하게 작성해야 함
- 변경된 부분만 저장하기에 매우 크기가 작음