# DOM

## DOM의 개념

웹페이지(Document)를 구조화된 객체로 제공하며 프로그래밍 언어가 웹 페이지를 사용할 수 있게 연결한다.

브라우저는  HTML문서를 해석하여 DOM tree라는 객체의 트리로 구조화 한다.

document
- html
  - head
    - title
  - body
    - h1
    - a

## DOM Query 선택

하나의 요소를 선택하는 방법과 여러 요소를 선택하는 방법이 있다.


```javascript
// 요소 하나 선택
document.querySelector()

// 여러 요소 선택
document.querySeletorAll()
```

document.querySelector(selector)
  - selector와 일치하는 하나의 element 선택
  - 만족하는 selector가 여러개라면 첫 번째 element 반환 (없으면 null)

document.querySeletorAll(selector)
  - seletor와 일치하는 여러 element 선택
  - seletor를 만족하는 NodeList 반환

## DOM Manipulation 조작

### attribute 조작

`classList` 속성
  - 요소의 class 목록을 DOMTokenList 형태로 반환한다.
  - add(), remove() 메서드를 사용하 조작할 수 있다.

```javascript
const h1Tag = document.querySeletor('h1')
h1Tag.classList.add('added_class')
h1Tag.classList.remove('added_class')
```

`일반` 속성

element.getAttribute()
  - 해당 요소에 지정된 값을 반환한다.

element.setAttribute()
  - 지정된 요소의 속성 값을 설정한다.
  - 이미 존재하는 속성이면 값을 업데이트, 아니면 추가

element.removeAttribute()
  - 요소에서 지정된 이름을 가진 속성 제거

`textContent` 속성
  - element의 텍스트 콘텐츠를 표현

```HTML
<h1>Heading</h1>
```

```javascript
const h1Tag = document.querySeletor('h1')
h1Tag.textContent = 'Heading_changed'
```
