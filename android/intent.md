### 인텐트란?

앱에서 컴포넌트한테 무슨 행동을 할지 전달하는 것.

### 필요한 이유

- 안드로이드는 컴포넌트끼리 부르지 못함.
- 그래서 데이터를 열어주거나 화면 열어주라는 걸 intent로 부탁하는 구조임.

### 인텐트에 들어가는 것들

- 누가 할지 → 어떤 activity / 어떤 앱
- 뭘 할지 → action (보기, 공유하기, 전화 등)
- 데이터 → extra, uri 등

### 명시적 인텐트

이 activity 를 실행하라고 정확히 찍어줌.

ex)

```java
Intent intent = new Intent(this, MainActivity.class);
startActivity(intent);
```

= MainActivity 실행해

**언제 사용**

- 앱 내부 화면 이동
- 로그인 → 메인
- 리스트 → 상세 화면

**특징 정리**

- 같은 앱 안에서 사용
- 대상이 명확함
- 빠르고 안정적임

### 암시적 인텐트

이 행동을 할 수 있는 앱 아무나 나오라고 하는 것.

ex)

```java
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("https://www.google.com"));
startActivity(intent);
```

= 이 URL 볼 수 있는 앱 아무거나 실행해 (크롬, 사파리, 인터넷 등 하나 뜸)

**언제 사용**

- 전화 걸기
- 웹 열기
- 사진 공유
- 카메라 실행
