# xml 주요 레이아웃의 종류는?
LinearLayout, ConstraintLayout, RelativeLayout, FrameLayout 등이 있다.

### LinearLayout

- 가로 혹은 세로로 순차적으로 쌓아가는 레이아웃임.
- android:oritation = vertical or horizontal

### ConstraintLayout

- 자식 view들에게 제약을 줘서 부모 view 기준으로 위치를 정하거나 다른 view들을 지정할 수 있는 레이아웃임.
- 각 view 크기를 유연하게 지정할 수 있는 레이아웃.
- 구글이 권장하는 레이아웃이고 xml 기본적으로 생성할 때 적용되어 있음.

### RelativeLayout

- 상대적으로 위치를 지정해주는 레이아웃.
- 부모 뷰인 RelativeLayout 으로 위치를 지정하거나, 다른 view 자식들을 기준으로 위치를 지정할 수 있음.

### FrameLayout

- 한 가지 뷰를 보여줄 때 사용함.
- 여러 개의 뷰를 중첩시킬 수 있기 때문에 여러 개의 뷰를 중첩한 후에 android:visivility 를 설정하여 한 가지 뷰만 visible 처리하여 보여주는 방식으로 사용함.
- 근데 ConstraintLayout으로도 중첩이 가능함
