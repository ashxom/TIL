# Markwon이란?
 Markwon = 안드로이드에서 Markdown / HTML을 TextView에 문서처럼 렌더링해주는 라이브러리

특징을 정리하면

- `# 제목`, `*굵게**`, 리스트, 코드 블럭 같은 마크다운 문법 지원
- `<p>`, `<a>`, `<ul>`, `<li>`, `<img>` 같은 HTML 태그도 함께 지원
- `<a href>` 링크 클릭 가능
- `<img src>` 이미지를 자동으로 로딩 (plugin 사용)
- `<li class="task-list-item checked">` 같은 체크박스 리스트도 표현 가능

### 1. Gradle 설정

**1) 모듈 build.gradle에 의존성 추가**

```
dependencies {
    implementation ("io.noties.markwon:core:4.6.2")
    implementation ("io.noties.markwon:html:4.6.2")
    implementation ("io.noties.markwon:image:4.6.2")
}
```

버전은 상황에 따라 업데이트 가능.

### 2. 가장 기본 사용 방법

(게시글 상세 화면에서 서버에서 문자열을 받아왔다고 가정)

```
String content = postDetailResponse.getContent();
```

서버에서 받아온 본문 (HTML 포함 문자열)

**(1) Markwon 인스턴스 만들기**

보통 Activity 나 Fragment 안에서 한 번만 만들어서 재사용

```
Markwon markwon = Markwon.builder(this)
        .usePlugin(HtmlPlugin.create())          // HTML 태그 지원
        .usePlugin(ImagesPlugin.create(this))    // <img> 태그 이미지 로딩
        .build();
```

**(2) TextView에 렌더링**

```
TextView tvContent = findViewById(R.id.tvContent);
markwon.setMarkdown(tvContent, content);
```

이 두 줄로 끝
