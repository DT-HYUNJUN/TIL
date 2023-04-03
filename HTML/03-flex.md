# Flex

요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식

## Flexbox

main(가로) 축을 기준으로 왼쪽이 start, 오른쪽이 end

cross(세로) 축을 기준으로 위쪽이 start, 아래쪽이 end로 진행된다.

또한 flex container에는 1차 자식 요소들이 flex item이 된다.

```html
<div id="flex-container">
  <div id="first-child">
    <div id="second-child">
    </div>
  </div>
</div>
```

#flex-container 의 1차 자식인 #first-child는 flex 속성값으로 배치되지만, #second-child는 영향을 받지 않는다.

## 속성

### Flex Container 속성

- 배치 설정
  - flex-direction
  - flex-wrap
- 공간 분배
  - justify-content
  - align-items
- 정렬
  - align-items
  - align-self

### Flex Item 속성

align-self, flex-grow, flex-shrink, flex-basis, order