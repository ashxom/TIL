# Bearer Token

### 개념

- Bearer Token은 서버가 로그인한 사용자에게 발급하는 인증용 토큰
- 사용자가 로그인하면 서버한테 인증된 사용자라고 증명하는 문자열을 줌
- 이후 앱은 API 요청할 때마다 이 토큰을 헤더에 포함시켜 보냄

### 동작과정

1. 사용자 로그인 요청

→ 아이디, 비밀번호 서버로 전송

1. 서버에서 계정 확인 후 Access Token 발급

→ 이게 Bearer Token 

1. 앱은 받은 토큰을 저장

→ SharedPreferences 등에 보관

1. 이후 요청마다 헤더에 포함시켜 전송

```vhdl
Authorization: Bearer [access_token]
```

1. 서버는 토큰을 보고 사용자 인증 여부 판단

### 왜 필요한가?

- 비밀번호를 계속 보내지 않아도 돼서 보안 강화
- 서버가 누가 요청했는지 쉽게 판단 가능
- 로그인하지 않은 사용자와 구분 가능

https://nulzi-dev.tistory.com/349
