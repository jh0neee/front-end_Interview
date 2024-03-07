## CORS(Cross-Origin Resource Sharing)

CORS는 **교차 출처 리소스 공유**를 뜻한다.

브라우저는 보안상의 이유로 출처가 다른 서버와 통신하는 것을 막는데,
이를 SOP(Same-Origin Policy)라고 한다.

반대로 CORS는 서로 다른 출처라도 리소스 요청, 응답을 허용할 수 있다.
`CORS를 설정한다`는 **출처가 다른 서버 간의 리소스 공유를 허용**한다는 것

이때, 출처가 다르다는 것은 프로토콜, 도메인, 포트 중 하나라도 다른 경우를 의미한다.

- 프로토콜(Protocol) : `https`
- 도메인(Hostname) : `billim.store`
- 출처(Origin) : `https://billim.store`

<br/>

서버와 클라이언트가 분리되어 있거나 다른 웹서비스를 사용할 때 CORS 에러가 뜨는데, CORS가 가능하도록 설정하면 된다.

- 요청한 서버와 출처(프로토콜, 도메인, 포트)가 같은지 확인 - SOP 준수
- 서버에서 응답하고 있는 헤더를 확인
  - 서버에서 Access-Control-Allow-Origin 헤더 설정
- 프록시 서버
