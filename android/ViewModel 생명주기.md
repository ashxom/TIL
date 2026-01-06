## ViewModel이란?
ViewModel은 UI(Activity/Fragment)가 살아있는 동안 데이터를 유지해주는 객체,
그래서 화면이 회전되어도 데이터가 안 날아감

## ViewModel 생명주기

ViewModel은 Activity/Fragment의 생명주기를 직접 따르지 않고, 해당 화면의 범위가 완전히 종료될 때까지 유지된다.

Activity 생성되면 ViewModel이 생성되고 
Activity가 종료되면 onCleared()가 호출되면서 끝남
