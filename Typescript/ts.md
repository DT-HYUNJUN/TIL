# TS

## Type Tree

Typescript 타입간의 계층 구조

![Type-Tree](./type-tree.png)

### **Unknown**

unknown 타입은 최 상단에 위치한다.

따라서 unknown 타입 변수에는 모든 타입의 값을 할당할 수 있다.

```ts
let unknownVar: unknown
unknownVar = 1
unknownVar = 'hi'
unknownVar = true
unknownVar = {}
```

### **Never**

never 타입은 unknown과 반대로 최 하단에 위치한다.

따라서 never 타입 변수는 모든 타입에 할당될 수 있다.

```ts
function neverFunc() {
  while (true) {}
}

let num: number = neverFunc()
```

### **Void**

void 타입은 undefined의 슈퍼타입이기에 undefined 타입을 void 변수에 할당할 수 있다.

또한 반환값이 void인 함수에 undefined 타입을 반환해도 된다.

```ts
function voidFunc(): void {
  console.log('hi')
  return undefined // 또는 return만 써도 된다.
}
```

### **Any**

any 타입은 타입 계층도를 완전히 무시하는 타입이다.

모든 타입의 슈퍼타입이 될 수도 있고, 모든 타입의 서브타입이 될 수도 있다.

하지만 공집합인 never 타입 변수에는 any를 할당할 수 없다.

## 객체 타입의 호환성

```ts
type Animal = {
  name: string
  color: string
}

type Dog = {
  name: string
  color: string
  breed: string
}

let animal: Animal = {
  name: '기린',
  color: 'yellow'
}

let dog: Dog = {
  name: '댕댕이',
  color: 'white',
  breed: '진도'
}

animal = dog // O

dog = animal // X
```

객체도 마찬가지로 업 캐스팅은 허용되지만 다운 캐스팅은 허용되지 않는다.

Animal 타입이 슈퍼 타입이고 Dog 타입이 서브 타입이다.

그 이유는 typescript는 property를 기준으로 타입을 정의하기 때문이다.

Animal 타입은 name, color를 property로 갖는 객체를 포함하는 집합으로 볼 수 있고,

Dog 타입은 name, color, breed를 property로 갖는 객체를 포함하는 집합으로 볼 수 있다.

그러므로 Dog 타입에 포함되는 객체는 무조건 Animal 타입에도 포함되기 때문에 Animal 타입이 슈퍼타입이 된다.

## 대수 타입

대수 타입은 여러개의 타입을 합성해서 새롭게 만들어낸 타입이다.

종류로는 합집합(Union) 타입과 교집합(Intersection) 타입이 존재한다.

### 합집합

Union 타입은 |를 이용한다.

```ts
let a: number | string

a = 1
a = 'Hi'
```

변수 a에는 number 또는 string 타입이 올 수 있다.

배열 또한 Union 타입을 이용할 수 있다.

```ts
let arr: (number | string | boolean)[] = [1, 'hi', true]
```

객체 타입의 Union 타입도 가능하다.

```ts
type Dog = {
  name: string
  color: string
}

type Person = {
  name: string
  language: string
}

type Union1 = Dog | Person

let union1 = {
  name: '',
  color: ''
}

let union2 = {
  name: '',
  language: ''
}

let union3 = {
  name: '',
  color: '',
  language: ''
}

// union4 같은 경우에는 불가능하다.
let union4 = {
  name: ''
}
```

Union1 타입은 Dog 타입과 Person 타입의 합집합이다.

그 말은, Dog 타입(name, color) 또는 Person 타입(name, language) 타입의 객체를 포함하는 타입이라는 말이다.

union4 객체 같은 경우에는 property로 name만 있기 때문에 Union1 타입이 될 수 없다.

### 교집합

Intersection 타입은 &를 이용한다.

```ts
let inter: number & string // never
```

number 타입과 string 타입간에는 교집합이 없기에 never 타입으로 추론된다.

기본 타입들 경우에는 겹치는 교집합이 없기 때문에 보통 객체에서 intersection 타입이 사용된다.

```ts
type Dog = {
  name: string
  color: string
}

type Person = {
  name: string
  language: string
}

type Intersection = Dog & Person

let intersection: Intersection = {
  name: '',
  color: '',
  language: ''
}
```

Intersection 타입은 Dog 타입과 Person 타입을 모두 포함하고 있다.

## 타입 추론

typescript는 타입이 정의되어 있지 않은 변수의 타입을 자동으로 추론하는데, 이 기능을 타입 추론이라고 한다.

```ts
let num1 = 10
```

num1 변수의 타입을 정의하지 않았지만, 타입 추론으로 num1의 타입은 number가 된다.

만약 초기값을 설정하지 않게되면 자동으로 any 타입으로 추론하게 된다.

```ts
let a

a = 10
a.toFixed()

a = 'hi'
a.toUpperCase()
```

변수 a에 초기값을 설정하지 않았으므로 자동으로 any타입으로 추론하게 되어 코드의 흐름에 따라 타입이 계속 변화한다.

const로 선언된 상수도 타입 추론이 가능하다.

```ts
const num = 10 // 10 number literal
```

하지만 const 변수는 값을 변경할 수 없기에 리터럴 타입으로 추론된다.

## 타입 단언

```ts
type Person = {
  name: string
  age: number
}

let person: Person = {}
person.name = "park"
person.age = 26
```

person 객체를 초기화 할 때 빈 객체를 넣어두고 싶다고 가정하고 싶어도 typescript는 허용하지 않는다. 빈 객체는 Person 타입이 아니기에 오류가 발생한다.

이럴 때는 아래와 같이 빈 객체가 Person 타입이라고 단언해주면 된다.

```ts
type Person = {
  name: string
  age: number
}

let person = {} as Person
person.name = "park"
person.age = 26
```

"값 as 타입" 으로 원하는 타입으로 단언할 수 있다.

초과 property에도 쓸 수 있다.

```ts
type Person = {
  name: string
  age: number
}

let person = {
  name: 'park',
  age: 26,
  language: 'kor'
} as Person
```

타입 추론에도 조건은 있다.

A as B로 표현할 때

1. A가 B의 슈퍼 타입
2. A가 B의 서브 타입

객체를 const로 단언하면 모든 property가 readonly를 갖는다.

```ts
let cat = {
  name: 'kitty',
  color: 'yellow'
} as const
```

## 타입 좁히기

매개변수로 number 또는 string을 받는 함수가 있다고 가정하자

```ts
function func(value: number | string) {

}
```

number 일때는 toFixed()를, string 일때는 toUpperCase() 메서드를 사용하고 싶다면 if문을 사용해서 타입을 보장해야 한다.

```ts
function func(value: number | string) {
  if (typeof value === 'number') {
    console.log(value.toFixed())
  } else if (typeof value === 'string') {
    console.log(value.toUpperCase())
  }
}
```

### instanceof 타입가드

instanceof를 이용하면 내장 클래스 타입을 보장할 수 있다.

```ts
function func(value: number | string | Date | null) {
  if (typeof value === 'number') {
    console.log(value.toFixed())
  } else if (typeof value === 'string') {
    console.log(value.toUpperCase())
  } else if (value instanceof Date) {
    console.log(value.getTime())
  }
}
```

### in 타입가드

만약 우리가 직접 만든 type과 함께 사용하기 위해서는 in 연산자를 사용하면 된다.

```ts
type Person = {
  name: string
  age: number
}

function func(value: number | string | Date | null | Person) {
  if (typeof value === 'number') {
    console.log(value.toFixed())
  } else if (typeof value === 'string') {
    console.log(value.toUpperCase())
  } else if (value instanceof Date) {
    console.log(value.getTime())
  } else if (value && "age" in value) {
    console.log(value.name, value.age)
  }
}
```