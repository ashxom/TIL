# 안드로이드 디자인 패턴 (MVC, MVP, MVVM)

# MVC (Model–View–Controller)

- **아이디어**: `Activity`가 보통 View + Controller 역할까지 떠안음 → 코드가 뚱뚱해짐.
- **언제**: 연습용 초간단 앱 정도

```java
// Model
class UserRepo {
    boolean login(String id, String pw) {
        return "test".equals(id) && "1234".equals(pw);
    }
}

// Activity = View + Controller
public class LoginActivity extends AppCompatActivity {
    EditText etId, etPw; TextView tv;
    UserRepo repo = new UserRepo();

    protected void onCreate(Bundle b) {
        super.onCreate(b); setContentView(R.layout.activity_login);
        etId = findViewById(R.id.etId); etPw = findViewById(R.id.etPw); tv = findViewById(R.id.tv);
        findViewById(R.id.btnLogin).setOnClickListener(v -> {
            boolean ok = repo.login(etId.getText().toString(), etPw.getText().toString());
            tv.setText(ok ? "성공" : "실패");
        });
    }
}

```

---

# MVP (Model–View–Presenter)

- **아이디어**: `Activity`는 **View**만, 로직은 **Presenter**가 담당(인터페이스로 연결).
- **장점**: Activity 가벼움, 테스트 쉬움.
- **단점**: Presenter 비대해질 수 있음.

```java
// Model
class UserRepo {
    boolean login(String id, String pw) { return "test".equals(id) && "1234".equals(pw); }
}

// View 계약
interface LoginView {
    void showSuccess();
    void showError();
}

// Presenter
class LoginPresenter {
    private final LoginView view; private final UserRepo repo = new UserRepo();
    LoginPresenter(LoginView view) { this.view = view; }
    void onLogin(String id, String pw) { if (repo.login(id, pw)) view.showSuccess(); else view.showError(); }
}

// Activity = View
public class LoginActivity extends AppCompatActivity implements LoginView {
    EditText etId, etPw; TextView tv; LoginPresenter p;
    protected void onCreate(Bundle b) {
        super.onCreate(b); setContentView(R.layout.activity_login);
        etId = findViewById(R.id.etId); etPw = findViewById(R.id.etPw); tv = findViewById(R.id.tv);
        p = new LoginPresenter(this);
        findViewById(R.id.btnLogin).setOnClickListener(v -> p.onLogin(
            etId.getText().toString(), etPw.getText().toString()));
    }
    public void showSuccess(){ tv.setText("성공"); }
    public void showError(){ tv.setText("실패"); }
}

```

---

# MVVM (Model–View–ViewModel) 

- **아이디어**: `ViewModel`이 **상태(LiveData/Flow)**를 관리, `Activity`는 **관찰**만.
- **장점**: 결합도↓, 수명주기 안전, Jetpack 지원 좋음
- **언제**: 대부분의 실제 앱(특히 서버/DB/리스트 많은 앱).

```java
// Model
class UserRepo {
    boolean login(String id, String pw) { return "test".equals(id) && "1234".equals(pw); }
}

// ViewModel
public class LoginViewModel extends ViewModel {
    private final MutableLiveData<Boolean> loginResult = new MutableLiveData<>();
    private final UserRepo repo = new UserRepo();
    LiveData<Boolean> result() { return loginResult; }
    void login(String id, String pw) { loginResult.setValue(repo.login(id, pw)); }
}

// Activity = View(관찰자)
public class LoginActivity extends AppCompatActivity {
    EditText etId, etPw; TextView tv; LoginViewModel vm;
    protected void onCreate(Bundle b){
        super.onCreate(b); setContentView(R.layout.activity_login);
        etId = findViewById(R.id.etId); etPw = findViewById(R.id.etPw); tv = findViewById(R.id.tv);
        vm = new ViewModelProvider(this).get(LoginViewModel.class);
        vm.result().observe(this, ok -> tv.setText(ok ? "성공" : "실패"));
        findViewById(R.id.btnLogin).setOnClickListener(v -> vm.login(
            etId.getText().toString(), etPw.getText().toString()));
    }
}

```

---

## 요약

- **MVC**: 빠르게 만들긴 쉬운데 Activity가 비대해짐(연습용).
- **MVP**: 역할 분리 좋음, 인터페이스 설계 필요, Presenter 비대화 주의.
- **MVVM**: ViewModel+LiveData/Flow로 상태관리 깔끔, Jetpack과 궁합이 좋음


코드 : chatGPT
