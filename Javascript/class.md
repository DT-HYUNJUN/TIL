# Class

## Class란

`Class`는 `객체`를 생성하기 위한 `템플릿`으로 볼 수 있다.

쉽게 말해, 붕어빵 틀에 팥을 넣으면 팥 붕어빵, 슈크림을 넣으면 슈크림 붕어빵이 되는 것 처럼 `붕어빵(객체)`을 생성하기 위한 `붕어빵 틀(템플릿)` 이라고 생각하면 쉽다.

## Class 정의

```js
class Person {
  // 없어도 됨
  name
  age

  constructor(name, age) {
    this.name = name
    this.age = age
  }

  hello() {
    console.log(`안녕하세요, ${this.age}살 ${this.name}입니다.`)
  }
}

const park = new Person('Park', 25)
console.log(park) // Person { name: 'Park', age: 25 }
```

### constructor()

생성자 메서드 `constructor()`를 통해 인스턴스 객체를 초기화할 때 `초기값`을 설정해준다.

이 때, class 자신의 property를 사용하기 위해서는 `this`키워드를 사용하여 접근할 수 있다.

## Getter / Setter

### Getter

getter를 사용하는 경우는 두 가지가 있다.

1. 데이터를 가공해서 새로운 데이터를 반환할 때
2. private한 값을 반환할 때

객체에서 getter를 불러올 때는 괄호를 쓰지 않고 불러온다.


```js
class Person {
  // ...

  get nameAndAge() {
    return `${this.name}-${this.age}`
  }
}

const park = new Park('Park', 25)
console.log(park.nameAndAge) // Park-25
```

### Setter

Setter는 Getter의 반대 개념이라고 볼 수 있다. Getter는 값을 가져온다고 한다면 Setter는 값을 설정한다.

```js
class Person {
  // ...

  set setName(name) {
    this.name = name
  }
}

const park = new Park('Park', 25)
park.setName = 'HJ'

console.log(park.name) // HJ
```

`set` 키워드로 setter 이름을 설정하고 하나의 파라미터를 반드시 설정한다.

굳이 왜 이런 방법을 쓰는지 의문을 가질 수 있다.

setter를 쓰는 이유는 아까 말했던 getter와 setter를 쓰는 두 가지 경우 중에서 두 번째에 해당하는데,

property를 private으로 설정하면 setter를 사용해서 값을 바꿔줘야 하기 때문이다.

## Static

`static`키워드는 클래스에 귀속이 되도록 하는 키워드다.

```js
class Person {
  name
  age
  static groupName = "Student"

  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

const park = new Park('Park', 25)
console.log(park) // Person { name: 'Park', age: 25 } (groupName인 "Student"는 찾아볼 수 없다.)
console.log(Person.groupName) // Student
```

### Factory Constructor

static키워드를 가장 많이 사용하는 방식이다. 

```js
class Person {
  name
  age

  constructor(name, age) {
    this.name = name
    this.age = age
  }

  static fromObject(object) {
    return new Person {
      object.name
      object.age
    }
  }
}

const park = Person.fromObject({
  name: "Park",
  age: 25,
})

console.log(park) // Person { name: 'Park', age: 25 }
```

이런식으로 static키워드를 활용해서 인스턴스를 만들어 낼 수 있다.

## 상속

상속은 객체들 간의 관계를 구축하는 방법이다.

자식 클래스는 부모 클래스로 부터 속성이나 동작을 상속받을 수 있다.

```js
class Person {
  name
  age

  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

class Student extends Person {
  hello() {
    return "Hello! I'm student"
  }
}

const park = new Student('Park', 25)
console.log(park)       //Student { name: 'Park', age: 25 }
console.log(park.hello()) // Hello! I'm student
```

Person이라는 부모 클래스를 생성하고, Person을 상속받는 Student 클래스를 생성했다.

상속은 `extends`키워드를 통해 받을 수 있다.

## Super / Override

### Super()

```js
class Person {
  name
  age

  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

class Student extends Person {
  major

  constructor(name, age, major) {
    super(name, age)
    this.major = major
  }
}

const park = new Student('Park', 25, 'Computer Engineer')
console.log(park)
```

자식 클래스에서 부모 클래스의 property에 값을 넣기 위해서는 생성자 메서드에 `super`키워드를 사용한다.

### Override

```js
class Person {
  name
  age

  sayHello() {
    return `Hi I'm ${this.name}!`
  }

  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

class Student extends Person {
  major

  sayHello() {
    return `Hi I'm ${this.name}! I major in ${this.major}`
  }

  constructor(name, age, major) {
    super(name, age)
    this.major = major
  }
}

const park = new Student('Park', 25, 'Computer Engineer')
console.log(park.sayHello()) // Hi I'm Park! I major in Computer Engineer
```

부모 클래스의 메서드를 재정의 하고 싶으면 동일한 이름의 메서드를 자식클래스에서 override하여 사용할 수 있다. 이 때, 부모 클래스의 property를 사용하고자 하면 super.name이 아닌 `this.name`으로 불러와야 한다.

그런데 한 가지 문제점이 있는데, 

```js
// Person
sayHello() {
  return `Hi I'm ${this.name}!`
}

// Student
sayHello() {
  return `Hi I'm ${this.name}! I major in ${this.major}`
}
```

부모 클래스의 메서드를 override 했지만, 여전히 return에는 중복된 문자열이 존재한다.

이럴 때는 `super`키워드를 사용하여 부모 클래스의 메서드를 불러올 수 있다.

```js
// Person
sayHello() {
  return `Hi I'm ${this.name}!`
}

// Student
sayHello() {
  return `${super.sayHello()} I major in ${this.major}`
}
```