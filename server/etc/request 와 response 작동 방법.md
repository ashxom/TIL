# 2025-08-29

## 1. HTTP 요청(Request)과 응답(Response)의 기본 원리

- **클라이언트 ↔ 서버 구조**:
    
    클라이언트(앱 또는 브라우저)가 서버에게 데이터를 요청(request)하고, 서버는 그에 대한 응답(response)을 보낸다. 
    
- **요청(request)은 보통 이렇게 구성**:
    - **Request Line**: HTTP 메서드(ex. GET, POST) + URI + 버전
    - **Headers**: 인증, 콘텐츠 형식, 쿠키 등 추가 정보
    - **Body (선택사항)**: POST/PUT 같은 요청 시 JSON 등 데이터
- **응답(response)은 이렇게 구성**:
    - **Status Line**: HTTP 버전 + 상태 코드(예: 200, 404) + 메시지
    - **Headers**: 콘텐츠 유형, 캐시 정책 등
    - **Body (선택사항)**: 서버가 보내는 데이터(ex. HTML, JSON 등)

## 2. 안드로이드에서 Retrofit으로 요청-응답 처리 흐름

- **Retrofit 역할**:
    
    HTTP 요청과 응답 요청을 추상화해 인터페이스로 쉽게 다룰 수 있게 도와주는 라이브러리
    

### 작동 방식 순서

1. **인터페이스 정의**
    
    ```java
    @POST("/auth/sign-in")
    Call<LoginResponse> signIn(@Body LoginRequest request);
    ```
    
2. **요청(Request)**
    - `LoginRequest(id, pw)` 객체가 JSON으로 변환되어 HTTP 요청의 **Body**에 담겨 전송됨
3. **서버 응답(Response)**
    - 서버가 JSON으로 `access_token`, `refresh_token` 등을 담아 응답하면,
    - Retrofit은 이를 `LoginResponse` 객체로 자동 매핑해줌
4. **서버 응답 핸들링**
    
    ```java
    call.enqueue(new Callback<LoginResponse>() {
      onResponse(...) { // 응답 있음
        // 성공 시 토큰 저장, 화면 전환
      }
      onFailure(...) { // 연결 자체 실패
        // 네트워크 문제 등
      }
    });
    ```
    
- 즉, `Request → 서버 → Response → Callback`으로 결과를 처리하는 흐름
- 그리고 Retrofit의 `Call` 객체는 요청 하나마다 **request-response 한 쌍**을 관계지어줌

## 정리

| 단계 | 설명 |
| --- | --- |
| **Request (요청)** | 클라이언트가 서버에 데이터 요청 (메서드, URL, headers, body 포함) |
| **Response (응답)** | 서버가 요청 처리 후 보내는 결과 (상태 코드 + 데이터 포함) |
| **Retrofit 사용** | Request/Response를 Java 객체로 추상화하여 쉽게 제어 가능 |
