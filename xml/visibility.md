안드로이드에서 `android:visibility`는 뷰(텍스트, 버튼, 레이아웃 등)를 **보이게 할지/숨길지** 정하는 속성임.

---

### visibility 종류 3가지

1. **`visible` (기본값)**
    - 뷰가 화면에 **보임**
    - 차지하는 영역도 그대로 있음.
    
    ```xml
    android:visibility="visible"
    ```
    
2. **`invisible`**
    - 뷰는 **안 보이지만**
    - 화면에서 **자리(공간)는 그대로 차지**함.
    
    ```xml
    android:visibility="invisible"
    ```
    
3. **`gone`**
    - 뷰가 **완전히 사라짐**
    - 화면에서 **자리도 차지하지 않음** → 레이아웃이 자동으로 재정렬됨.
    
    ```xml
    android:visibility="gone"
    ```
    

---

 정리하면:

- `visible` → 보이고 자리 있음
- `invisible` → 안 보이지만 자리 있음
- `gone` → 안 보이고 자리도 없음
