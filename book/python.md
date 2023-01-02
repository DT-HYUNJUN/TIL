# Python

## Python이란?
- Easy to learn
    - 다른 언어보다 문법이 간단하면서도 엄격하지 않음
    - 문법 표현이 간결하여 프로그래밍 경험이 없어도 부담없음
- Expressive Language
    - 같은 작업도 C나 Java보다 더 간결하게 작성 가능
- Interpreter
    - 소스코드를 기계어로 변환하는 컴파일 과정 없이 바로 실행 가능
    - 코드를 대화하듯 한줄 입력하고 실행한 후, 바로 확인할 수 있음
- Object Oriented Programming
    - 파이썬은 객체지향 언어며, 모든 것이 객체로 구현되어 있음

## 객체와 변수
Python은 모두 `객체`로 구성되어 있다.

### 변수
 - 변수란?
    - 컴퓨터 메모리에 어딘가에 저장되어 있는 객체를 참조하기 위해 사용되는 이름
    - 동일 이름에 다른 객체를 언제든 할당할 수 있기 때문에 '변수'라고 불림
 - 변수는 할당 연산자(=)를 통해 값을 할당(assignment)
 - type()
    - 변수에 할당된 값으 타입
 - id()
    - 변수에 할당된 값의 고유한 아이덴티티 값이며, 메모리주소

```python
x = 'hi'

type(x)
# str

id(x)
# 465387184
```

### 변수 할당
 - 같은 값을 동시에 할당할 수 있음
```python
x = y = 1004
```
 - 다른 값을 동시에 할당 할 수 있음
```python
x, y = 1, 2
```
### 식별자
 - 파이썬 객체를 식별하는 이름
 - 규칙
    - 식별자의 이름은 영문 알파벳, 언더스코어(_), 숫자로 구성
    - 첫 글자에 숫자 불가
    - 길이제한이 없고, 대소문자 구별
    - 키워드(keywords)는 예약어(reserved words)로 사용할 수 없음
    - 내장함수나 모듈 등의 이름으로도 만들면 안됨

## 자료형 (Data Type)

### 수치형 (Numeric Type)
 - int 정수
    - long은 없고 모두 int로 표기
    - 오버플로우가 발생하지 않음
 - float 실수
    - 정수가 아닌 모든 실수는 float
 - complex 복소수
    - 허수부를 j로 표현

### 불린형 (Boolean Type)
 - True / False 값을 가진 타입은 bool
 - 비교 / 논리 연산을 수행함에 있어서 활용

### 연산자 (Operator)
 - 사칙연산 및 수식 계산

| 연산자  | 내용  |
|----|---|
| + | 덧셈 |
| -  | 뺄셈 |
| *  | 곱셈 |
| %  | 나머지  |
| /  | 나눗셈  |
| // | 몫  |
| ** | 거듭제곱  |

- 복합 연산자

| 연산자  | 내용  |
|----|---|
| a += b | a = a + b |
| a -= b  | a = a - b |
| a *= b  | a = a * b |
| a /= b  | a = a / b  |
| a //= b  | a = a // b  |
| a %= b | a = a % b  |
| a **= b | a = a ** b  |

- 비교 연산자

| 연산자  | 내용  |
|----|---|
| <  | 미만  |
| <= | 이하  |
| >  | 초과  |
| >= | 이상  |
| == | 같음  |
| != | 같지않음  |

- 논리식을 판단하여 True와 False를 반환

| 연산자  | 내용  |
|----|---|
| A and B | A와 B 모두 True시, True|
| A or B | A와 B 모두 False시, False  |
| Not | True를 False로, False를, True로 |

- AND

| AND  | 내용  |
|----|---|
| True and True  | True  |
| True and False | False  |
| False and True  | False  |
| False and False  | False  |

- OR

| OR  | 내용  |
|----|---|
| True and True  | True  |
| True and False | True  |
| False and True  | True  |
| False and False  | False  |

- NOT

| NOT  | 내용  |
|----|---|
| not True  | False  |
| not False | True  |