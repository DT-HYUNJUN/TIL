# Typescript 기본

## 기본 타입

### **number**

```ts
let num1: number = 123 // type annotation 가장 기본적인 방법

let num2: number = Infinity

let num3: number = NaN
```

### **string**

```ts
let str1: string = "hello"

let str2: string = `hello`

let str3: string = `hello ${num1}`
```

### **boolean**

```ts
let bool1: boolean = true

let bool2: boolean = false
```

### **null**

```ts
let null1: null = null
```

만약 특정 변수의 값을 null로 임시값을 주고싶다면

```ts
let numA: number = null
```

아래와 같이 하면 된다고 생각하지만, typescript에서는 null도 타입의 일종이기 때문에, 에러가 발생한다.

따라서 위 처럼 하고싶다면 tsconfig.json을 수정하면 된다.

```ts
// tsconfig.json
{
  "compilerOptions" : {
    // ...
    "strictNullChecks": false, // 추가
    // ...
  }
}
```

### **undefined**

```ts
let undef1: undefined = undefined
```

### **literal**

리터럴 타입은 변수의 타입을 `값 그 자체`로 설정하는 방식이다.

```ts
let numA: 10 = 10

let stringA: 'hi' = 'hi'

let boolA: true = true
```

### **Array**

```ts
let numArr: number[] = [1, 2, 3]

let strArr: string[] = ['a', 'b', 'c']

let boolArr: Array<boolean> = [true, false, true]
```

혹은 여러 배열에 요소들의 타입이 다양할 때는 `|`를 사용한다.

```ts
let multiArr: (number | string | boolean)[] = [1, 'hi', true]
```

다차원 배열의 경우 괄호를 연장해서 사용한다.

```ts
let doubleArr: number[][] = [
  [1, 2, 3],
  [4, 5, 6]
]
```

### Tuple

튜플은 길이와 타입이 정해진 배열이다.

기존 javascript에는 없는 타입이지만 typescript에서는 배열을 사용한 타입으로 사용된다.

```ts
let tup1: [number, number] = [1, 2]

let tup2: [number, string, boolean] = [1, 'hi', true]
```

앞서 말했듯이 길이가 고정되어 있다고 했지만, 배열을 사용하기에 `pop()`이나 `push()` 메소드의 사용을 막아주지는 못한다.

보통 아래와 같이 배열의 순서를 지정할 때 쓰인다.

```ts
const users: [string, number][] = [
  ['Park', 26],
  ['Kim', 25],
  ['Lee', 18],
  ['Han', 24],
]
```

### **Object**

Typescript에서 객체는 이름을 기준으로 타입을 정의하지 않고, 객체의 구조를 기준으로 타입을 지정한다.

```ts
let user: {
  id: number
  name: string
} = {
  id: 1,
  name: 'park'
}
```

속성중 하나가 선택적 속성이라면, 속성 뒤에 `?`를 붙여준다.

```ts
let user: {
  id?: number
  name: string
} = {
  id: 1,
  name: 'park'
}

user = {
  name: 'kim'
}
```

특정 속성의 값이 변경되는 것을 막기 위해서는 속성 앞에 `readonly` 키워드를 붙여준다.

```ts
let config: {
  readonly apiKey: string
} = {
  apiKey: 'My Api Key'
}
```

### **Type Alias**

동일한 오브젝트를 여러개 만든다고 하면, 각 오브젝트의 타입들을 일일이 적어줘야 하는 번거로움이 생긴다.

```ts
let user: {
  id: number
  name: string
  nickname: string
  birth: string
  bio: string
  location: string
} = {
  id: 1,
  name: 'park',
  nickname: 'P',
  birth: '1998-03-07',
  bio: 'Hi',
  location: '화성시'
}
```

그렇기에 오브젝트의 타입을 따로 별칭으로 만들어 사용하면 더 편리해진다.

```ts
type User = {
  id: number
  name: string
  nickname: string
  birth: string
  bio: string
  location: string
}

let user: User = {
  id: 1,
  name: 'park',
  nickname: 'P',
  birth: '1998-03-07',
  bio: 'Hi',
  location: '화성시'
}
```

type alias는 typescript에서 지원하는 기능으로, 실제 javascript로 변환 하면 type alias는 없어진 것을 확인할 수 있다.

### Index Signature

인덱스 시그니처는 type을 더 유연하게 사용할 수 있도록 해준다.

```ts
type CountryCodes = {
  Korea: string
  UnitedStates: string
  UnitedKingdom: string
}

let countryCodes: CountryCodes = {
  Korea: 'ko',
  UnitedStates: 'us',
  UnitedKingdom: 'uk'
}
```

이런 코드가 있다고 할 때, 지금은 속성이 3개 뿐이지만, 만약 모든 나라를 다 적는다면 type에도 모든 나라에 대한 속성을 하나하나 다 적어야 한다.

```ts
type CountryCodes = {
  [key: string]: string
}

let countryCodes: CountryCodes = {
  Korea: 'ko',
  UnitedStates: 'us',
  UnitedKingdom: 'uk'
}
```

하지만 위 처럼 "key는 string 타입이고, value는 string타입이다" 라고 정의를 해두면 모든 속성에 다 적용이 된다.

또 이때 반드시 포함해야 하는 속성이 있다면 직접 명시해도 된다.

```ts
type CountryCodes = {
  [key: string]: string
  Korea: string
}

let countryCodes: CountryCodes = {
  Korea: 'ko'
}
```

이 때 주의할 점은 인덱스 시그니처의 value와 직접 명시하는 속성의 value 타입이 서로 같아야 한다.

## **Enum**

Enum은 여러가지 값들에 각각 이름을 부여해 열거해두고 사용하는 타입이다. (typescript에만 있는 타입)

```ts
enum Role {
  ADMIN = 0,
  USER = 1,
  GUEST = 2,
}

const user = {
  name: 'park',
  role: Role.ADMIN
}
const user = {
  name: 'kim',
  role: Role.USER
}
const user = {
  name: 'lee',
  role: Role.GUEST
}
```

혹은 enum에 값을 지정 안하면 0부터 차례대로 값이 들어간다.

또 중간에 값을 지정하면 그 다음 부터는 값이 차례대로 들어간다.

```ts
enum Role {
  ADMIN,  // 0
  USER,   // 1
  GUEST,  // 2
}

enum Role {
  ADMIN,      // 0
  USER = 10,  // 10
  GUEST,      // 11
}
```

## **Any / Unknown**

### **Any**

Any타입은 typescript에서만 제공되는 특별한 타입으로 타입 검사를 받지 않는 타입이다.

그렇기에 any타입 변수에 어떠한 값을 넣어도 오류가 발생하지 않는다.

```ts
let anyVar: any = 10

anyVar = 'hi'
anyVar = true
anyVar = {}
anyVar = () => {}
```

타입 검사를 받지 않기에 문법과 규칙으로부터 자유롭지만 동시에 위험한 타입이다.

### **Unknown**

Unknown타입은 any타입과 비슷하지만 더 안전한 타입이다.

```ts
let unknownVar: unknown

unknownVar = 10
unknownVar = 'hi'
unknownVar = {}
unknownVar = () => {}
```

## **Void / Never**

### **Void**

void는 아무것도 없음을 의미하는 타입이다.

```ts
function func1(): void {
  console.log('hello')
}
```

func1()은 'hello'를 출력하는 기능 외에 아무런 return을 하지 않는다.

### **Never**

never는 불가능한 타입을 의미한다.

```ts
function func2() {
  while (true) {}
}

function func3() {
  throw new Error()
}
```

func2()는 무한 루프를 도는 함수다.

무한 루프를 돌기 때문에 return을 할 수가 없기에 반환 타입에 never를 적어준다.

func3()은 에러를 출력하는 함수이기에 프로그램이 종료된다. 그러기에 또한 return을 할 수 없어서 반환 타입에 never를 적어준다.