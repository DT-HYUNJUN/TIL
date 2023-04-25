# pseudo-class 가상 클래스

선택자 뒤에 `:가상이벤트`를 붙여서 특정 이벤트마다 적용할 스타일을 지정해줄 수 있다. 이를 가상 클래스라고 한다.

## 종류

대표적으로 쓰이는 가상 클래스는 다음과 같다.

- `:link` - 방문한 적이 없는 링크
- `:visited` - 방문한 링크
- `:hover` - 마우스 올렸을 때
- `:active` - 마우스 클릭할 때
- `:focus` - 포커스 될 때 (input등)
- `:first` - 첫 번째 요소
- `:last` - 마지막 요소
- `:first-child` - 첫 번째 자식
- `:last-child` - 마지막 자식
- `:nth-child()` - ()안에 식을 통한 자식 선택 ex) odd, even, 2n+1

```css
/* 마우스 올렸을 때 배경색 tomato로 지정 */
div:hover {
  background-color: tomato;
}
```

js를 사용하지 않아도 간단한 이벤트를 처리할 수 있다.

# pseudo-element 가상 요소

가상 클래스는 실제로 존재하는 요소에 디자인을 입힌 것이라면, 가상요소는 존재하지 않는 요소를 만들게 해준다. 선택자 뒤에 `::가상요소`를 붙여서 사용한다.

## 종류

- `::before` - 요소의 첫 번째 자식 요소를 생성
- `::after` - 요소의 마지막 자식 요소를 생성
- `::marker` - 목록 아이템 앞에 마커 선택
- `::first-letter` - 요소의 텍스트 컨텐츠 첫 글자 선택
- `::first-line` - 요소의 텍스트 컨텐츠 첫 줄 선택
- `::selection` - 마우스 드래그로 선택한 텍스트 컨텐츠 영역 선택

```css
/* 첫 글자 색 tomato로 지정 */
p::first-letter {
  color: tomato;
}
```
