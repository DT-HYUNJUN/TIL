## [README](../README.md) <img src="https://img.shields.io/badge/README-018EF5?style=flat&logo=README&logoColor=white" /><br>
## [Markdown](markdown.md) <img src="https://img.shields.io/badge/MARKDOWN-000000?style=flat&logo=Markdown&logoColor=white" />
## [Git](git.md) <img src="https://img.shields.io/badge/GIT-F05032?style=flat&logo=Git&logoColor=white" />
## [Decoration](decorate.md) 🎨
## [Career](book/career.md) 👨‍💻<br></br>

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

## 컨테이너

### 컨테이너 정의
 - 여러 개의 값을 담을 수 있는 것(객체)
 - 컨테이너 분류
    - 순서 O (Ordered) vs. 순서 X (Unordered)

### 컨테이너 뷴류
 - 시퀀스
    - 문자열 (immutable) : 문자들의 나열
    - 리스트 (mutable) : 변경 가능한 값들의 나열
    - 튜플 (immutable) : 변경 불가능한 값들의 나열
    - 레인지 (immutable) : 숫자의 나열
 - 컬렉션 / 비시퀀스
    - 세트 (mutable) : 유일한 값들의 모음
    - 딕셔너리 (mutable) : 키-값들의 모임

### 문자열
 - 모든 문자는 str 타입
 - 문자열은 ` `` `나 ` `` `` `를 활용하여 표기
 - 따옴표 안에 따옴표
 ```python
 print('hello')
 # hello

 print(type('hello'))
 # <class 'str'>
 ```

### 중첩따옴표
 - 따옴표 안에 따옴표
 ```python
 print('문자열 안에 "큰 따옴표" 사용')
 print("문자열 안에 '작은 따옴표' 사용")
 ```

### 인덱싱
 - 인덱스를 통해 특정 값에 접근할 수 있음

 - lst[1] => 'b'

|"| a | b | c | d | e | f | g | h | i | " |
|-|---|---|---|---|---|---|---|---|---|---|
|index|0|`1`|2|3|4|5|6|7|8| |

### 슬라이싱
 - lst[2:5] => 'ced'

|"| a | b | c | d | e | f | g | h | i | " |
|-|---|---|---|---|---|---|---|---|---|---|
|index| 0| 1| `2`| `3`| `4`| 5| 6| 7| 8| |
|index|-9|-8|-7|-6|-5|-4|-3|-2|-1| |

 - lst[2:5:2] => 'ce'

|"| a | b | c | d | e | f | g | h | i | " |
|-|---|---|---|---|---|---|---|---|---|---|
|index| 0| 1| `2`| 3| `4`| 5| 6| 7| 8| |
|index|-9|-8|-7|-6|-5|-4|-3|-2|-1| |

### 기타
 - 결합

   ```python
   'hello, ' + 'python!'
   # 'hello, python!'
   ```
 - 반복

   ```python
   'hi!' * 3
   # 'hi!''hi!''hi!'
   ```
 - 포함
   
   ```python
   'a' in 'apple'
   # True
   'app' in 'apple'
   # True
   'b' in 'apple'
   # False
   ```

### Escape sequence
 - 문자열 내에서 특정 문자나 조작을 위해서 역슬래시(\\)를 활용하여 구분

| 예약문자 | 내용 |
|----|---|
| \n | 줄 바꿈 |
| \t | 탭 |
| \r | 캐리지리턴 |
| \0 | 널(Null) |
| \\\ | \ |
| \' | 단일인용부호(') |
| \" | 이중인용부호(") |

```python
print('철수 \'안녕\'')
# 철수 '안녕'
print('이 다음은 엔터.\n그리고 탭\t탭')
# 이 다음은 엔터.
# 그리고 탭   탭
```

## 리스트
 - 변경 가능한 값들의 나열된 자료형
 - 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
 - 변경 가능하며(mutable), 반복 가능함(iterable)
 - 항상 대괄호 형태로 정의하며, 요소는 콤마로 구분

### 생성과 접근
 - 리스트는 대괄호 [] 혹은 list()를 통해 생성
 - 순서가 있는 시퀀스로 인덱스를 통해 접근 가능
   - 값에 대한 접근은 lst[i]

|| 객체 1 | 객체 2 | 객체 3 | 객체 4 | 객체 5 | 객체 6 | 객체 7 |
|-|---|---|---|---|---|---|---|
|Positive index| 0| 1| 2| 3| 4| 5| 6|
|Negative index|-7|-6|-5|-4|-3|-2|-1|

### 리스트 생성
```python
my_list = []
another_list = list()
type(my_list)
# <class 'list'>
type(another_list)
# <class 'list'>
```

### 리스트 접근과 변경
```python
# 값 접근
a = [1, 2, 3]
print(a[0])
# 1

# 값 변경
a[0] = '1'
print(a)
# ['1', 2, 3]
```

### 리스트 값 추가/삭제
- 값 추가는 .append()를 활용하여 추가하고자 하는 값을 전달

```python
even_numbers = [2, 4, 6, 8]
even_numbers.append(10)
even_numbers
# => [2, 4, 6, 8, 10]
```

- 값 삭제는 .pop()을 활용하여 삭제하고자 하는 인덱스를 전달

```python
even_numbers = [2, 4, 6, 8]
even_numbers.pop(0)
even_numbers
# => [4, 6, 8]
```

###  None
 - 파이썬 자료형 중 하나
 - 파이썬에서는 값이 없음을 표현하기 위해 None 타입이 존재함.
 - 일반적으로 반한 값이 없는 함수에서 사용하기도 함.

 ```python
 print(type(None))
 # <class 'NoneType'>
 a = None
 print(a)
 # None
 ```

 ## String Formatting

 ### String Interpolation
 - 문자열을 변수를 활용하여 만드는 법
   - f-string
```python
name = 'Kim'
score = 4.5
print(f'Hello, {name}! 성적은 {scroe}')
# Hello, Kim! 성적은 4.5
```

## Typecasting

### 자료형 변환
- Python에서 데이터 형태는 서로 변환할 수 있음
   - 암시적 (Implicit)
      - 사용자가 의도하지 않고, Python 내부적으로 자료형을 변환 하는 경우
   - 명시적 (Explicit)
      - 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환 하는 경우

### 암시적 (Implicit)
- 사용자가 의도하지 않고, Python 내부적으로 자료형을 변환 하는 경우
   - bool
   - Numeric type (int, float, complex)
```python
True + 3
# 4
3 + 5.0
# 8.0
3 + 4j +5
# (8+4j)
```

### 명시적 (Explicit)
- int
   - str*, float => int
- float
   - str*, int => float
- str
   - int, float, list, tuple, dict => str

## 제어문
- Python은 기본적으로 위에서부터 아래로 순차적으로 명령을 수행
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요
- 순서도(flow chart)로 표현이 가능

### 조건문
- 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용
- expression에는 참/거짓에 대한 조건식
```python
if <expression>:
   # Run this Code block
else:
   # Run this Code block
```

### 복수 조건문
```python
if <expression>:
   # Code block
elif <expression>:
   # Code block
elif <expression>:
   # Code block
else:
   # Code block
```

### 중첩 조건문
- 조건문은 다른 조건문에 중첩되어 사용될 수 있음
```python
if <expression>:
   # Code block
   if <expression>:
      # Code block
else:
   # Code block
```

## Range

### range(n=0, m s=1)
- 숫자의 시퀀스를 나타내기 위해 사용
   - 기본형: range(n)
      - 0부터 n-1까지 증가
   - 범위 지정: range(n, m)
      - n부터 m-1까지 증가
   범위 및 스텝 지정: range(n, m, s)
      - n부터 m-1까지 s만큼 증가
```python
range(4)
#0 1 2 3
range(1, 4)
# 1 2 3
range(2, 8, 2)
# 2 4 6
```

## 반복문
- 특정 조건을 도달할 때까지, 계속 반복

### 반복문 종류
- while 문
   - 종료조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
- for 문
   - 반복가능한 객체를 모두 순회하면 종료
- 반복 제어
   - break, continue, for-else

### while 문
- 조건이 참인 경우 코드블록이 실행됨
- 무한 루프를 하지 않도록 종료조건이 반드시 필요
```python
while <expression>:
   # Code block
```

### for 문
- 처음부터 끝까지 모두 순회하므로 별도의 종료조건이 필요하지 않음
- 순회 가능한 객체: 컨테이너형
```python
for <변수명> in <iterable>:
   # Code block
```

### 반복문 제어
- break
   - 반복문 종료
- continue
   - continue 이후 코드는 수행하지 않고, 다음 반복을 수행
- for-else
   - 끝까지 반복문을 실행한 이후에 else문 실행
      - break를 통해 중간에 종료되는 경우 else문은 실행되지 않음
```python
# break
n = 0
while True:
   if n == 3:
      break
   print(n)
   n += 1
# 0 1 2
```
```python
# continue
for i in r range(6):
   if i % 2 == 0:
      continue
   print(i)
# 1 3 5
```
```python
# for-else
for char in 'apple':
   if char == 'b':
      print('b!')
      break
else:
   print('b가 없습니다.')
# b가 없습니다.
```