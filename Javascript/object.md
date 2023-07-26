# Object

키로 구분된 데이터 집합을 저장하는 자료형

## 객체의 구조

- {}를 이용해 작성
- {}안에는 key: value 쌍으로 구성된 속성(property)를 여러 개 넣을 수 있음
- key는 문자형, value는 모든 자료형이 허용

```javascript
const user = {
  name: "Park",
  age: 30,
  "key with space": true,
}
```

## 속성 활용

### CRUD

```javascript
// 조회
console.log(user.age) // 30
console.log(user["key with space"]) // true

// 추가
user.address = "korea"
console.log(user) // {..., address: "korea"}

// 수정
user.age = 20
console.log(user.age) // 20

// 삭제
delete user.address
console.log(user) // {name: "Park", age: 20, key with space: true}
```

### 존재 여부 확인

```javascript
console.log("age" in user) // true
console.log("country" in user) // false
```

### 단축 속성

키 이름과 값으로 쓰이는 변수의 이름이 같은 경우, 단축 구문을  사용할 수 있음

```javascript
const age = 30
const address = "korea"

const oldUser = {
  age: age,
  address: address,
}

// 단축
const newUser ={
  age,
  address,
}
```

### 계산된 속성

키가 []로 둘러싸여 있는 속성

고정된 값이 아닌 변수 값을 사용할 수 있음

```javascript
const product = prompt("물건 이름을 입력해주세요") // 연필
const prefix = "my"
const suffix = "property"

const bag = {
  [product]: 5,
  [prefix + suffix]: "value",
}

console.log(bag) // {연필: 5, myproperty: "value"}
```

## Method

객체 속성에 정의된 함수

object.method()로 객체를 '행동'할 수 있도록 함

```javascript
const person = {
  name: "Park",
  greeting: function () {
    return "Hello"
  },
}

console.log(person.greeting()) // Hello
```

### this

this 키워드를 사용해 객체에 대한 특정한 작업을 수행 할 수 있음

```javascript
const person = {
  name: "Park",
  greeting: function () {
    return `Hello my name is ${this.name}`
  },
}

console.log(person.greeting()) // Hello my name is Park
```

this는 함수나 메서드를 호출한 객체를 가리키는 키워드.