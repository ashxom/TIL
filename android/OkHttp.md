# 2025-08-07


## OkHttp란?

OkHttp는 안드로이드 개발에서 인터넷을 통한 데이터 교환을 위해 널리 사용되는 오픈소스 HTTP 클라이언트 라이브러리이다.

## 주요 기능

1. HTTP/2 지원 : 여러 HTTP 요청을 동시에 처리할 수 있어 효율성을 높인다.
2. 연결 풀링 : 서버와의 연결을 재사용하여, 연결 시간을 줄이고 전체적인 네트워크 성능을 향상 시킨다.
3. GZIP 압축 : 네트워크를 통해 전송되는 데이터의 크기를 줄여, 데이터 사용량과 전송 시간을 절약할 수 있다.
4. 캐싱 : 자주 요청되는 데이터를 로컬에 저장하며, 서버에 대한 요청 수를 줄이고 빠르게 데이터를 로드할 수 있다.
5. 자동 재시도 및 리다이렉션 : 네트워크 오류나 3xx 응답 코드에 대해서 자동으로 처리한다.

## 코드 예시로 쉽게 보기

### 동기식 GET 요청

```java
OkHttpClient client = new OkHttpClient();
Request request = new Request.Builder()
    .url("https://example.com/data")
    .build();
Response response = client.newCall(request).execute();
String body = response.body().string();
```

### 비동기식 요청

```java
client.newCall(request).enqueue(new Callback() {
  @Override
  public void onFailure(Call call, IOException e) {
    // 실패 처리
  }

  @Override
  public void onResponse(Call call, Response response) throws IOException {
    // 응답 받았을 때 처리
  }
});
```

## 정리 

| OkHttp가 하는 일 | 설명 |
| --- | --- |
| 안전하고 빠름 | 캐시, 압축, 커넥션 풀링 덕분에 훨씬 효율적임 |
| 자동 복구 | 네트워크 문제도 자동으로 해결하려 노력함 |
| 쉽게 코드 작성 가능 | 동기/비동기, 요청 생성, 응답 처리 모두 깔끔함 |

OkHttp와 Retrofit은 각각의 장점이 있는 서로 다른 레벨의 라이브러리이며, 프로젝트의 요구 사항에 따라 선택하여 사용할 수 있다. 많은 안드로이드 개발자들은 이 두 라이브러리를 함께 사용하여 네트워크 통신의 효율성과 개발의 편리성을 동시에 높이고 있다.
