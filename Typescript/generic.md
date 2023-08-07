# 제네릭

## 제네릭 소개

```ts
function func<T>(value: T): T {
  return value
}

const num = func(10)          // number 타입
const string = func("string") // string 타입
```

함수의 매개변수의 타입에 따라 함수의 타입이 추론된다.

T는 타입 변수라고 부른다.

또는 직접 타입을 명시해도 된다.

```ts
function func<T>(value: T): T {
  return value
}

let arr = func<[number, number, number]>([1, 2, 3])   // [number, number, number] 타입
let arr = func([1, 2, 3])                             // number[] 타입
```

## 타입 변수 응용

### 사례 1

```ts
function swap(T, U)(a: T, b: U) {
  return [b, a]
}

const [a, b] = swap("1", 2)
```

T에는 "1"의 타입인 string, U에는 2의 타입인 number가 들어간다.

### 사례 2

```ts
function returnFirstValue<T>(data: T[]) {
  return data[0]
}

let num = returnFirstValue([1, 2, 3])               // number

let value = returnFirstValue([1, "hello", "park"])  // number | string
```

num 같은 경우에는 number[] 타입의 data가 들어왔으니 함수의 반환값은 number로 추론된다.

하지만 value는 (number | string)[]의 타입이 들어갔으니 함수의 반환값은 (numer | string)이 된다.

### 사례 3

사례 2에서 첫 번째 요소의 타입만 받고 싶으면 아래와 같이 튜플 타입과 나머지 파라미터를 사용하면 된다.

```ts
function returnFirstValue<T>(data: [T, ...unknown[]]) {
  return data[0]
}

let num = returnFirstValue([1, "hello", "park"])    // number
```

### 사례 4

마지막 사례는 타입에 제한을 두는 방법이다.

```ts
function getLength<T extends { length: number }>(data: T) {
  return data.length
}

getLength("123")            // O
getLength([1, 2, 3])        // O
getLength({ length: 1 })    // O
getLength(undefined)        // X
getLength(null)             // X
```

## map, forEach 메서드 타입 정의

### map

```ts
const arr = [1, 2, 3]

function map<T>(data: T[], callback: (item: T) => T): T[] {
  let result = []
  for (let i = 0; i < data.length; i++) {
    result.push(callback(arr[i]))
  }
  return result
}

map(arr, (item) => item * 2)
// number[] 타입의 [2, 4, 6] 반환
```

하지만 콜백함수의 return 타입이 배열의 타입과 일치할 필요는 없기에 toString() 같은  경우는 오류가 발생한다.

```ts
function map<T, U>(data: T[], callback: (item: T) => U): U[] {
  let result = []
  for (let i = 0; i < data.length; i++) {
    result.push(callback(arr[i]))
  }
  return result
}
```

그렇기에 콜백함수의 반환값에는 새로운 타입은 U를 설정해준다.

### forEach

forEach같은 경우에는 map과는 다르게 반환값이 없기에 간단하다.

```ts
const arr = [1, 2, 3]

function forEach<T>(data: T[], callback: (item: T) => void) {
  for (let i = 0; i < data.length; i++) {
    callback(arr[i])
  }
}
```

## 제네릭 인터페이스

제네릭은 인터페이스에도 적용할 수 있다.

```ts
interface KeyPair<K, V> {
  key: K
  value: V
}

let keypair: KeyPair<string, number> = {
  key: 'mykey',
  value: 10
}
```

제네릭으로 인터페이스를 정의하면 인스턴스를 생성할 때 <> 안에 타입을 지정해줘야 한다.

### 인덱스 시그니쳐와 같이 사용

```ts
interface Map<V> {
  [key: string]: V
}

let map: Map<string> = {
  key: 'mykey'
}
```

### 제네릭 타입 별칭

타입에도 제네릭을 적용할 수 있다.

```ts
type Map<V> = {
  [key: string]: V
}

let map: Map<string> = {
  key: 'mykey'
}
```

## 제네릭 클래스

```ts
class List<T> {
  constructor(private list: T[]) {}

  push(data: T) {
    this.list.push(data)
  }

  pop() {
    return this.list.pop()
  }

  print() {
    console.log(this.list)
  }
}

const numberList = new List([1, 2, 3])

const stringList = new List(["1", "2", "3"])
```