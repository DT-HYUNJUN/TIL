# C. 앱 개발자 공통 기술 질문: 5개 이상 잘 대답할 수 있어야 함

## PNG와 JPG의 차이점은?

### PNG

`Portable Network Graphics`의 약자로, `압축이 가능`하며 1600만개의 색상을 처리할 수 있다.

하지만 JPG 보다 저장 공간을 더 많이 차지하기 때문에, 고품질 사진보다는 `로고`, `웹 그래픽`, `차트` 등에 쓰인다.

또한 JPG와는 다르게 `투명한 배경`이 있는 그래픽을 처리할 수 있다.

### JPG

Joint Photographic Experts Groupd의 약자로, `압축`을 통해 이미지 `파일의 크기를 줄여서 저장`하고, 웹 페이지에 쉽게 업로드 할 수 있게 한다.

### 차이점

|| PNG | JPG |
|---|---|---|
| 압축 | 무손실 | 손실 |
| 파일 크기 | 크다 | 작다 |
| 투명도 조정 | O | X |

## Dynamic Programming이란?

`Dynamic Programming`이란 `큰 문제를 작은 문제로 나누어 푸는 문제`를 일컫는 말이다.

분할 정복이랑 흡사한 면이 있지만 결정적인 차이점이 있다.

분할 정복은 단순히 `큰 문제를 작은 문제로 쪼개어서 푸는 방법`이지만

동적프로그래밍은 `작은 부분문제들이 반복되는 것을 이용하여 푸는 방법`이다.

## Virtual Memory란?

`가상메모리`는 `실제 메모리보다 더 큰 프로세스의 실행`을 가능케 하는 메모리 관리 기법이다.

일반적으로 가상 메모리를 지원하는 시스템에서는 디스크와 같은 `보조 기억 장치`의 일부분을 마치 실제 메모리처럼 활용한다.

프로세스의 `전체 주소공간`은 `가상 메모리에 유지`하면서 프로세스 `실행에 필요한 부분`만을 `실제 메모리에 적재`시킴으로써 프로세스를 실행시킨다.

따라서 사용자는 실제 메모리보다 `더 큰 메모리가 존재하는 것처럼` 느끼게 된다.

이 때, `가상 메모리 주소공간`과 `실제 메모리 주소공간`이 `서로 다름`을 유의해야 한다.

가상 메모리 기법은 `실제 메모리보다 더 큰 프로세스를 실행`시킬 수 있는 장점이 있다.

하지만 프로세스의 일부만이 실제 메모리에 적재된 상태에서 프로세스가 실행되기 때문에 프로세스의 `실행 속도가 저하`되는 단점이 있다.

따라서 가상 메모리를 효과적으로 관리하기 위해서는 `반입 정책`, `교체 정책`, `할당 정책`을 고려해야 한다.

## Garbage Collection이란?

### Garbage

`변수를 선언`하면 메모리에 `저장 공간이 할당`되는데, 처음 그 안에는 어떤 값이 들어있는지 알 수 없다.

왜냐하면 하나의 프로그램이 사용하던 `메모리 공간은` 프로그램 종료 후 새로 실행되는 프로그램에 `재활용` 되기 때문이다.

그러기에 이전에 실행하던 프로그램이 메모리에 어떤 값을 남겨 놓았을지 알 수 없다.

그 메모리 안에 어떠한 값이 들어있든, `새로 실행되는 프로그램 입장`에서는 `쓰레기값(Garbage)`과 마찬가지로 의미가 없다.

### Garbage Collection

C, C++에서는 이러한 Garbage들을 `수동으로 할당과 해제`를 해야했다.

하지만 Java같은 경우는 Garbage들을 처리하는 `메모리 관리 기법`이 존재한다.

`Garbage Collection`은 Java의 메모리 기법 중 하나로 `JVM(Java Virtual Machine)의 Heap 영역`에서 `동적으로 할당된 메모리 영역 중 쓸모 없게된 영역을 주기적으로 삭제하는 프로세스`를 말한다.

덕분에 개발자는 메모리 문제에 대해 완벽하게 관리하지 않아도 되는 장점이 있다.

## Cache란?

`Cache Memory`는 메인 메모리와 CPU간의 데이터 속도 향상을 위한 중간 버퍼 역할을 하는 CPU내 또는 외에 존재하는 메모리이다.

`반복적으로 데이터를 불러오는 경우`에 매번 서버에 요청하는 것이 아니라 `메모리에 데이터를 저장`했다가 불러다 쓰는 것을 말한다.

## Database Index 추가의 장단점은?

DB index란 DB에서 테이블의 `검색 성능`을 높여주는 방법이다.

### 장점

원하는 데이터를 `빠르게 찾을 수 있기`에 전반적인 시스템의 부하를 줄일 수 있다.

### 단점

index는 SELECT를 제외한 모든 동작(INSERT, UPDATE, DELETE)에 `영향`을 미친다.

왜냐하면 위 동작들로 인해 index가 바뀌면 index 테이블의 수정도 필요하기 때문에 작업이 `두 번` 이루어 지기 때문이다.

또한 DB에 저장된 데이터의 주소를 인덱스의 key값으로 가지려면 `별도의 저장공간`이 필요하다.

## 비대칭 암호화란?

비대칭 암호화는 `공개키 암호화`라고도 알려져 있다. `공개 키`와 `개인 키`, 두 개의 `개별 암호화 대칭 키`를 사용하여 데이터를 암호화 및 해독한다.

`RSA`방식을 많이 사용한다.

## HDD, SSD, DRAM 각각의 성능은?

### HDD

`기계식 디스크`로 데이터를 저장한다.

플래터 위에 자기 헤드가 움직이면서 데이터를 읽고 쓰기에 `데이터 액세스 속도가 상대적으로 느리다`.

### SSD

`반도체 기반`으로 데이터를 저장한다.

기계적 부품이 없기에 기계적인 움직임이 없고 `데이터 액세스가 빠르다`.

### DRAM

`주기억장치`로 사용되는 `반도체 기반`의 메모리다.

`빠른 데이터 액세스 속도와 높은 처리 속도`를 제공한다. `비휘발성 메모리`기에 전원이 꺼지면 데이터가 사라진다.


## GIT의 장점은?

`분산 버전 관리 시스템`인 Git은 여러 장점을 가지고 있다.

Git을 사용하는 `전체 개발 내역`을 각 개발자의 로컬 컴퓨터로 `복사`할 수 있고, 각각의 작업내용을 `합칠수도 있다`.

또한 작업된 모든 내역들을 별도의 영역에서 관리되기에 안전하게 프로젝트를 운영할 수 있다.