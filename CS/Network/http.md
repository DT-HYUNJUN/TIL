# HTTP / HTTPS

## HTTP (Hyper Text Transfer Protocol)

HTTP는 서버/클라이언트 모델을 따라 데이터를 주고 받기 위한 프로토콜이다.

80포트를 기본적으로 사용하고 있다.

HTTP는 응용 레벨의 프로토콜이기 때문에 TCP/IP 위에서 동작한다. 상태를 가지지 않은 Stateless 프로토콜이며 Method, Path, Version, Headers, Body 등으로 구성된다.

하지만 암호화가 되지 않은 평문 데이터를 전송하는 프로토콜이기 때문에 HTTP로 중요한 정보를 주고 받으면 제 3자가 정보를 조회할 수 있다.

## HTTPS (Hyper Text Transfer Protocol Secure)

HTTPS 는 HTTP에 데이터 암호화가 추가된 프로토콜이다.

443포트를 기본적으로 사용하며 제 3자가 정보를 조회할 수 없도록 암호화하여 전송한다.

SSL(보안 소켓 계층)을 이용해서 HTTP의 보안상 문제를 해결했으며 SSL은 서버와 브라우저 사이에 안전하게 암호화된 연결을 만들 수 있게 도와주고 서버 브라우저가 민감한 정보를 주고 받을 때도 도난당하는 것을 막아준다.