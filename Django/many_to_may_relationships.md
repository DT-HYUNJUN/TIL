# Many To Many (M:N)

두 개의 테이블을 다대다 관계로 표현하기 위해서는 추가적인 중개 테이블이 필요하다.

# 중개 테이블

```python
class Doctor(models.Model):
  name = models.TextField()

class Patient(models.Model):
  # ManyToManyField 작성
  doctors = models.ManyToManyField(Doctor)
  name = models.TextField()
```

위 코드처럼 다대다 관계를 가질 테이블 중 아무데서나 모델을 설정해주면 된다.

```python
models.ManyToManyField(model)
```

그러면 DB에서는 아래와 같은 테이블이 생성된다.

|id|patient_id|doctor_id|
|---|---|---|
|1|1|1
2|2|1

기본적으로 pk와 각 테이블의 외래키로 구성되어있다.

## 중개 테이블 추가 필드

만약 중개테이블에 추가적인 필드를 작성하고 싶으면 `through`를 설정해준다.

```python
class Doctor(models.Model):
  name = models.TextField()

class Patient(models.Model):
  # through를 사용해 Reservation 테이블에 연결해준다.
  doctors = models.ManyToManyField(Doctor, through='Reservation')
  name = models.TextField()

class Reservation(models.Model):
  doctor = models.ForeignKey(Doctor, on_delete=models.CASCADE)
  patient = models.ForeignKey(Patient, on_delete=models.CASCADE)
  # 추가 필드 작성
  symptom = models.TextField()
  reserved_at = models.DateTimeField(auto_now_add=True)
```

## 역참조

다대다 관계가 여러개 있을 시, 역참조를 시행할 때 충돌이 발생할 수 있다. 이런경우에는 `related_name` 을 사용해 역참조 managet_name을 변경할 수 있다.

```python
class Doctor(models.Model):
  name = models.TextField()

class Patient(models.Model):
  # ManyToManyField - related_name 작성
  doctors = models.ManyToManyField(Doctor, related_name='patients')
  name = models.TextField()
```

이렇게 설정해주면 

```python
# 변경 전
doctor.patient_set.all()

# 변경 후
doctor.patients.all()
```

이런식으로 작성이 가능하다.