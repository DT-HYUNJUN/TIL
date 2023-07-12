# Component

## Component란?

Component는 리액트에서 UI를 구성하는데 있어 핵심적인 개념이다. 간단하게 말하면 UI를 구분하는 하나의 `단위`라고 할 수 있다.

예를 들어 아래와 같은 article을 구성한다고 하자.
```html
<article>
  <h1>My First Component</h1>
  <ol>
    <li>Components: UI Building Blocks</li>
    <li>Defining a Component</li>
    <li>Using a Component</li>
  </ol>
</article>
```

지금처럼 한 번만 사용할 때는 문제가 되지 않지만, 만약 article을 여러번 사용해야 할 때는 위 코드를 여러번 사용해야 하는 번거로움이 발생한다.

따라서, 코드의 재사용성을 위해 article을 하나의 `Component`로 만들고 해당 `Component`를 불러와서 사용한다.

## Component 생성

`Component`를 생성하는 방법은 두 가지가 있다.

- 함수 Component
- 클래스 Component

### 함수 Component

```jsx
function MyComponent() {
  return (
    <div>
      <h1>This Is Function Component</h1>
    </div>
  )
}
```

Javascript에서 사용하듯이 함수로 Component를 생성하고, return을 통해 jsx 코드를 반환한다.

### 클래스 Component

```jsx
import React, { Component } from 'react'

class MyComponent extends Component {
  render() {
    return (
      <div>
        <h1>This Is Class Component</h1>
      </div>
    )
  }
}
```

클래스 Component는 React의 Component를 상속받아서 사용하기에 import를 통해 Component를 불러온다.

그리고는 `render()` 메서드를 통해 jsx코드를 return한다.