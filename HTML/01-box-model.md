# Box Model

## Box

### Box 구성

- margin : 현재 박스와 다른 요소 사이의 공백, 가장 바깥쪽 영역
- border : content와 padding을 감싸는 테두리 영역
- padding : content 주위에 위치하는 공백 영역
- content : content가 표시되는 영역

### Box 방향

위에서부터 시계 방향으로 top, right, bottom, left로 나눈다.

### Width & Height

요소의 너비와 높이를 지정한다.

이때 지정되는 요소의 너비와 높이는 content 영역을 대상으로 한다.

### Box-sizing

요소의 너비와 높이를 계산하는 방법을 지정한다.

- content-box: content영역으로 box-sizing을 조절한다.
- border-box: box 전체 영역으로 box-sizing을 조절한다.

## Box 타입

### Normal Flow

CSS를 적용하지 않았을 경우 Block 및 Inline 요소가 기본적으로 배치되는 방향을 말한다.

- Inline Direction : 좌 -> 우
- Block Direction : 상 -> 하

### Block

항상 새로운 행으로 나눈다.

width와 height 속성을 사용하여 너비와 높이를 지정할 수 있다.

기본적으로 width 속성을 지정하지 않으면 박스는 inline 방향으로 모든 공간을 차지한다.

대표적으로는 h1~6, p, div가 있다.

### Inline

새로운 행으로 나뉘지 않는다.

width와 height 속성을 사용할 수 없다.

수직 방향으로 다른 요소를 밀 수 없다.

수평 방향으로는 다른 요소를 밀 수 있다.