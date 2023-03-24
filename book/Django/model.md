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