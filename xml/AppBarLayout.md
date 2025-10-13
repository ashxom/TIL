# AppBarLayout

`AppBarLayout`은 스크롤에 따라 **툴바(Toolbar)** 나 **탭(TabLayout)** 같은 상단 UI를

**펼치거나 접히게** 만들어주는 컨테이너임.

(보통 `CoordinatorLayout` 안에서 함께 사용)

---

### 언제 쓰나

- 스크롤 시 **툴바가 위로 숨고**, 아래로 내리면 다시 **나타나게** 하고 싶을 때
- **CollapsingToolbarLayout**과 함께 써서 큰 헤더가 **부드럽게 축소되는 효과** 만들 때
- 상단 영역(`Toolbar`, `TabLayout`)을 스크롤과 **동기화**하고 싶을 때

---

### 핵심 개념

- `app:layout_scrollFlags` : AppBar의 자식(예: Toolbar)이 스크롤될 때 **어떻게 반응할지** 설정
    - `scroll` : 스크롤 위로 올릴 때 함께 올라감
    - `enterAlways` : 아래로 내릴 때 바로 다시 나타남
    - `exitUntilCollapsed` : 일정 높이까지만 접히고 고정
    - `snap` : 접힘/펼침이 중간 없이 딱 맞게 멈춤
- `app:liftOnScroll="true"` : 스크롤 시 그림자(elevation) 효과 자동 추가
- `CoordinatorLayout`과 함께 써야 제대로 작동 (`appbar_scrolling_view_behavior` 필요)

---

### 최소 예제

```xml
<androidx.coordinatorlayout.widget.CoordinatorLayoutandroid:layout_width="match_parent"
    android:layout_height="match_parent">

    <com.google.android.material.appbar.AppBarLayoutandroid:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:liftOnScroll="true">

        <com.google.android.material.appbar.MaterialToolbarandroid:layout_width="match_parent"
            android:layout_height="wrap_content"
            app:layout_scrollFlags="scroll|enterAlways"
            android:title="App Bar Title"/>
    </com.google.android.material.appbar.AppBarLayout>

    <androidx.recyclerview.widget.RecyclerViewandroid:id="@+id/recyclerView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:layout_behavior="@string/appbar_scrolling_view_behavior"/>

</androidx.coordinatorlayout.widget.CoordinatorLayout>

```

---

### 팁 / 주의사항

- `scrollFlags`는 **AppBarLayout이 아니라 그 자식(Toolbar, CollapsingToolbarLayout)에 넣어야 함.
- `RecyclerView`나 `NestedScrollView` 등 **NestedScrollingChild**가 되는 뷰여야 함.
- AppBar가 스크롤되지 않게 하려면 `app:layout_scrollFlags="none"`
- 그림자 제거하고 싶으면 `app:liftOnScroll="false"` + `android:elevation="0dp"`

---

**정리:**

> AppBarLayout은 Toolbar, TabLayout 같은 상단 UI를 스크롤과 연동시켜
> 
> 
> 자연스럽게 **접히고 나타나는 상단 영역**을 만드는 컨테이너.
>
