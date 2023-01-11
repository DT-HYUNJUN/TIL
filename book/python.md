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

# 함수

## 함수 기초

### 함수의 정의
- 함수(Function)
   - 특정한 기능을 하는 코드의 조각(묶음)
   - 특정 명령을 수행하는 코드를 매번 다시 작성하지 않고, 필요 시에만 호출하여 간편히 사용
- 사용자 함수(Custom Function)
   - 구현되어 있는 함수가 없는 경우, 직접 작성
   ```python
   def function_name
      # Code block
      return returning_value
   ```
- 내장함수(Built-in Function)
   ```python
   import math
   values = []
   mean = sum(values) / len(values)
   ```
### 함수 기본 구조
```python
def function_name(param):
   # Code block
   return returning_value
```
INPUT x(param) -> Scope{function body} -> OUTPUT f(x)

## 내장 함수

### print
```python
print(*objects, sep=' ', end='\n', file=None)
```
- **objects* : 여러 객체 input 가능
- *sep=' '* : 객체를 ' '로 구분
- *end='\n'* : 뒤에 '\n'를 붙임
- *file=None* : None 타입

### 자주 사용하는 함수
- len(s)
   - 객체의 `길이`를 반환. 인자는 시퀀스 또는 컬렉션
- sum(iterable, start=0)
   - start및 iterable의 항목들을 왼쪽에서 오른쪽으로 합하고 `합계`를 반환
   - iterable 항목은 숫자
- max(iterable)
   - iterable에서 `최댓값`을 반환
   - 여러 항목이 최댓값이면 처음 만난 항목을 반환
- min(iterable)
   - iterable에서 `최솟값`을 반환
   - 여러 항목이 최솟값이면 처음 만난 항목을 반환
### 수학 관련 함수
- abs(x)
   - 숫자의 `절댓값` 반환
- divmod(a, b)
   - 두 수를 받아 `몫과 나머지` 반환
- pow(base, exp, mod=None)
   - base의 exp `거듭제곱` 반환
   - mod가 있는 경우 해당 값의 나머지 반환
- round(number, ndigit=None)
   - number를 소수점 다음에 ndigits 정밀도로 `반올림`한 값을 반환
   - ndigits 가 생략되거나 None이면, 입력에 가장 가까운 정수 반환
### 논리 관련 함수
- all(iterable)
   - iterable의 모든 요소가 `참이면`(또는 비어 있으면) `True` 반환
- any(iterable)
   - iterable의 요소중 `어느 하나라도 참이면` `True` 반환
   - iterable이 `비어 있으면` `False` 반환
### 진법 관련 함수
- bin(x)
   - 정수를 '0b' 접두사가 붙은 `2진수` 문자열로 반환
- hex(x)
   - 정수를 '0x 접두사가 붙은 `16진수` 문자열로 반환
- oct(x)
   - 정수를 '0o' 접두사가 붙은 `8진수` 문자열로 반환
### 유니코드 관련 함수
- ord(c)
   - `유니코드 문자 c`에 대응되는 `유니코드 숫자` 반환
- chr(i)
   - `유니코드 정수 i`에 대응되는 `문자`를 반환
### map
- map(function, iterable)
   - 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)적용하고, 그 결과를 map object로 반환
```python
numbers = [1, 2, 3]
result = map(str, numbers)
print(result, type(result))
# <map object at 0x10e2ca100> <class 'map'>

list(result)
# ['1', '2', '3']
```

- 알고리즘 문제 풀이시 input 값들을 숫자로 바로 활용하고 싶을 때
```python
n, m = map(int, input().split())
# 3 5

print(n, m)
print(type(n), type(m))
# 3 5
# <class 'int'> <class 'int'>
```

# 컬렉션

## 딕셔너리
- 키(key) : 값(value) 쌍으로 이뤄진 모음(collection)
   - 키(key) - 불변 자료형
   - 값(value) - 형태 무관
- 키와 값은 `:` 로 구분 / 개별 요소는 `,`로 구분
- 변경 가능하며(mutable), 반복 가능함(iterable)

### 딕셔너리 생성
- key는 변경 불가능한 데이터만 활용 가능
   - string, integer, float, boolean, tuple, range
- value는 모든 값으로 설정 가능
```python
Dict = {[1, 2, 3]: 'hi'}
# TypeError: unhashable type: 'list'
```

### 딕셔너리 접근
```python
student = {
   'name': '홍길동'
   'age': 25
}

student['name']
# 홍길동
```

### 딕셔너리 key, valye 추가 및 변경
- 딕셔너리에 키와 값의 쌍을 추가할 수 있음
- 이미 해당하는 키가 있다면 기존 값이 변경됨
```python
students = {'홍길동': 100, '김철수': 90}
students['홍길동'] = 80
# {'홍길동': 80, '김철수': 90}
students['박영희'] = 95
# {'홍길동': 80, '김철수': 90, '박영희': 95}
```

### 딕셔너리 key, value 삭제
- 키를 삭제하고자 하면 .pop()으로 키를 전달
```python
students = {'홍길동': 100, '김철수': 90}
students.pop('홍길동')
# {'김철수': 90}
```

- 키가 없는 경우 KeyError 발생
```python
students = {'홍길동': 100, '김철수': 90}
students.pop('Jane')
# KeyError: 'Jane'
```

### 딕셔너리 순회
- 딕셔너리는 기본적으로 key를 순회, key를 통해 값을 활용
```python
grades = {'John': 80, 'Eric': 90}
for name in grades:
   print(name)
"""
John
Eric
"""

grades = {'John': 80, 'Eric': 90}
for name in grades:
   print(name, grades[name])
"""
John 80
Eric 90
"""
```

- 추가 메서드를 활용하여 순회할 수 있음
   - keys() : Key로 구성된 결과
   - values() : value로 구성된 결과
   - items() : (key, value)의 튜플로 구성된 결과
```python
grades = {'John': 80, 'Eric': 90}
print(grades.keys())
print(grades.values())
print(grades.items())
"""
dict_keys(['John', 'Eric'])
dict_values([80, 90])
dict_items([('John', 80), ('Eric', 90)])
"""

grades = {'John': 80, 'Eric': 90}
for name, score in grades.items():
   print(name, score)
"""
(John, 80)
(Eric, 90)
"""
```

# 모듈
### module : 다양한 기능을 하나의 파일로
### package : 다양한 파일을 하나의 폴더로
### library : 다양한 패키지를 하나의 묶음으로
### pip : 이 것을 관리하는 관리자

## 모듈과 패키지
- 모듈
   - 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성
- 패키지
   - 특정 기능과 관련된 여러 모듈의 집합

## Python 표쥰 라이브러리
- Python에 기본적으로 설치된 모듈과 내장 함수

### radnom
- ramdom.randint(a, b)
   - a <= N <= b 임의의 정수 N을 반환
- random.choice(seq)
   - 비어 있지 않은 시퀀스에서 임의의 요소를 반환
   - 비어있으면 IndexError
- random.shuffle(seq)
   - 시퀀스를 제자리에서 섞음
- random.sample(population, k)
   - 무작위 비복원 추출한 결과인 k 길이의 리스트를 반환

### datetime
- datetime.date.today()
   - 현재 지역 날짜를 반환
- datetime.datetime.today()
   - 현재 지역 datetime을 반환
   - now()를 활용하면 타임존을 설정할 수 있음

### os
- os.listdir(path='.')
   - path에 의해 주어진 디렉토리에 있는 항목들의 이름을 담고 있는 리스트 반환
   - 리스트는 임의의 순서로 나열되며, 특수 항목은 포함하지 않음
- os.mkdir(path)
   - path라는 디렉토리를 생성
- os.chdir(path)
   - path를 변경

## Python 패키지

### pip
- PyPI에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템

### pip 명령어
- 패키지 설치
   - pip install
- 패키지 삭제
   - pip uninstall
- 패키지 목록 및 특정 패키지 정보
   - pip list
   - pip show SomePackage

### 모듈과 패키지  활용
```python
import module
from module import var, function, Class
from module import *

from package import module
from package.module import var, function, Class
```

# 에러/예외 처리
조건/반복, 함수 등 값이 변경되는 시점에서 주로 에러가 발생

## 에러와 예외

### 문법 에러 (Syntax Error)
- Syntax Error가 발생하면, Python 프로그램은 실행이 되지 않음

- EOL (End of Line)
```python
print('hello
# SyntaxError: EOL
```

- EOF (End of File)
```python
print(
# SyntaxError: EOF
```

- Invalid syntax
```python
while
# SyntaxError: invalid syntax
```

- assign to literal
```python
5 = 3
# SyntaxError: cannot assign to literal
```

### 예외 (Exception)
- 실행 도중 예상치 못한 상황을 맞이하면, 프로그램 실행을 멈춤
- 사용자 정의 예외를 만들어 관리할 수 있음

- ZeroDivisionError
```python
10/0
# ZeroDivisionError: division by zero
```

- NameError
```python
print(name_error)
# NameError: name 'name_error' is not defined
```

- ModuleNotFoundError
```python
import nonamed
# ModuleNotFoundError: No module named 'nonamed'
```

- ImportError
```python
from random import samp
# ImportError: cannot import name 'samp' from 'random'
```

## 예외 처리
- try / except 을 이용하여 예외 처리 가능
- try 문
   - 오류가 발생할 가능성이 있는 코드를 실행
   - 예외가 발생되지 않으면, except 없이 실행 종료
- except 문
   - 예외가 발생하면, except 절이 실행
   - 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취함
```python
try:
   num = input('숫자 입력 > ')
   print(int(num))
except:
   print('숫자가 아닙니다')
# ModuleNotFoundError: No module named 'nonamed'
```
# 파일 입출력

## 파일 입출력 활용

### 파일 입력
- open(file, mode='r', encoding=None)
   - file : 파일명
   - mode : 텍스트 모드
   - encoding : 인코딩 방식 (UTF8)

### 파일 활용
- 파일 객체 활용
```python
f = open('workfile', 'w')
```
- with 키워드 활용
```python
with open('workfile') as f:
   read_data = f.read()
```
- with 키워드를 사용 하면, f.close()를 호출하지 않아도 오류가 발생하지 않음.

### JSON
- JSON은 자바스크립트 객체 표기법으로 개발환경에서 많이 활용되는 데이터 양식으로 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용
- 문자 기반(텍스트) 데이터 포멧으로 다수의 프로그래밍 환경에서 쉽게 활용 가능
   - 텍스트를 언어별 데이터 타입으로 변환
   - 언어별 데이터 타입을 텍스트로 변환

### JSON 활용
- 객체(리스트, 딕셔너리 등)를 JSON으로 변환
```python
import json
x = [1, 'simple', 'list']
json.dumps(x)
# '[1, 'simple', 'list']'
```

- JSON을 객체(리스트, 딕셔너리 등)로 변환
```python
x = json.load(f)
```

### pprint
- 임의의 파이썬 데이터 구조를 예쁘게 인쇄 할 수 있는 기능을 제공

# Tuple

### 튜플의 정의
- 불변한 값들의 나열
- 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
- 변경 불가(immutable), 반복 가능함(iterable)
- 항상 소괄호 형태로 정의하며, 요소는 콤마로 구분

### 생성과 접근
- 소괄호() 혹은 tuple()을 통해 생성
- 값에 대한 접근은 리스트와 동일하게 인덱스로 접근
   - 값 변경은 불가능하여 추가/삭제도 불가능함
```python
a = (1, 2, 3, 1)
a[1]
# 2

a[1] = '3'
# 값 변경은 불가능
```

# Set

### 세트의 정의
- 유일한 값들의 모음(Collection)
- 순서가 없고 중복된 값이 없음
   - 수학에서의 집합과 동일한 구조를 가지며, 집합 연산도 가능
- 변경 가능(mutable), 반복 가능함(iterable)
   - 단,  세트는 순서가 없어 반복의 결과가 정의한  순서와 다를 수 있음

### 세트의 생성
- 중괄호 {} 혹은 set()를 통해 생성
   - 빈 Set를 만들기 위해서는 set()을 반드시 활용해야 함
- 순서가 없어 별도의 값에 접근할 수 없음
```python
{1, 2, 3, 1, 2}
# {1, 2, 3}

blank_set = set()
{'hi', 1, 2}
# {1, 2, 'hi'}

{1, 2, 3}[0]
# 순서가 없어 인덱스 접근 불가
```

### 세트 추가/삭제
- 추가는 .add()로 전달
- 삭제는 .remove()로 전달
```python
numbers = {1, 2, 3}
numbers.add(5)
# {1, 2, 3, 5}

numbers.add(1)
# {1, 2, 3, 5}
```

```python
numbers = {1, 2, 3}
numbers.remove(1)
# {2, 3}
```

# 메서드

## 문자열 메서드

### 문자열 탐색
- .find(x)
   - x의 첫 번째 위치를 반환. 없으면 -1 반환
```python
print('apple'.find('p'))
# 1
print('apple'.find('k'))
# -1
```

- .index(x)
   - x의 첫 번째 위치를 반환. 없으면 오류 발생
```python
print('apple'.index('p'))
# 1
'apple'.index('k')
# 에러
```

### 문자열 변경
- .replace(old, new[,count])
   - 바꿀 대상 글자를 새로운 글자로 바꿔서 변환
   - count를 지정하면, 해당 개수만큼만 시행
```python
print('coone'.replace('o', 'a'))
# caane
print('wooowoo'.replace('o', '!', 2))
# w!!owoo
```

- .strip([chars])
   - 특정한 문자들을 지정하면
   - 양쪽을 제거(strip), 왼쪽을 제거(lstrip), 오른쪽 제거(rstrip)
   - 문자열을 지정하지 않으면 공백을 제거
```python
print('     와우!\n'.strip())
# '와우!'
print('     와우!\n'.lstrip())
# '와우!\n'
print('     와우!\n'.rstrip())
#'    와우!'
print('안녕하세요????'.rstrip('?')))
# 안녕하세요
```

## List

### 리스트의 정의
- 변경 가능한 값들의 나열된 자료형
- 순서를 가지며, 서로 다른 타입의 요소를 가질 수 있음
- 변경 가능하며(mutable), 반복 가능함(iterable)
- 항상 대괄호 형태로 정의하며, 요소는 콤마로 구분

### 값 추가/삭제
- .append(x)
   - 리스트에 값을 추가함
```python
num = [1, 2, 3]
num.append(4)
print(num)
# [1, 2, 3, 4]
```
- .extend(iterable)
   - 리스트에 iterable의 항목을 추가함
```python
num = [1, 2, 3]
num.extend([4, 5])
print(num)
# [1, 2, 3, 4, 5]
```

- .insert(i, x)
   - 정해진 위치 i에 값을 추가함
```python
num = [1, 2]
num.insert(0, 0)
print(num)
# [0, 1, 2]

num.insert(1000, 4)
print(num)
# [0, 1, 2, 4]
```

- .remove(x)
   - 리스트에서 값이 x인 것 삭제
```python
num = [1, 2, 3, 'hi']
print.remove('hi')
print(num)
# [1, 2, 3]
```

- .pop(i)
   - 인덱스 i에 있는 값을 삭제, 그 항목을 반환
   - i가 없으면 마지막 항목을 삭제, 반환
```python
num = ['hi', 1, 2, 3]
pop_number = num.pop()
print(pop_number)
# 3
print(num)
# ['hi', 1, 2]
```
- .clear()
   - 모든 항목을 삭제함
```python
num = [1, 2, 3]
print(num.clear())
# []
```

### 탐색 및 정렬
- .index(x)
   - x값을 찾아 해당 index 값을 반환
```python
num = [1, 2, 3]
print(num.index(3))
# 2
```

- .count(x)
   - 원하는 값의 개수를 반환함
```python
num = [1, 2, 3, 1, 1,]
print(num.count(1))
# 3
```

- .sort()
   - 원본 리스트를 정렬함. None 반환
   - sorted()는 정렬된 리스트를 반환
```python
num = [3, 2, 5, 1]
num.sort()
# [1, 2, 3, 5]
```

- .reverse()
   - 순서를 반대로 뒤집음 (정렬 X).
```python
num = [3, 2, 5, 1]
result = num.reverse()
print(num)
# [1, 5, 2, 3]
```

## Set
- 유일한 값들의 모음(Collection)
- 순서가 없고 중복된 값이 없음
- 변경 가능(mutable), 반복 가능(iterable)

## Dictionary
- 키 - 값 쌍으로 이뤄진 모음(Collection)
   - key : 불변 자료형만 가능
   - value : 어떠한 형태든 무관
- 변경 가능(mutable), 반복 가능(iterable)

### 조회
- .get(key[,default])
   - key를 통해 value를 가져옴
   - keyError가 발생하지 않음
   - default값을 변경하면 해당 key가 없을시 default값을 반환
```python
dic = {'apple': '사과', 'banana': '바나나'}
print(dic.get('apple'))
# 사과
print(dic.get('pineapple', 0))
# 0
```

### 추가/삭제
- .pop(key[,default])
   - key가 딕셔너리에 있으면 제거 후 반환
```python
dic = {'apple': '사과', 'banana': '바나나'}
data = dic.pop('apple')
# 사과
data = dic.pop('pineapple', 0)
# 0
```

- .update([other])
   - 값을 제공하는 key, value로 덮어쓴다.
```python
dic = {'apple': '사', 'banana': '바나나'}
dic.update(apple='사과')
print(dic)
# {'apple': '사과', 'banana': '바나나'}
```

# 사용자 정의 함수

## 함수 기초

### 선언과 호출
- def 키워드로 함수 선언
- 들여쓰기를 통해 Function body를 작성
- parameter를 념겨줄 수 있음
- 동작 후에 return을 통해 결과값을 전달함

## Output
- 함수는 반드시 값을 하나만 return
   - return이 두 개 이상일 경우 첫 번째 return을 반환
   - 명시적인 return이 없으면 None 반환
- return과 동시에 실행이 종료

## Input
- parameter : 함수를 실행할 때, 함수 내부에서 사용되는 식별자
- argument : 함수를 호출 할 때, 넣어주는 값

### argument
- 함수 호출 시 함수의 parameter를 통해 전달되는 값
   - 필수 argument : 반드시 전달되어야 하는 값
   - 선택 argument : 값을 전달하지 않아도 되는 경우는 default 값 전달

### keyword argument
- 직접 변수의 이름으로 특정 argument를 전달할 수 있음
- keyword argument 다음에 positional argument를  활용할 수 없음
```python
def add(x, y):
   return x+y
```

### default argument
- 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함
```python
def add(x, y=0):
   return x+y
```

### 정해지지 않은 개수의 arguments
- 여러 개의 positional argument를 하나의 필수 parameter로 받아서 사용
- argument들은 튜플로 묶여 처리되며, parameter에 * 를 붙여 표현
```python
def add(*args):
   return sum(args)
```

### 정해지지 않은 개수의 keyword arguments
- 임의의 개수 argument를 keyword argument로 호출될 수 있도록 지정
- argument들은 dictionary로 묶여 처리되며, parameter에 ** 를 붙여 표현
```python
def family(**kwargs):
   for key, value in kwargs:
      print(key, : value)
```

## 함수의 범위

### scope
- 함수는 코드 내부에 local scope를 생성하며 그 외의 공간인 glbal scope로 구분
- scope
   - global scope : 코드 어디에서든 참조할 수 있는 공간
   - local scope : 함수가 만든 scope. 함수 내부에서만 참조 가능
- variable
   - global variable : global scope에 정의된 변수
   - local variable : local scope에 정의된 변수

### 객체 lifecycle
- 객체는 각자의 lifecycle 존재
   - built-in scope : Python이 실행된 이후부터 영원히 유지
   - global scope : 모듈이 호출된 시점 이후 혹은 interpreter가 끝날 때까지 유지
   - local scope : 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

### 이름 검색 규칙
- Python에서  사용되는 식별자들은 namespace에 저장되어 있음
- 아래와 같은 순서로 이름을 찾아가며, LEGB Rule이라고 부름
   - Local scope : 함수
   - Enclosed scope : 특정 함수의 상위 함수
   - Global scope : 함수 밖의 변수, Import 모듈
   - Built-in scope : Python 안에 내장되어 있는 함수 또는 속성
- 즉, 함수 내에서는 바깥 scope의 변수에 접근 가능하나 수정불가

### global 문
- 현재 코드 블록 전체에 적용되며, 나열된 식별자가 global variable임을 나타냄
   - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음
   - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않음

# 사용자 정의 클래스

## 객체 지향 프로그래밍

### 객체 지향 vs 절차 지향
- 절차 지향
```python
def area(x, y):
   return x * y

a = 10
b = 30
square_are = area(a, b)
# 300
```

- 객체 지향
```python
class Rectangle:
   def __init__(self, x, y):
      self.x = x
      self.y = y
   
   def area(self):
      return self.x * self.y

rec = Rectangle(10, 30)
rec.area()
# 300
```
- Rectangle - `클래스(class)`
- rec - `인스턴스(instance)`
- 사각형 정보 - `속성(attribute)`
   - 가로, 세로 길이
- 사각형의 기능 - `메소드(method)`
   - 넓이 구하기

### 객체지향의 장점 (Wikipedia)
- 객체지향은 **프로그램을 유연하고 변경이 용이**하게 만들고 대규모 SW개발에 많이 사용됨
- **SW개발과 보수를 간편하게** 하며, **직관적인 코드 분석**을 가능케 함

## 클래스와 인스턴스

### 기본 문법
- 객체의 틀(class)을 가지고, 객체(instance)를 생성한다.
- 클래스 : 객체들의 분류
- 인스턴스 : 하나하나의 실체
- 속성 : 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미
- 메소드 : 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)

### 객체 비교
- ==
   - equal
   - 변수가 참조하는 객체 내용이 같은 경우 True
- is
   - identical
   - 두 변수가 동일한 객체를 가리키는 경우 True

## 인스턴스
### 인스턴스 변수
- 인스턴스가 개인적으로 가지는 속성
- 각 인스턴스들의 고유 변수
- 생성자 메소드에서 self.\<name>으로 정의
- 인스턴스가 생성된 이후 \<instance>.\<name>으로 접근 및 할당

### 인스턴스 메소드
- 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메소드
- 클래스 내부에 정의
- 호출 시, 첫 인자로 self 전달

### 생성자(constructor) 메소드
- 인스턴스 객체가 생성될 때 자동으로 호출되는 메소드
- 인스턴스 변수들의 초기값을 설정
   - 인스턴스 생성
   - __init__메소드 자동 호출

### 소멸자(destructor) 메소드
- 인스턴스 객체가 소멸(파괴)되기 직전에  호출되는 메소드
   - __del__메소드

### 매직 메소드
- __가 있는 메소드는 특수한 동작을 위해 만들어진 메소드
- 특정 상황에 자동으로 불리는 메소드