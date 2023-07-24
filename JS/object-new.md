# Object

## Object 생성 방법 3가지

### Object 이용

가장 기본이 되는 object 생성

```js
const person = {
  name: 'Park'
  age: 25
}
```

### Class 이용

class를 사용하여 object 생성

```js
class Person {
  name
  age

  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

const park = new Person('Park', 25)
```

### Function 이용

function을 사용하여 object 생성 (생성자 함수)

```js
function PersonFunction(name, age) {
  this.name = name
  this.age = age
}

const park = new PersonFunction('Park', 25)
```

## Property Attribute

### Data Property

키와 값으로 이루어진 실질적인 값을 가지는 property

```js
const park = {
  name: 'Park',
  age: 25
}

console.log(Object.getOwnPropertyDescriptor(park, 'name'))
// { value: 'Park', writable: true, enumerable: true, configurable: true }
```

Object의 static함수인 `getOwnPropertyDescriptor()`로 park 인스턴스의 name 속성을 찍어보니 네 가지의 값들이 나왔다.

1. value - 실제 property의 값
2. writable - 값을 수정할 수 있는지 여부
3. enumberable - 열거가 가능한지 여부
4. configurable - property attribute의 재정의가 가능한지 여부

반대로 property를 추가하고 싶으면 `defineProperty()`를 사용한다.

```js
Object.defineProperty(park, 'year', {
  value: 1998,
  writable: true,
  enumberable: true,
  configurable: true
})
```


### Accessor Property

자체적으로 값을 가지지 않지만 다른 값을 가져오거나 설정할 때 호출되는 함수로 구성된 property (getter, setter)

## Immutable Object

### Extensible

해당 객체가 확장 가능한지를 결정한다.

```js
const park = {
  name = 'Park',
  age = 25
}

console.log(Object.isExtensible(park)) // true
```

기본값은 true로 설정되어있다.

만약 extensible을 막아두면 확장을 해도 바뀌지 않는다.

```js
Object.preventExtensions(park)
console.log(Object.isExtensible(park)) // false

park['year'] = 1998
console.log(park) // { name: 'Park', age = 25 }
```

error가 발생하지는 않지만 확장이 안된다.

하지만 반대로 삭제는 가능하다.

```js
delete park['age']
console.log(park) // { name: 'Park' }
```

### Seal

객체를 밀봉한다. 객체에 속성을 추가/삭제가 불가능해지고 모든 속성을 설정(configuration) 불가능하게 만든다.

```js
const park = {
  name: 'Park',
  age: 25
}

Object.seal(park)

park['year'] = 1998
delete park['age']

console.log(park) // { name: 'Park', age: 25 }

console.log(Object.getOwnPropertyDescriptor(park, 'name'))
// { value: 'Park', writable: true, enumberable: true, configurable: false }
```

### Freezed

Freeze는 읽기 외에 모든 기능을 불가능하게 만든다.

```js
const park = {
  name: 'Park',
  age: 25
}

Object.freeze(park)

console.log(Object.getOwnPropertyDescriptor(park, 'name'))
// { value: 'Park', writable: false, enumberable: true, configurable: false }
```

단, extensible, seal, freeze 모두 nested된 하위 객체는 변경하지 않는다.