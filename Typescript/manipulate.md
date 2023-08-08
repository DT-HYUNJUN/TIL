# 타입 조작

## 인덱스드 엑세스 타입

```ts
interface Post {
  title: string
  content: string
  author: {
    id: number
    name: string
    age: number
  }
}

function printAuthorInfo(author: Post["author"]) {
  console.log(`${author.id} - ${author.name}`)
}
```

Post 타입의 author 타입만 가져오고 싶을 때는 인덱스를 이용해서 해당 속성만 가져올 수 있다.

## keyof 연산자

keyof 연산자는 객체 타입으로부터 프로퍼티의 모든 key들을 문자열 리터럴 유니온 타입으로 추출한다.

```ts
interface Person {
  name: string
  age: number
  location: string
}

function getPropertyKey(person: Person, key: keyof Person) {
  return person[key]
}
```

## 맵드 타입

맵드 타입(Mapped Type)은 객체 타입을 기반으로 새로운 객체 타입을 만드는 기능이다.

```ts
interface User {
  id: number
  name: string
  age: number
}

type partialUser = {
  [key: keyof User]?: User[key]
}

// {
//   id?: number
//   name?: string
//   age?: number
// }
```

## 템플릿 리터럴 타입

템플릿 리터럴을 이용해 특정 패턴을 갖는 string 타입을 만드는 기능이다.

```ts
type Color = 'red' | 'green' | 'blue'

type Animal = 'dog' | 'cat' | 'bird'

type ColoredAnimal = `${Color}-${Animal}`
```