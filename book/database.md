## [README](../README.md) <img src="https://img.shields.io/badge/README-018EF5?style=flat&logo=README&logoColor=white" /><br>
## [Markdown](markdown.md) <img src="https://img.shields.io/badge/MARKDOWN-000000?style=flat&logo=Markdown&logoColor=white" />
## [Git](git.md) <img src="https://img.shields.io/badge/GIT-F05032?style=flat&logo=Git&logoColor=white" />
## [Python](python.md) <img src="https://img.shields.io/badge/PYTHON-3776AB?style=flat&logo=python&logoColor=white" />
## [Decoration](decorate.md) 🎨
## [Career](career.md) 👨‍💻<br></br>



# MySQL 접속 방법

1. MySQL Workbench 를 실행한다.
2. MySQL Connections + 버튼을 누른다.
3. 새롭게 열린 창에다가 다음 사항을 입력한다.
    - Connection Name : 연결 객체의 이름. 본인이 구분하기 쉬운 영문 이름으로 입력한다.
    - Hostname: 로컬로 사용하기 위해서는 127.0.0.1 또는 localhost로 입력한다. 원격으로 사용하기 위해서는 해당하는 서버의 IP 주소를 입력한다.
    - Username: MySQL을 설치할 때 지정한 이름을 입력하는데, 보통 초기 super 사용자는 root로 입력한다.
    - Port: 다른 RDBMS를 사용할 경우, 해당하는 Port 번호를 입력하지만, MySQL을 사용하기에 3306을 입력한다.
    - Password: 비밀번호를 입력한다.
4. 이후에 연결 검사가 정상적을 진행되면 끝이 난다.

# SQL Query
SQL 이란 뜻은 Structed Query Language의 줄임말로, 구조적 쿼리 언어를 말한다. (여기서 Query란 '질의' 를 뜻한다.)

즉 사용자가 원하는 명령을 질의문을 통해 표현하는 것이다.

Query문에는 여러가지가 있지만 먼저 기본적인 질의문을 알아보자.

- CREATE
- INSERT
- SELECT
- UPDATE
- DELETE
- DROP

## CREATE
일단 테이블을 만들어야 한다. 테이블은 CREATE문으로 생성할 수 있다.

```SQL
CREATE TABLE Students (
    sid     CHAR(20),
    name    CHAR(20),
    age     INTEGER
)
``` 
Students 라는 테이블에 sid, name, age 속성값들과 데이터 타입을 지정해준다.

여기서 sid값에 CHAR(20) 로 설정한 이유는,

sid같은 경우엔 따로 정수 타입의 연산을 필요로 하지 않기에 CHAR로 생성해준다.

이처럼 속성값의 데이터 타입을 적절하게 설정해주는 것이 중요하다.

## INSERT
테이블을 생성했으니, 테이블에 튜플을 삽입해준다. 
INSERT 명령을 사용하여 데이터를 삽입해준다.

```SQL
INSERT
INTO Students   (sid, name, age)
VALUES  (2200032, '박현준', 26)
```
그러면 Students 테이블에는 튜플 (2200032, '박현준', 26) 이 생성되었다.

## SELECT
튜플을 삽입했으니 테이블을 조회해보자. SELECT 명령을 통하여 테이블을 조회할 수 있다.

```SQL
SELECT *
FROM Students
```
해석을 해보면 Students 테이블에서 모든 속성을(*) 조회하는 질의문이다.

만약 원하는 값만 찾고싶다면
```SQL
SELECT S.sid
FROM Students S
```
이렇게 sid값만 뽑아낼 수 있다.

## UPDATE
만약 테이블의 이미 있는 행 또는 열의 값을 수정해야 하는 일이 발생한다면 UPDATE 명령을 통하여 값을 수정할 수 있다.

예를들어 6월부터 만 나이로 통일한다면 age 값을 수정해야 한다.
```SQL
UPDATE Students S
SET S.age = S.age - 1
```
이런식으로 해당하는 테이블의 속성값들을 수정할 수 있다.

## DELETE
졸업식이 다가오는데, 졸업을 하면 졸업생들의 데이터를 관리할 필요가 없어진다. 이 때는 DELETE 명령을 통하여 해당하는 튜플을 제거할 수 있다.
```SQL
DELETE
FROM Students S
WHERE S.sid = 2200032
```
sid가 2200032인 학생을 Students 테이블에서 제거 한다.
여기서 새로운 WHERE 질의문이 나왔는데,

WHERE은 어떤 행들이 수정되어야 하는가를 결정해준다. 여기서는 학번이 2200032인 학생을 제거했는데

다른식으로는, WHERE S.age > 30 이런식으로 30살 보다 많은 학생들을 모두 제거해줄 수 있다.

## DROP
예를들어 파괴왕 주호민님이 머물다 가셔서 대학교가 없어진다고 하자.

이럴때는 더이상 Students 테이블을 유지할 필요가 없어진다.

과감하게 DROP 명령을 통해 테이블을 제거해준다.

```SQL
DROP
TABLE Students
```