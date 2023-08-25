# RESTful API

## REST (Representational State Transfer)

REST란 웹 상에서 자원(리소스)을 표현하고 상태를 전달하는 아키텍처 스타일을 말한다.

웹 서비스 설계 원칙을 기반으로한 API 방법론이다.

## 구성

- 자원(Resource) - URI
- 행위(Verb) - HTTP METHOD
- 표현(Representations)

## 특징

1. Uniform (유니폼 인터페이스)

Uniform Interface는 URI로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일을 말한다.

2. Stateless (무 상태성)

REST는 작업을 위한 상태정보를 따로 저장하고 관리하지 않는다. 그렇기에 API 서버는 들어오는 요청만을 단순히 처리한다. 때문에 서비스의 자유도가 높아지고 불필요한 정보를 관리하지 않음으로써 구현이 단순해진다.

3. Cacheable (캐시 가능)

REST의 가장 큰 특징 중 하나는 HTTP라는 웹표준을 그대로 사용하기 때문에 웹에서 사용하는 기존 인프라를 그대로 활용할 수 있다는 점이다. 따라서 HTTP가 가진 캐싱 기능을 적용할 수 있다.

4. Self-Descriptiveness (자체 표현 구조)

REST API 메시지만 보고도 이를 쉽게 이해할 수 있는 자체 표현 구조로 되어있다.

5. Client - Server 구조

클라이언트와 서버가 각각의 역할이 확실히 구분되기 때문에 서로간의 의존성이 줄어들게 된다.

6. 계층형 구조

REST 서버는 다중 계층으로 구성될 수 있기에 구조상의 유연성을 가지게 된다.

## REST API 디자인 가이드

REST API 설계 시 가장 중요한 항목은 다음 두 가지다.

1. URI는 정보의 자원을 표현해야 한다.
2. 자원에 대한 행위는 HTTP METHOD (GET, POST, PUT, DELETE)로 표현해야 한다.