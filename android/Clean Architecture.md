

### 클린 아키텍처란?

간단히 말하면, **추상화 개념'(Abstraction principle)’으로써 관심사를 분리시키고 의존도를 낮추는 것에 목적을 둔 아키텍처**이다. **코드를 층별로 구분해서, 서로 간섭하지 않게 만든 구조.**

기본적인 원리 :  **종속성 규칙(Dependency Rule)을 지키는 것.**

각 코드의 종속성은 외부에서 내부로 안쪽으로만 가리킬 수 있고, 고수준 정책이 저수준 정책의 변경에 영향을 받지 않도록 하는 것.

## 클린 아키텍처의 레이어 구조

![image.png](attachment:3a83462b-5ede-435c-824a-3e69508a6fb1:image.png)

(안쪽으로 갈수록 고수준, 바깥쪽으로 갈수록 저수준)

### Entities

- 의도에 따라 도메인 계층이라고 불림.
- 하나 이상의 프로젝트 간에 공유를 할 수 있다는 가정하에 만든 수명이 긴 객체
- 재사용될 가능성을 인지하고 외부에 의해 변경될 가능성을 낮춰야 함.
- Enterprise 규모의 비지니스 데이터를 포함하거나 핵심이 되는 비지니스 규칙을 캡슐화함.

### Use Cases

- 애플리케이션 계층이라고도 불리고 어플리케이션 규모의 비지니스 규칙을 포함함.
- 이 레이어의 변경사항은 Entities 에 영향을 미치면 안 됨.
- 인프라 단의 DB나 UI, 라이브러리와 같은 외부 요인에서 영향을 받지 않는다는 게 원칙임.

### **Interface Adapter**

- 어뎁터 계층은 DB나 Web, UI와 같은 바깥 계층에서 사용하기 편하도록 Entities나 Use Cases 계층에서 데이터를 변환하는 어뎁터의 집합.
- 흔히 **MVC**, **MVVM**과 같은 아키텍처를 포함하는 것이 이 영역으로 컨트롤러, 프레젠터, 게이트웨이 등이 속함.

### **Frameworks & Drivers**

- 인프라 계층이라고도 불리며, 가장 외부에 있는 레이어로 DB, 웹 프레임워크와 같은 세부 정보를 나타내는 계층.
- 보통 글루코드만 작성함.
- 시간에 따라 구성이 변경될 수도 있어서 Entities 계층에 추상화하여 도메인 계층에 영향 없이 인터페이스를 수정하고 업데이트 할 수 있음.

## **클린 아키텍처 (이론 in Android)**

![image.png](attachment:47c63714-56e3-4892-8e50-9d6d2d75c981:image.png)

클린 아키텍처는 자유도가 높은 편이기 때문에 위 핵심 규칙을 위반하지 않다는 가정하에 다양한 형태로 구현될 수 있음.

https://developer.android.com/topic/architecture?hl=ko

https://daryeou.tistory.com/280#google_vignette

https://vagabond95.me/posts/clean-architecture-1/

| 계층 | 하는 일 | 예시 |
| --- | --- | --- |
| **Presentation(UI)** | 사용자에게 보여주고 입력 받음 | Activity, Fragment, ViewModel |
| **Domain(Use Case)** | 앱의 “핵심 로직”을 담당 | “로그인 성공 시 토큰 저장” 같은 규칙 |
| **Data** | 외부 데이터 처리 (API, DB) | Retrofit, Room, Repository |
