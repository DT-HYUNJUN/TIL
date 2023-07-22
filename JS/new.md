# 📒**JS 노트**

프로젝트를 하면서 javascript를 익혔기에 이번 기회에 제대로 배워보고자 [inflearn 코드팩토리](https://www.inflearn.com/course/%EC%BD%94%EB%93%9C%ED%8C%A9%ED%86%A0%EB%A6%AC-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%ED%92%80%EC%BD%94%EC%8A%A4/dashboard) 강의를 들으면서 새롭게 알게 된 내용이나 중요한 내용들을 정리해 보았다.

## 📑**Index**

1. [Operator](#operator)
2. [Function](#function)
3. [Array](#array)

## 📌**Operator**

### **단항 더하기 (+)**

피연산자 앞에 `+`를 붙이면 숫자로 변환을 시도한다.

```js
console.log(typeof +'100', +'100')      // number 100

console.log(typeof +true, +true)        // number 1

console.log(typeof +false, +false)      // number 0

console.log(typeof +'hello', +'hello')  // NaN
```

### **parseInt() vs Number()**

`parseInt()`와 `Number()`는 둘 다 문자열을 숫자로 변환해준다.

하지만 동작하는 과정이 다르다.

`parseInt()`는 문자열을 `분석`하고 숫자로 변환한다. 만약 숫자로 시작하지 않으면 숫자로 변환 가능한 부분까지만 변환한다.

```js
parseInt('123')   // 123
parseInt('123px') // 123 (123 까지는 숫자로 변환하다가 p를 만나서 변환 중지)
parseInt('px123') // NaN (숫자로 시작하지 않아서 변환 실패)
```

`Number()`는 문자열이나 다른 타입을 숫자로 변환해준다. parseInt()보다 더 엄격하게 동작한다. 만약 문자열에 숫자가 아닌 타입이 들어있다면 변환되지 않는다.

```js
Number('123')   // 123
Number('123px') // NaN
Number('px123') // NaN
```

### **Short Circuit Evaluation**

- && : 좌측이 true -> 우측 값 반환
- && : 좌측이 false -> 좌측 값 반환
- || : 좌측이 true -> 좌측 값 반환
- || : 좌측이 false -> 우측 값 반환

```js
console.log(true && 'SCE')  // 'SCE'
console.log(false && 'SCE') // false
console.log(true || 'SCE')  // true
console.log(false || 'SCE') // 'SCE'

console.log(true && true && 'SCE')  // 'SCE'
console.log(true && false && 'SCE') // false
```

### **null 병합 연산자 (??)**

좌측이 `null` 또는 `undefined` -> 우측 값 반환

```js
console.log(null ?? 'NCO')      // 'NCO'
console.log(undefined ?? 'NCO') // 'NCO'
console.log(0 ?? 'NCO')         // 0
console.log('' ?? 'NCO')        // ''
```

## 📌**Function**

### **화살표 함수**

```js
const arr = x => y => z => `x: ${x}, y: ${y}, z: ${z}`
function arr2(x) {
  return function(y) {
    return function(z) {
      return `x: ${x}, y: ${y}, z: ${z}`
    }
  }
}
console.log(arr(1)(2)(3))   // x: 1, y: 2, z: 3
console.log(arr2(1)(2)(3))  // x: 1, y: 2, z: 3
```

### **arguments**

```js
const multiplyThree = function (x, y, z) {
  console.log(arguments)
  return x * y * z
}
console.log(muliplyThree(3, 4, 5))

// [Arguments] { '0': 3, '1': 4, '2': 5}
// 60
```

```js
const multiplyAll = function (...arguments) {
  return Object.values(arguments).reduce((a, b) => a * b, 1)
}
console.log(multiplyAll(1, 2, 3, 4, 5, 6)) // 120
```

### **IIFE (Immediately Invoked Function Expression)**

함수를 정의함과 동시에 실행한다.

```js
(function (x, y) {
  console.log(x * y)
})(4, 5);

// 20
```

## 📌**Array**

### **concat(element)**

`push()`와 같이 배열 맨 끝 자리에 요소를 추가하지만, 기존 배열을 조작하지 않고 `새로운 배열`을 반환한다.

```js
number = [1, 2, 3, 4, 5]
console.log(number.concat(6)) // [1, 2, 3, 4, 5, 6]
console.log(nunber)           // [1, 2, 3, 4, 5]
```

### **slice(start, end)**

배열의 `start index`부터 `end-1 index` 까지 잘라서 `새로운 배열`을 반환한다.

```js
number = [1, 2, 3, 4, 5]
console.log(number.slice(2, 4)) // [3, 4]
console.log(nunber)             // [1, 2, 3, 4, 5]
```

### **spread operator (...)**

배열의 요소들을 추출할 때는 배열앞에 `...`를 붙여서 추출한다.

```js
number = [1, 2, 3, 4, 5]
console.log(...number) // 1 2 3 4 5
```

`...`을 활용해서 새로운 배열을 만드는 것도 가능하다.

```js
number2 = [
  ...number,
]
console.log(number2) // [1, 2, 3, 4, 5]
```

이 때, 새롭게 생성된 배열은 기존 배열과 다른 메모리 주소를 가진다.

```js
console.log(number === number2) // false
```

### **sort()**

`sort()`는 배열의 요소들을 `유니코드를 기준`으로 오름차순으로 정렬한다. 원본 배열을 변경하며, 변경된 배열을 반환한다. 즉 `원본 배열 자체가 정렬`된다.

유니코드를 기준으로 정렬되기 때문에 정수 배열을 sort()로 정렬하게 되면 원하는 결과를 얻지 못할 수 있다.

```js
number = [1, 10, 2, 8, 25]
console.log(number.sort()) // [1, 10, 2, 25, 8]
```

따라서 숫자 배열을 오름차순으로 정렬하기 위해서는 `sort()`에 매개변수로 전달해야 한다.

```js
// 오름차순
number.sort((a, b) => a - b)

// 내림차순
number.sort((a, b) => b - a)
```

이렇게 되는 이유는

a, b를 비교할 때

- a를 b보다 뒤에 두려면 양수를 반환
- a를 b보다 앞에 두려면 음수를 반환
- 그대로 두려면 0을 반환

위 3가지 규칙을 따르기 때문이다.

### **map()**

`map()`은 배열 내의 모든 요소에 대하여 주어진 함수를 각각 실행한 결과를 `새로운 배열`로 반환한다.

```js
number = [1, 2, 3, 4, 5]
numberTimesTwo = number.map((x) => x * 2)
console.log(numberTimesTwo) // [2, 4, 6, 8, 10]
```

### **filter()**

`filter()`매서드 주어진 함수의 결과가 `true면 포함`시키고, `false면 제외`시켜서 `새로운 배열`을 반환한다.

```js
number = [1, 2, 3, 4, 5, 6]
evenNumber = number.filter((x) => x % 2 == 0)
console.log(evenNumber) // [2, 4, 6]
```

### **find()**

`find()`는 `filter()`와 마찬가지로 주어진 함수의 결과가 `true인 첫 번째 요소`를 반환한다.

```js
number = [1, 2, 3, 4, 5, 6]
evenNumber = number.filter((x) => x % 2 == 0)
console.log(evenNumber) // 2
```

### **reduce()**

`reduce()` 매서드는 배열의 각 요소들에 대해 주어진 함수를 실행시킨 결과값을 반환한다.

사용법은 아래와 같다.

```js
reduce(function, initialValue)
```

첫 번째 매개변수로는 `실행 할 함수`를, 두 번째 매개변수로는 `시작 값`을 넣는다.

만약 배열의 합을 구하기 위해서는 아래와 같이 코드를 짤 수 있다.

```js
number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
number.reduce((accumulator, currentValue) => accumulator + currentValue, 0)
```

`이 때 첫 시작은 accumulator에 initialValue를 넣고 시작한다. (0 + 1 + 2 + ... + 10)`

만약 initialValue에 1을 넣는다면 (1 + 1 + 2 + ... + 10) 처럼 작동하게 된다.

또 다른 예시로 배열 모든 요소의 곱을 구하기 위해서는

```js
number = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
number.reduce((accumulator, currentValue) => accumulator * currentValue, 1)
```

이 처럼 initialValue에 0이 아닌 1을 넣는다. 왜냐면 첫 시작에 accumulator에 initialValue가 들어가기에 0을 넣으면 (0 * 1 * 2 * ... * 10) 값이 0이 나오게 되기 때문이다.