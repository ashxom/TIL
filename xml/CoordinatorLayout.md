# CoordinatorLayout

안드로이드에서 `CoordinatorLayout`은 자식 뷰들의 **스크롤/위치/애니메이션을 서로 연동**시켜주는 컨테이너임. (강화된 `FrameLayout` 느낌)

### 언제 쓰나

- **툴바 접힘/펼침**: `AppBarLayout` + 스크롤 목록 연동
- **FAB·스낵바 상호작용**: 스낵바 뜨면 FAB가 자동으로 위로 이동
- 스크롤에 맞춰 **숨기기/고정/이동** 같은 행동(Behavior) 쉽게 적용

### 핵심 개념

- `app:layout_behavior` : 자식에게 어떻게 반응할지 규칙 부여
- `app:layout_anchor` / `app:layout_anchorGravity` : 다른 뷰 기준 고정(FAB 등)
- 목록 쪽에는 `@string/appbar_scrolling_view_behavior`를 달아 AppBar와 연동

### 최소 예제

```xml
<androidx.coordinatorlayout.widget.CoordinatorLayoutandroid:layout_width="match_parent"
    android:layout_height="match_parent">

    <com.google.android.material.appbar.AppBarLayoutandroid:layout_width="match_parent"
        android:layout_height="wrap_content">

        <com.google.android.material.appbar.MaterialToolbarandroid:layout_width="match_parent"
            android:layout_height="56dp" />
    </com.google.android.material.appbar.AppBarLayout>

    <androidx.recyclerview.widget.RecyclerViewandroid:id="@+id/rv"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_behavior="@string/appbar_scrolling_view_behavior"/>

    <com.google.android.material.floatingactionbutton.FloatingActionButtonandroid:layout_width="56dp"
        android:layout_height="56dp"
        app:layout_anchor="@id/rv"
        app:layout_anchorGravity="bottom|end"/>
</androidx.coordinatorlayout.widget.CoordinatorLayout>

```

### 팁/주의

- `android:elevation`으로 레이어(그림자) 우선순위 조절 가능
- AppBar 그림자 없애려면 `android:elevation="0dp"` (+ 필요 시 `app:liftOnScroll="false"`)
- Behavior는 커스텀도 가능하지만, 대부분은 기본 제공으로 충분

**정리:** “툴바·FAB·스낵바·스크롤”이 같이 놀아야 하면 `CoordinatorLayout`이 답.
