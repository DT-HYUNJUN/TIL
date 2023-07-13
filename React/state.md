# State

## state란?

`state`는 `component`에서 쓰이는 어떠한 이벤트에 의해 변경되는 동적인 값을 말한다. [React Document]('https://react.dev/learn/state-a-components-memory')에서는 state를 `component's memory`라고 표현한다.

## state 사용하기 `useState`

함수형 component에서 state를 사용하기 위해서는 `useState Hook`을 사용한다.

문법은 아래와 같다.
```jsx
const [state, setState] = useState(initialState)
```

`state`는 현재 상태를 나타내고, `setState`는 state를 다루는 함수를 나타낸다.

즉 state를 변경하기 위해서는 setState 함수를 사용하여 변경해야 한다.

예를 들어 counter를 1씩 증가하는 state를 만들기 위해서는 아래와 같이 구성한다.

```jsx
// counter state를 0으로 초기화하고 counter를 다루는 setCounter함수를 생성
const [counter, setCounter] = useState(0)

// 첫 번째 방법
const addCounter = () => setCounter(counter + 1)

// 두 번째 방법
const addCounter = () => setCounter((prev) => prev + 1)

```
```html
<button onClick={addCounter}>버튼</button>
```

`counter` state와, `setCounter`를 만들고, 버튼에 `addCounter`이벤트를 붙인다.

`addCounter`는 `setCounter`를 통해 `counter`를 1씩 증가시킨다.

여기서 addCounter를 두 가지 방법으로 만들었다.

### 첫 번째 방법
```jsx
// A 방법
const addCounter = () => setCounter(counter + 1)
```

A 방법은 간단하게 `counter` state를 `setCounter`를 통해 1씩 증가시키는 방법이다.

### 두 번째 방법
```jsx
// B 방법
const addCounter = () => setCounter((prev) => prev + 1)
```

B 방법은 setCounter를 통해 counter state의 이전 값을 1씩 증가시키는 방법이다.

B 방법은 이전 상태 값을 기반으로 새로운 값을 업데이트 한다. 이렇게 하면 예기치 않은 동작이 발생하는 경우를 방지할 수 있다.

반면 A 방법은 현재 상태 값을 사용하여 업데이트를 하기 때문에 항상 안정적인 동작을 보장하지 않을 수 있다.

특히 비동기적인 업데이트나 여러 개의 상태 값이 연관되어 있는 경우, 예기치 않은 결과가 발생할 수 있다.