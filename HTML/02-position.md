# Position

## CSS Position

기존에 Normal Flow에서 요소를 꺼내 다른 위치로 배치하는 것을 말한다.

## Position 유형

- static
- relative
- absolute
- fixed
- sticky

### Static

기본값으로 요소를 Normal FLow에 따라 배치한다.

### Relative

요소를 Normal Flow에 따라 배치하고, 자기 자신을 기준으로 이동한다.

요소가 차지하는 공간은 static과 동일하다.

### absolute

요소를 Normal Flow에서 제거하고, 가장 가까운 relative 부모 요소를 기준으로 이동한다.

문서에서 요소가 차지하는 공간이 없어진다. (밑에 요소가 현재 공간을 차지)

### fixed

요소를 Nomal Flow에서 제거하고, 현재 화면영역(viewport)을 기준으로 이동한다.

문서에서 요소가 차지하는 공간이 없어진다. (밑에 요소가 현재 공간을 차지)

### sticky

요소를 Normal Flow에 따라 배치하고, 가장 가까운 block 부모 요소를 기준으로 이동한다.

요소가 특정 위치(상단에서부터 10px)에 스크롤될 때 그 위치에 고정된다(fixed).

그리고 만약에 다른 sticky요소를 만나면 그 sticky 요소가 이전 sticky 요소의 자리를 대체한다(겹치기 때문).

## Z-index

정수 값을 사용해 Z축 순서를 지정한다.

더 큰 값을 가진 요소가 작은 값의 요소를 덮는다.