# Model

## Django Model
 
DJango의 디자인 패턴 MVT에서 M을 의미한다.

DB의 테이블을 정의하고 데이터를 조작하는 기능들을 제공한다.

테이블 구조를 설계하는 청사진이라고 봐도 된다.

## Model Class

Model 클래스를 작성하는 방법은 해당 App의 models.py 파일에 만들고 싶은 테이블을 파이썬 문법에 맞게 작성한다.

```python
from django.db import models

class Model(models.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
```

django.db.models 모듈의 Model 클래스를 상속받아서 작성한다.

[Django Model Document](https://docs.djangoproject.com/ko/4.1/topics/db/models/)에서도 확인할 수 있다.

개발자는 설계할 테이블 구조에 대한 코드만 작성해주면 된다.

```python
title = models.CharField(max_length=10)
# 필드이름 = models.데이터 타입(제약조건)
```

## Migrations

Model 클래스의 변경사항(필드 생성, 추가 수정 등)을 DB에 최종적으로 반영하는 방법이다.

models.py 파일에 테이블을 구성했으면, 테이블 설계도를 만들어준다

```bash
$ python manage.py makemigrations
```

그리고 만들어진 설계도를 DB에 전달하여 반영해준다.

```bash
$ python manage.py migrate
```

이후에는 db.sqlite3 파일을 통해 확인할 수 있다.

## Field 추가

테이블에 필드를 추가하고싶으면 위 과정을 반복하면 된다.

models.py 에 필드 추가 -> makemigrations -> default 설정 -> migrate

단, 기존에 존재하던 테이블에 필드를 추가하기 때문에 필드의 기본값이 필요하다.

makemigrations을 하면 default값 설정에 대한 안내문이 나오는데

```
1) 기본 값을 직접 입력
2) 현재 대화에서 나간 후 models.py에 기본값 설정
```

위 선택지 중에서 상황에 맞게 설정해준다.

## Admin

Django에서는 추가적인 설치나 설정 없이도 기본적인 관리자 기능을 제공해준다.

urls.py를 보면

```python
path('admin/', admin.site.urls),
```

위 경로가 있는것을 확인할 수 있다.

경로에도 알 수 있듯이 관리자 페이지를 말한다.

하지만 우리는 아직 super user를 생성하지 않았어서 로그인은 못한다.

### 계정 생성

```bash
$ python manage.py createsuperuser
```

위 명령어를 입력하면 username, email, password, password(확인용) 을 입력하는데

리눅스 sudo를 만들 때처럼

비밀번호를 입력해도 보안상 터미널에는 뜨지 않는다.

생성완료하면 db.sqlite3의 auth_user에 표시된다.

### Admin에 모델 등록

```python
from django.contrib import admin

# models.py 에서 생성한 Article 모델을 추가한다.
from .models import Article

admin.site.register(Article)
```

모델을 추가했지만 admin site에 등록을 하지 않아서 관리자페이지에는 나타나지 않는다.

모델 등록을 해야만 관리자페이지에서 접근할 수 있다.

기존에 models.py에서 생성한 Article을 관리자 페이지에 등록해준다.

이후에는 관리자 페이지에서 Article 모델을 확인할 수 있으며, CRUD도 테스트할 수 있게 된다.

# ORM

ORM (Object-Relational-Mapping)은 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템 간에 데이터를 변환하는 프로그래밍 기술을 말한다.

## QuerySet API

QuerySet API는 ORM에서 데이터를 검색, 필터링, 정렬 및 그룹화 하는데 사용하는 도구다.

쉽게 말해, API를 사용하여 SQL이 아닌 Python코드로 데이터를 처리한다.

## 라이브러리 설치

Django 환경 안에서 실행되는 python shell을 통해 QuerySet API를 입력하는데 필요한 라이브러리를 설치한다.

```bash
$ pip install ipython
$ pip install django-extensions
```

## ORM CREATE

데이터 객체를 만드는 방법에는 세 가지가 있다.

(models.py에는 Article() 클래스가 있다.)

### 첫 번째

Article 클래스로부터 article 인스턴스를 생성한 후 각 필드에 값을 할당한다.

```shell
>>> article = Article()
>>> article.title = 'title'
>>> article.content = 'content'
>>> article.save()
```

### 두 번째

article 인스턴스를 생성할 때, 값을 할당한다.

```shell
>>> article = Article(title='title', content='content')
>>> article.save()
```

### 세 번째

QuerySet API인 create() 메서드를 사용한다.

```shell
>>> Article.objects.create(title='title',content='content')
```

## ORM READ

READ에는 단일 데이터를 조회하는 방법과 여러 데이터를 조회하는 방법이 있다.

### 전체 데이터 조회

```shell
>>> Article.objects.all()
```

### 단일 데이터 조회

get() 메서드를 사용한다.

객체를 찾을 수 없으면 DoesNotExist 예외가 발생하고,

둘 이상의 객체를 찾으면 MultipleObjectsReturned 예외가 발생한다.

그렇기에 pk와 같이 고유성을 보장하는 조회에서 사용해야 한다.

```shell
>>> Article.objects.get(pk=1)
>>> Article.objects.get(title='title')
```

### 특정 데이터 조회

filter() 메서드를 사용한다.

해당 조건에 만족하는 데이터를 배열의 형태로 반환한다.

```shell
>>> Article.objects.filter(content='content')
>>> Article.objects.filter(title='a')
```

### Field lookups

특정 레코드를 조회할 때 조건을 설정하는 방법이다.

[Django QuerySet API ](https://docs.djangoproject.com/en/3.2/ref/models/querysets/#field-lookups)

## ORM Update

