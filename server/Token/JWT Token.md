# 2025-08-02

## JWT 토큰이란?

JWT(Json Web Token)은 Json 객체에 인증에 필요한 정보들을 담은 후 비밀키로 서명한 토큰으로, 인터넷 표준 인증 방식이다. 공식적으로 **인증(Authentication) & 권한허가(Authorization)** 방식으로 사용된다.

## JWT 프로세스

(로그인 전)

1. 사용자가 아이디와 비밀번호 혹은 소셜 로그인을 이용하여 서버에 **로그인 요청**을 보낸다.
2. 서버는 **비밀키**를 사용해 json 객체를 암호화한 **JWT 토큰**을 발급한다.
3. JWT를 **헤더**에 담아 클라이언트에 보낸다.

(로그인 후)

1. 클라이언트는 JWT를 **로컬에 저장**해놓는다.
2. **API 호출**을 할 때마다 **header에 JWT를 실어 보낸다**.
3. 서버는 **헤더를 매번 확인**하여 **사용자가 신뢰할만한지**하고, 인증이 되면 API에 대한 응답을 보낸다.

## JWT의 구조

JWT는 Header, Payload, Signature 3개로 구성되어 있다.

### Header

- alg : Signature에서 사용하는 알고리즘
- typ : 토큰 타입

Signature에서 사용하는 알고리즘은 대표적으로 `RS256`(공개키/개인키)와 `HS256`(비밀키(대칭키))가 있다. 이 부분은 [auth0](https://auth0.com/docs/get-started/applications/signing-algorithms) 공식 문서에서 자세히 설명해주고 있다.

### Payload

사용자 정보의 한 조각인 클레임(claim)이 들어있다.

- sub : 토큰 제목(subject)
- aud : 토큰 대상자(audience)
- iat : 토큰이 발급된 시각 (issued at)
- exp : 토큰의 만료 시각 (expired)

### Signature

Signature는 헤더와 페이로드의 문자열을 합친 후에, **헤더에서 선언한 알고리즘과 key를 이용해 암호한 값**이다.

Header와 Payload는 단순히 [Base64url](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URLs)로 인코딩되어 있어 누구나 쉽게 복호화할 수 있지만, Signature는 key가 없으면 복호화할 수 없다. 이를 통해 **보안상 안전하다**는 특성을 가질 수 있게 되었다.

## 정리

- 사용 목적 : JWT 토큰은 사용자 인증과 로그인 유지를 위해 쓰인다
- 토큰의 구조 : Header, Payload, Signature
    - Header: 서명 알고리즘 (공개키/개인키 or 비밀키)
    - Payload : 토큰 정보(대상, 발급시각, 만료시각)
    - Signature : (Header+Payload) 서명 (인증용)
- 장단점
    - 장점 : 네트워크 부하가 적고 모바일 앱에 사용하기 적합하다
    - 단점 : 토큰 크기를 신경써야하고, 만료 기간 처리를 따로 해줘야한다
