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