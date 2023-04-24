# REST API

## API (Application Programming Interface)

API란 애플리케이션과 프로그래밍으로 소토하는 방법을 말한다.

복잡한 코드를 추상화하여 대신 사용할 수 있는 몇 가지 더 쉬운 구문을 제공해준다.

## REST (Representational State Transfer)

API 서버를 개발하기 위한 일종의 SW 설계 방법론을 뜻한다.

자원을 정의하고, 자원에 대한 주소를 지정하는 전반적인 방법을 서술한다.

### 자원을 정의하고 주소를 지정하는 방법

자원을 식별
  - URI

자원의 행위
  - HTTP Methods

자원의 표현
  - JSON으로 표현된 데이터를 제공

## Response JSON

기존에 클라이언트의 요청에 html을 응답하는 서버에서, JSON 데이터를 응답하는 서버로 작동한다.

따라서 Django에서는 더 이상 Template을 작성하지 않게되며 FE와 BE가 분리되어 구성되게 된다.

## Serialization

여러 시스템에서 활용하기 위해 데이터 구조나 객체 상태를 나중에 재구성할 수 있는 포맷으로 변환하는 과정

즉, 나중에 다시 쉽게 사용할 수 있는 포맷으로 변환하는 과정이다.