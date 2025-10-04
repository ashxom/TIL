# 2025-05-22

`match_parent`/`wrap_content`는 **뷰의 크기를 어떻게 잡을지** 정하는 속성.

---

1. **`match_parent`**
    - 부모가 허용하는 **최대 크기만큼 꽉 채움**
    - 폼의 `EditText`/`Button` 가로, 구분선 `View`의 가로 등에 자주 씀
    
    ```xml
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    ```
    
2. **`wrap_content`**
    - **내용이 필요한 만큼만** 크기 차지
    - `TextView`, `ImageView` 같은 작은 요소에 자주 씀
    
    ```xml
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    ```
    

---

정리하면:

- **한 줄을 꽉** 채우고 싶다 → `width="match_parent"`
- **내용만큼만** 보이게 → `wrap_content`
- `ScrollView` 안 컨테이너 높이 → **`wrap_content`** (필요하면 `fillViewport="true"`로 빈 화면 없이)
