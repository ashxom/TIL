### `android:clipToPadding="false"`

- 기본값은 `true`(= **패딩 안쪽으로만** 그리기).
- `false`로 두면, **패딩 영역까지 아이템이 그려질 수 있음**.
- 효과:
    - 리스트 맨 위/아래 아이템이 **패딩 영역까지 자연스럽게 보임**(페이드/그림자/에지 이펙트도 잘 보임).
    - 스크롤 글로우/오버스크롤 효과가 패딩 바깥으로 잘 표현됨.
- 자주 쓰는 조합:
    
    ```xml
    android:paddingTop="8dp"
    android:paddingBottom="8dp"
    android:clipToPadding="false"
    ```
    
    → 첫/마지막 아이템이 화면 모서리에 딱 붙지 않고 **여유 공간**이 생기면서도 깔끔하게 보임.
