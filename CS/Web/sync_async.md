#  동기 / 비동기

##  동기

동기적인 작업은 순차적으로 진행되는 작업을 말한다. 한 작업이 시작하면 이 작업이 완료될 때까지 다음 작업은 대기해야 한다.

동기 작업은 작업의 순서와 실행이 예측 가능하며, 순차적으로 진행되기 때문에 코드가 간단하고 이해하기 쉽다.

하지만 하나의 작업이 끝나야 다른 작업을 수행해야 하기에 여러 작업을 동시에 처리하기 어렵다.

```js
function taskA() {
  console.log('task A')
}

function taskB() {
  console.log('task B')
}

taskA()
taskB()

// 출력 결과
// task A
// task B
```


  ## 비동기

비동기적 작업은 동시에 여러 작업을 처리할 수 있는 방식이다. 하나의 작업이 시작하면 다른 작업은 이를 기다리지 않고 동시에 진행된다.

비동기 작업은 콜백함수, Promise, Async/Await 등의 방식을 사용하여 구현한다.

```js
function taskA() {
  console.log('task A')
}

function asyncTaskB() {
  setTimeout(() => {
    console.log('async task B')
  }, 1000)
}

function taskC() {
  console.log('task C')
}

taskA()
asyncTaskB()
taskC()

// 출력 결과
// task A
// task C
// async task B (1초후)
```