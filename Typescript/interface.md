# 인터페이스

## 인터페이스

인터페이스란 타입 별칭과 동일하게 타입의 이름을 지어주는 또 다른 문법이다.

```ts
interface Person {
  name: string
  age: number
}

const person: Person = {
  name: 'park',
  age: 25
}
```

### 선택적 속성과 readonly

선택적 속성과 readonly 또한 사용 가능하다.

```ts
interface Person {
  readonly name: string
  age?: number
}

const person: Person = {
  name: 'park',
  // age: 25
}

person.name = 'kim' // error
```

### 메서드 타입

호출 시그니쳐를 이용하여 메서드 타입을 정의할 수 있다.

```ts
interface Person {
  readonly name: string
  age?: number
  sayHi(): void 
}
```

또한 메서드 오버로딩 구현이 가능하다.

```ts
interface Person {
  readonly name: string
  age?: number
  sayHi(): void
  sayHi(a: number, b: number): void
}
```

## 인터페이스 확장

인터페이스 확장은 하나의 인터페이스를 다른 인터페이스들이 상속받아 중복된 프로퍼티를 정의하지 않도록 하는 문법이다.

```ts
interface Animal {
  name: string
  color: string
}

interface Dog extends Animal {
  isBark: boolean
}

interface Cat extends Animal {
  isScratch: boolean
}
```

extends 키워드를 사용하여 인터페이스를 확장한다.

### 프로퍼티 재정의

확장과 동시에 프로퍼티를 재정의 할 수 있다.

```ts
interface Animal {
  name: string
  color: string
}

interface Dog extends Animal {
  name: 'doggy'
  isBark: boolean
}
```

단, 재정의 할 때는 서브타입으로만 재정의가 가능하다.

## 인터페이스 선언 합치기

타입 별칭은 동일한 스코프 내에 중복된 이름으로 선언할 수 없지만 인터페이스는 가능하다.

```ts
interface Person {
  name: string
}

interface Person {
  age: number
}

const person: Person = {
  name: 'park',
  age: 25
}
```