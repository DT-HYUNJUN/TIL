# 클래스

## 타입스크립트의 클래스

typescript 에서 클래스를 선언할 때는 타입을 함께 적어줘야 한다. 그렇지 않으면 암시적으로 any타입으로 추론된다.

```ts
class Employee {
  name: string
  age: number
  position: string

  constructor(name: string, age: number, position: string) {
    this.name = name
    this.age = age
    this.position = position
  }

  work() {
    console.log('working')
  }
}
```

### 상속

```ts
class Employee {
  name: string
  age: number
  position: string

  constructor(name: string, age: number, position: string) {
    this.name = name
    this.age = age
    this.position = position
  }

  work() {
    console.log('working')
  }
}

class ExecutiveOfficer extends Employee {
  officeNumber: number

  constructor(
    name: string,
    age: number,
    position: string,
    officeNumber: number
  ) {
    super(name, age, position)
    this.officeNumber = officeNumber
  }
}
```

super()를 사용해 부모클래스의 생성자를 호출한다.

## 접근 제어자

접근 제어자(Access Modifier)는 typescript에서만 제공하는 기능으로 클래스의 특정 필드나 메서드를 접근할 수 있는 범위를 설정하는 기능을 가진다.

- public : 모든 범위에서 접근 가능
- protected : 클래스 내부 또는 파생 클래스 내부에서만 접근 가능
- private : 클래스 내부에서만 접근 가능

### public

public은 따로 지정하지 않아도 기본값으로 public을 갖는다.

```ts
class Employee {
  name: string      // public
  age: number       // public
  position: string  // public

  constructor(name: string, age: number, position: string) {
    this.name = name
    this.age = age
    this.position = position
  }

  work() {
    console.log('working')
  }
}

const employee = new Employee('park', 26, 'dev')
employee.name = 'kim'
employee.age = 36
employee.position = 'design'
```

### protected

클래스 내부 또는 파생 클래스 내부에서만 접근 가능하다.

```ts
class Employee {
  public name: string    
  protected age: number     // protected
  public position: string

  constructor(name: string, age: number, position: string) {
    this.name = name
    this.age = age
    this.position = position
  }

  work() {
    console.log('working')
  }
}

class ExecutiveOfficer extends Employee {
  officeNumber: number

  constructor(
    name: string,
    age: number,
    position: string,
    officeNumber: number
  ) {
    super(name, age, position)
    this.officeNumber = officeNumber
  }

  func() {
    this.age   // 파생 클래스 내부에서 접근 가능
  }
}

const employee = new Employee('park', 26, 'dev')
employee.name = 'kim'
employee.age = 36             // 접근 불가
employee.position = 'design'
```

### private

클래스 내부에서만 접근 가능하다.

```ts
class Employee {
  private name: string      // private
  protected age: number
  public position: string

  constructor(name: string, age: number, position: string) {
    this.name = name
    this.age = age
    this.position = position
  }

  work() {
    console.log(`${this.name} working`)   // 클래스 내부에서 접근 가능
  }
}

class ExecutiveOfficer extends Employee {
  officeNumber: number

  constructor(
    name: string,
    age: number,
    position: string,
    officeNumber: number
  ) {
    super(name, age, position)
    this.officeNumber = officeNumber
  }

  func() {
    this.name   // 파생 클래스 내부에서 접근 불가능
    this.age
  }
}

const employee = new Employee('park', 26, 'dev')
employee.name = 'kim'   // 접근 불가
```

### 필드 생략

접근 제어자를 생성자 함수의 매개변수에 설정하면 자동으로 필드가 설정된다.

```ts
class Employee {
  constructor(
    private name: string,
    protected age: number,
    public position: string
  ) {}

  work() {
    console.log(`${this.name} working`)   // 클래스 내부에서 접근 가능
  }
}
```

## 인터페이스와 클래스

interface는 클래스의 설계도 역할을 할 수 있다.

```ts
interface CharacterInterface {
  name: string
  moveSpeed: number
  move(): void
}

class Character implements CharacterInterface {
  constructor(
    public name: string,
    public moveSpeed: number,
    private extra: string
  ) {}

  move(): void {
    console.log('')
  }
}
```