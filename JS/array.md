# Array

순서가 있는 데이터 집합을 저장하는 자료구조

## 배열의 구조

- []를 사용해 작성
- length를 사용해 배열의 길이를 알 수 있음
- 배열 요소의 자료형에는 제약이 없음

```javascript
const fruits = ["apple", "banana", "coconut",]

console.log(fruits[0]) // apple
console.log(fruits[1]) // banana
console.log(fruits[2]) // coconut

console.log(fruits.length) // 3
```

## 반복

```javascript
// for
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i])
}

// for...of
for (const fruit of fruits) {
  console.log(fruit)
}
```

## 메서드

|메서드|기능|역할|
|---|---|---|
push / pop|배열 끝 요소를 추가 또는 제거| 요소 추가/제거|
|uhshift / shift|배열 앞 요소를 추가 또는 제거|요소 추가/제거|
|forEach|인자로 주어진 콜백함수를 배열 요소 각각에 대해 실행|반복|
|map|배열 요소 전체를 대상으로 콜백함수를 호출하고, 함수 호출 결과를 배열로 반환|변형|

### pop

배열 끝 요소를 제거하고 반환

```javascript
console.log(fruits.pop()) // coconut
console.log(fruits) // ["apple", "banana"]
```

### push

배열 끝에 요소를 추가

```javascript
fruits.push("orange")
console.log(fruits) // ["apple", "banana", "orange"]
```

### shift

배열 앞 요소를 제거하고 반환

```javascript
console.log(fruits.shift()) // apple
console.log(fruits) // ["banana", "orange"]
```

### unshift

배열 앞에 요소를 추가

```javascript
fruits.unshift("melon")
console.log(fruits) // ["melon", "banana", "orange"]
```

### forEach

인자로 주어진 콜백함수를 배열 요소 각각에 대해 실행

```javascript
array.forEach(function (item, index, array) {
  // code
})
```

콜백함수는 3가지 매개변수로 구성
  1. item: 배열의 요소
  2. index: 배열 요소의 인덱스
  3. array: 배열

반환값: undefined

```javascript
const fruits = ["apple", "banana", "coconut"]

// function
fruits.forEach(function (item, index, array) {
  console.log(`${item} / ${index} / ${array}`)
})

// () =>
fruits.forEach((item, index, array) => {
  console.log(`${item} / ${index} / ${array}`)
})
```

### map

배열 요소 전체를 대상으로 콜백함수를 호출하고, 함수 호출 결과를 새로운 배열로 반환

기본적으로 forEach와 동작 원리는 같지만, map은 새로운 배열을 반환함

```javascript
const fruits = ["apple", "banana", "coconut"]

const result = fruits.map((fruit) => {
  return fruit.length
})

console.log(result) // [5, 6, 7]
```