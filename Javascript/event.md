# Event

무언가 일어났다는 신호, 사건
(모든 DOM 요소는 이러한 신호를 만들어 냄)

DOM 요소는 event를 받고, 받은 event를 처리할 수 있음

## event handler

이벤트가 발생했을 때 실행되는 함수

### .addEventListener()

대표적인 이벤트 핸들러 중 하나

EventTarget.addEventListener(type, handler)

```javascript
const btn = document.querySelecotr('#btn')

btn.addEventListener('click', (event) => {
  console.log(event.target)
})
```

event.target을 활용해 원하는 값을 선택

### .preventDefault()

현재 Event의 기본 동작을 중단