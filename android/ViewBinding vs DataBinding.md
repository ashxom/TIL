# 2025-08-15

## ViewBinding과 DataBinding의 차이

### 정리

| 구분 | 뷰 바인딩(ViewBinding) | 데이터 바인딩(DataBinding) |
| --- | --- | --- |
| 역할 | XML 레이아웃의 뷰를 코드에서 안전하게 접근할 수 있게 함 (findViewById 대체) | 뷰 바인딩 기능 플러스, 데이터와 뷰를 직접 연결 |
| XML 필요 태그 | `<layout>` 없음 | `<layout>` 루트 + `<data>` 영역 필요  |
| 인플레이션 방식 | 코드에서 `inflate()` + `getRoot()` 사용  | `DataBindingUtil.setContentView()` 또는 `<layout>`로 시작하여 자동 생성된 바인딩 클래스 사용 |
| 자동 UI 업데이트 | 없음 — UI 업데이트는 코드에서 직접 해야 함 | 가능 — 변수 변경 시 XML 뷰가 자동으로 업데이트됨 (양방향 바인딩 가능)  |
| 빌드 속도 | 빠름 (어노테이션 프로세싱 없음)  | 느림 (어노테이션 프로세싱 때문에)  |
| 적합한 경우 | 단순 뷰 접근이 필요한 경우, 빠르고 가볍고 안전하게 UI 다루고 싶을 때 | MVVM 구조, 라이브 데이터 연동, UI와 데이터 자동 동기화 필요할 때 |

### 위키백과 같은 설명(공식 기준)

- **ViewBinding**: XML에 ID를 가진 뷰를 타입 안전하고 널 세이프하게 코드에서 바로 사용할 수 있게 binding 클래스를 자동 생성해 줌.
- **DataBinding**: 뷰와 데이터를 XML에서 직접 연결하도록 해주는 더 강력한 기능. 변수 바인딩, 표현식, 양방향 바인딩, Observable 연동, BindingAdapter까지 지원.

### 결론적으로

- **뷰 바인딩 (ViewBinding)**: 단순하고 빠르고 안전하게 뷰를 참조하는 용도. 복잡한 구조가 필요 없을 때 추천.
- **데이터 바인딩 (DataBinding)**: XML에서 코드-데이터 연결을 직접 작성하고, 자동 UI 업데이트 + MVVM용. 조금 무겁지만 기능은 강력.

프로젝트가 작고 간단하면 **ViewBinding만으로 충분하고**, UI와 데이터 자동 연동→ **DataBinding이 더 편할 수 있음.**

바인딩은 XML 뷰를 코드와 연결해주는 기술이고, ViewBinding은 findViewById 없이 안전하게 뷰에 접근할 수 있게 해주는 방식입니다. DataBinding은 여기에 데이터까지 XML에서 직접 처리할 수 있는 확장된 버전입니다.
