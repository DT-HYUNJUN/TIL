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

## Constructor Function

```js
function Person(name, age) {
  this.name = name
  this.age = age

  this.sayHello = function() {
    return `Hi I'm ${this.name}!`
  }
}

const park = new Person('Park', 25)
```

## Prototype

```js
function Person(name, age) {
  this.name = name
  this.age = age

  this.sayHello = function() {
    return `Hi, I'm ${this.name}!`
  }
}

const park = new Person('Park', 25)
const kim = new Person('Kim', 25)

console.log(park.sayHello === kim.sayHello) // false
```
Person이라는 생성자 함수를 만들었고, sayHello 메서드를 속성으로 설정했다.

이 상태에서 park, kim 인스턴스를 생성하고 각각의 sayHello를 비교했더니 false가 나왔다.

어찌보면 당연하다. 왜냐하면 인스턴스를 만들었기의 각각의 고유의 속성으로 메모리 주소가 할당되기 때문이다.

같은 동작을 하는 메서드인데, 인스턴스를 만들 때 마다 메모리 주소가 할당되니 불필요하게 메모리를 쓴다고 할 수 있다.

이러한 경우에는 생성자 함수의 prototype으로 메서드를 생성할 수 있다.

```js
function Person(name, age) {
  this.name = name
  this.age = age
}

Person.prototype.sayHello = function() {
  return `Hi, I'm ${this.name}!`
}

const park = new Person('Park', 25)
const kim = new Person('Kim', 25)

console.log(park.sayHello === kim.sayHello) // true
```

true가 나오는 이유는 park, kim 인스턴스는 new를 통해 만들어졌기에 Person.prototype을 상속받기 때문이다.

## This

1. 일반 함수 호출할땐 this가 최상위 객체 (global 또는 window)를 카리킨다.
2. 메서드로 호출할땐 호출된 객체가 가리킨다.
3. new 키워드를 사용해서 객체를 생성했을땐 객체를 가리킨다.

## Closure

```js
function cacheFunction(newNumber) {
  // 아래 계산이 오래 걸린다는 가정
  var number = 10 * 10

  return number * newNumber
}

console.log(cacheFunction(10))
console.log(cacheFunction(20))
console.log(cacheFunction(30))
```

위 코드에서는 오래 걸리는 계산이라고 가정한 (10 * 10)를 cacheFunction()을 실행할 때 마다 작동하고 있다.

만약 cacheFunction()을 지속적으로 반복해서 실행한다고 하면 많은 리소스가 필요하게 된다.

그렇다면 오래 걸리는 계산인 (10 * 10)을 초기에 실행 해두고 cacheFunction()을 불러올 때 마다 newNumber만 곱해서 반환해주면 리소스를 효율적으로 쓸 수 있게된다.

```js
function cacheFunction(newNumber) [
  var number = 10 * 10

  function innerCacheFunction(number) {
    return number * newNumber
  }

  return innerCacheFunction
]

const runner = cacheFunction()

console.log(runner(10))
console.log(runner(20))
console.log(runner(30))
```

cacheFunction() 내부에 innerCacheFunction()을 만들고 그 안에서 결과값을 return 하는 구조로 만들었다.

이렇게 만들면 runner에 cacheFunction()을 대입하는 순간 (10 * 10)이 실행된 상태로 runner에 존재하기 때문에 innerCacheFunction()에서 argument로 받은 newNumber만 계산한 결과를 반환해주면 된다.