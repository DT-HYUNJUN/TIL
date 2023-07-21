# 새로 배운 것들

프로젝트를 하면서 javascript를 익혔기에 이번 기회에 제대로 배워보고자 inflearn 코드팩토리 강의를 들으면서 새롭게 알게 된 내용을 정리해 보았다.

## Operator

### 단항 더하기 (+)

피연산자 앞에 `+`를 붙이면 숫자로 변환을 시도한다.

```js
console.log(typeof +'100', +'100') // number 100

console.log(typeof +true, +true) // number 1

console.log(typeof +false, +false) // number 0

console.log(typeof +'hello', +'hello') // NaN
```

### parseInt() vs Number()

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

### Short Circuit Evaluation

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

### null 병합 연산자 (??)

좌측이 `null` 또는 `undefined` -> 우측 값 반환

```js
console.log(null ?? 'NCO')      // 'NCO'
console.log(undefined ?? 'NCO') // 'NCO'
console.log(0 ?? 'NCO')         // 0
console.log('' ?? 'NCO')        // ''
```

## Function