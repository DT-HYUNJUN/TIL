# Django 개발 환경 설정 가이드

파이썬은 글로벌과 독립된 가상 환경을 제공한다.

동일한 PC 내에서 두 개의 다른 프로젝트를 진행하는데, 각각의 프로젝트의 필요 환경이 다를 수 있다. 만약 가상 환경이 없으면 이러한 개발 환경은 구축하기가 힘들다.

그렇기 때문에 독립된 가상 환경을 파이썬에서 제공해주기 때문에 프로젝트 개발 시 매우 유용하게 쓰인다.

## Django 프로젝트 생성 루틴

1. 가상환경 생성

2. 가상환경 활성화

3. django 설치

4. 의존성 파일 생성

5. .gitignore 파일 생성

6. git 저장소 생성

7. django 프로젝트 생성

8. 서버 실행

## 1. 가상환경 생성

> `$ python -m venv <venv>`

가상환경을 생성하기 위한 명령어다.

`venv` 모듈을 실행해주기 위해 -m 옵션을 사용한다.

`<>` 안에 생성 할 가상환경의 이름을 적어주는데, 보통은 `venv`를 사용한다.

명령어를 실행시키면 현재 디렉토리에 `venv` 폴더가 있을거다.

<br>

## 2. 가상환경 활성화

> `$ source <venv>/Scripts/activate`

위에서 가상환경을 생성했다면 이제는 활성화 차례다.

`source`는 쉘 명령어로, 스크립트 파일을 실행시켜준다. 또한 `.`으로 대체해서 사용할 수 있기 때문에 `<venv>/Scripts/activate`로 실행할 수 있다.

<br>

## 3. Django 설치

> `(venv) $ pip install django==3.2.18`

Django를 설치해주는데, `3.2.18`버전으로 install 한다.

이유는 `3.2`버전이 `LTS`이기 때문이다.

`LTS`는 `Long-Term Support`의 약자로 장기지원 버전을 의미한다.

<br>

## 4. 의존성 파일 생성

> `(venv) $ pip freeze > requirements.txt`

1번 글에서 기술했다시피 가상환경은 협업시에도 쓰인다. 사람마다 개발환경이 다르기 때문에 가상환경에서 통일된 버전을 유지하는게 핵심이다.

위 명령어를 실행하면 `requirements.txt`파일을 생성하는데, 파일 안에는 현재 가상환경의 패키지리스트와 버전이 있다.

그렇기에 패키지 설치시마다 진행한다.

<br>

## 5. .gitignore 파일 생성

> `(venv) $ touch .gitignore` 또는 GUI 이용


프로젝트를 Github에 올릴 때 필요 없는 파일이나 디렉토리까지 올릴 필요가 없기에 .gitignore를 사용해준다.

## 6. git 저장소 생성

> `(venv) $ git init`

위 명령어를 실행 후 `repository`에 `remote`해준다.

## 7. Django 프로젝트 생성

> `(venv) $ django-admin startproject <firstpjt> .`

`django-admin`명렁어는 Django 프레임워크에서 제공하는 명령어다. 새 프로젝트를 생성하거나, 애플리케이션, 데이터베이스 등을 관리하는 작업을 수행한다.

## 8. 서버 실행

> `(venv) $ python manage.py runserver`

프로젝트를 생성하고 바로 서버를 실행시켜주고 브라우저 주소창에

`localhost:8000`을 입력해주면 우주선이 우주선이 우리를 반겨준다.