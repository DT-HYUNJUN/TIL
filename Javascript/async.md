# Async 

Single Thread로 동작하는 Javascript에서 기존에 동기식으로 순서대로 코드가 진행되던걸 비동기식으로 코드가 진행되는것을 뜻한다.

## Promise

```js
const getPromise = (seconds) => new Promise((resolve, reject) => {
  setTimeout(() => {
    if (조건) {
      resolve('완료')
    } else {
      reject('에러')
    }
  }, seconds * 1000)
})

getPromise(3)
.then((res) => {
  console.log(res)
  // 완료
})
.catch((res) => {
  console.log(res)
  // 에러
})
.finally(() => {
  console.log('끝')
})

// (3초후...)
// 완료   <-- then()
// 끝     <-- finally()
```

Promise()에는 완료를 넘기는 resolve와 에러를 넘기는 reject인 두 개의 parameter가 들어간다.

만약 성공적으로 작업이 완료되면 '완료'를 resolve에 담고, 실패하면 '에러'를 reject에 담아서 보내준다.

getPromise(3)는, 성공할 때 실행되는 .then(), 실패할 때 실행되는 .catch(), 성공여부에 상관없이 항상 마지막에 실행되는 .finally()로 구성된다.

만약 Callback Hell 처럼 getPromise를 연속해서 실행하고 싶을때는 아래와 같이 구성한다.

```js
const getPromise = (seconds) => new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('완료')
  }, seconds * 1000)
})

getPromise(1)
.then((res) => {
  console.log('first then')
  console.log(res)

  // 다음에 불러올 getPromise
  return getPromise(2)
})
.then((res) => {
  console.log('second then')
  console.log(res)
})

// (1초후...)
// first then
// 완료
// (2초후...)
// second then
// 완료
```

똑같이 구성하되, 다음에 불러올 getPromise()를 return으로 불러오면 된다.

## async

위에서 사용한 Promise를 async를 사용해 간결하게 표현할 수 있다.

```js
const getPromise = (seconds) => new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('완료')
  }, seconds * 1000)
})

async function runner() {
  try {
    const result = await getPromise(3)
  } catch(e) {
    console.log(e)
  } finally {
    console.log('끝')
  }
}

// (3초후...)
// 완료
// 끝
```