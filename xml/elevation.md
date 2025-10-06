# android:elevation

안드로이드에서 `android:elevation`은 뷰의 **Z축 높이(깊이) = 그림자/떠있는 느낌**을 정하는 속성임.

---

### 값에 따른 느낌

1. **`0dp` (기본 플랫)**
    - **그림자 없음**, 배경과 같은 평면
    
    ```xml
    android:elevation="0dp"
    ```
    
2. **`4dp` ~ `6dp` (살짝 떠 있음)**
    - 얕은 그림자, 상단바/카드에 자주 씀
    
    ```xml
    android:elevation="4dp"
    ```
    
3. **`8dp` 이상 (확실히 떠 있음)**
    - 진한 그림자, FAB·모달 등 강조 요소
    
    ```xml
    android:elevation="8dp"
    ```
    

---

정리하면:

- **값이 클수록 더 위에 떠 보이고 그림자 진해짐.**
- **겹칠 때는 elevation 큰 뷰가 위에 그려짐.**
- *API 21+**에서만 효과 있음.
- AppBar/Material 컴포넌트가 스크롤 시 자동으로 그림자 올리면 완전히 끄려면:
    
    ```xml
    app:liftOnScroll="false"
    android:stateListAnimator="@null"
    ```
    
- 단위는 **dp**
