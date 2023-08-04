# 함수

## 함수 타입

함수의 매개변수와 반환값에도 타입을 지정할 수 있다.

```ts
function func(a: number, b: number): number {
  return a + b
}
```

함수의 반환값은 자동으로 추론되기 때문에 생략 가능하다.

```ts
function func(a: number, b: number) {
  return a + b
}
```

화살표 함수 또한 동일하다

```ts
const func = (a: number, b: number) => a + b
```

만약 매개변수에 기본값을 설정한다면 타입이 자동으로 추론된다.

```ts
function introduce(name = "park") {
  console.log(name)
}
```

## 함수 타입 표현식

함수 타입을 별도로 지정할 수 있다.

```ts
type Add = (a: number, b: number) => number

const add: Add = (a, b) => a + b
```

함수 타입은 다음과 같이 여러 함수가 동일한 타입을 갖는 경우에 유용하게 쓰인다.

```ts
type Operation = (a: number, b: number) => number

const add: Operation = (a, b) => a + b
const sub: Operation = (a, b) => a - b
const mul: Operation = (a, b) => a * b
const div: Operation = (a, b) => a / b
```

### 호출 시그니쳐

호출 시그니쳐는 함수 타입 표현식과 동일하게 함수의 타입을 별도로 정의하는 방식이다.

```ts
type Operation = {
  (a: number, b: number): number
}

const add: Operation = (a, b) => a + b
```

## 함수 타입의 호환성

함수 타입의 호환성은 특정 함수 타입을 다른 함수 타입으로 괜찮은지 판단하는 것을 의미한다.

함수 타입의 호환성에는 두 가지 기준이 있다.

1. 두 함수의 반환값 타입
2. 두 함수의 매개변수 타입

### 두 함수의 반환값 타입

```ts
type A = () => number
type B = () => 10

let a: A = () => 10
let b: B = () => 10

a = b  // O
b = a  // X
```

A 타입은 number 타입을 반환하고, B 타입은 10 number literal을 반환한다.

두 타입을 비교했을 때는 A 타입이 슈퍼타입이고 B 타입이 서브 타입이다.

- A : 슈퍼 타입
- B : 서브 타입

그렇기에 b 함수를 a 함수에 할당하는 것은 가능하나(업 캐스팅)

b 함수를 a 함수에 할당하는 것은 불가능 하다(다운 캐스팅)

### 두 함수의 매개변수 타입

매개변수 같은 경우에는 두 가지의 경우가 있다.

1. 매개변수의 개수가 같을 때
2. 매개변수의 개수가 다를 때

#### **매개변수의 개수가 같을 때**

```ts
type C = (value: number) => void
type D = (value: 10) => void

let c: C = (value) => {}
let d: D = (value) => {}

c = d  // X
d = c  // O
```

C 타입은 매개변수로 number 타입을, D 타입은 매개변수로 10 number literal 타입을 받는다.

매개변수는 앞에서의 반환값과 달리 d 를 c에 할당하는 것은 불가능하나

c를 d에 할당하는 것은 가능하다.

이는 매개변수로 객체가 들어올 때 좀 더 두드러진다.

```ts
type Animal = {
  name: string
}

type Dog = {
  name: string
  color: string
}

let animalFunc = (animal: Animal) => {
  console.log(animal.name)
}

let docFunc = (dog: Dog) => {
  console.log(dog.name)
  console.log(dog.color)
}

animalFunc = dogFunc  // X
dogFunc = animalFunc  // O
```

docFunc을 animalFunc에 할당하게 되면 Dog 타입의 color 프로퍼티를 Animal 타입에서는 쓸 수 없기 때문에 할당이 불가능하게 된다.

animalFunc = DogFunc를 코드로 표현하면 다음과 같다.

```ts
let animalFunc = (animal: Animal) => {
  console.log(animal.name)
  console.log(animal.color)
}
```

#### **매개변수의 개수가 다를 때**

```ts
type Func1 = (a: number, b: number) => void
type Func2 = (a: number) => void

let func1: Func1 = (a, b) => {}
let func2: Func2 = (a) => {}

func1 = func2  // O
func2 = func1  // X
```

func2를 func1에 할당할 때 매개변수 하나가 모자라지만 js에서는 매개변수를 버리는 것이 허용되기 때문이다.

하지만 func1을 func2로 할당하는 것은 2개의 매개변수가 들어갈 자리가 없기 때문에 오류가 발생한다.

## 함수 오버로딩

함수 오버로딩은 같은 이름의 함수를 매개변수의 개수나 타입에 따라 여러가지 버전으로 만드는 문법을 말한다.

```c
void func(int a) {}
void func(int a, int b) {}
...
```

typescript에서 함수 오버로딩을 구현하려면 우선 오버로드 시그니쳐를 만들어야 한다.

```ts
// 오버로드 시그니쳐
function func(a: number): void
function func(a: number, b: number, c: number): void
```

그 다음으로는 구현 시그니쳐를 만든다.

```ts
// 오버로드 시그니쳐
function func(a: number): void
function func(a: number, b: number, c: number): void


// 구현 시그니쳐
function func(a: number, b?: number, c?: number) {}
```

우리가 구현하려는 함수는 a매개변수를 받는 함수와 a, b, c 매개변수를 받는 함수다.

즉 a 매개변수는 필수로 받고 b, c매개변수는 선택적으로 받기에 ?를 사용하여 선택적 매개변수로 만들어준다.

그 다음 타입좁히기로 원하는 구현을 완성해준다.

```ts
function func(a: number): void
function func(a: number, b: number, c: number): void


// 구현 시그니쳐
function func(a: number, b?: number, c?: number) {
  if (typeof b === 'number' && typeof c === 'number') {
    console.log(a + b + c)
  } else {
    console.log(a * 20)
  }
}

func(1)           // O
func(1, 2)        // X
func(1, 2, 3)     // O
func(1, 2, 3, 4)  // X
```

## 사용자 정의 타입가드

사용자 정의 타입가드는 참 또는 거짓을 반환하는 함수를 이용해 우리가 타입 가드를 만들 수 있도록 하는 문법이다.

```ts
type Dog = {
  name: string
  isBark: boolean
}

type Cat = {
  name: string
  isScratch: boolean
}

type Animal = Dog | Cat

function warning(animal: Animal) {
  if ("isBar" in animal) {
    // 강아지
  } else if ("isScratch" in animal) {
    // 고양이
  }
}
```

Dog와 Cat 타입을 정의하고 그 둘의 합집합인 Animal 타입을 정의했다.

그 다음 warning 함수에 매개변수로 Animal 타입 객체를 받고, Dog 타입일 때와 Cat 타입일 때를 나눴다.

하지만 in 연산자는 좋은 방법은 아니기에 타입 가드를 만들어 타입을 좁히는 것이 더 좋다.

```ts
function isDog(animal: Animal): animal is Dog {
  return (animal as Dog).isBark !== undefined
}

function isCat(animal: Animal): animal is Cat {
  return (animal as Cat).isScratch !== undefined
}

function warning(animal: Animal) {
  if ("isBar" in animal) {
    // 강아지
  } else if ("isScratch" in animal) {
    // 고양이
  }
}
```