# 2025-08-06

retrofit은 네트워크로 부터 전달된 데이터를 우리 프로그램에서 필요한 형태의 객체로 받을 수 있는 Httpclient 라이브러리입니다. 

Retrofit을 사용하는 기본 순서

 ### 1. 의존성 추가

`app/build.gradle`에 다음과 같이 작성:

```groovy
implementation 'com.squareup.retrofit2:retrofit:2.9.0'
implementation 'com.squareup.retrofit2:converter-gson:2.9.0'
```

### 2. 인터넷 권한 설정

AndroidManifest.xml:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

### 3.  데이터 모델 클래스 정의

서버의 JSON 구조를 반영한 클래스 만들기 (예: User, LoginResponse 등)

### 4. API 호출 인터페이스 작성

```java
public interface AuthService {
   @POST("/auth/sign-in")
   Call<LoginResponse> signIn(@Body LoginRequest body);
}
```

### 5. Retrofit 인스턴스 생성

```java
Retrofit retrofit = new Retrofit.Builder()
      .baseUrl("http://your.api.url/")
      .addConverterFactory(GsonConverterFactory.create())
      .build();

AuthService authService = retrofit.create(AuthService.class);
```

### 6. API 호출 실행

```java
authService.signIn(request).enqueue(new Callback<LoginResponse>() {
      @Override public void onResponse(...) { /* 성공 처리 */ }
      @Override public void onFailure(...) { /* 실패 처리 */ }
});
```
