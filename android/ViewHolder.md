만약 스크롤 가능한 리스트가 있다고 치고 카톡 채팅이 있다고 하면 화면에 한 번에 보이는 아이템은 대략 8개 정도가 있음.

→ 근데 데이터는 100개~1000개가 될 수 있음

아무 생각 없이 만들면 생기는 문제

스크롤할 때마다

1. 아이템 View를 새로 만들고
2. findViewById()를 생성하고
3. 다시 화면에 붙임

이걸 반복하게 된다면? → 느려짐, 스크롤 끊김, 렉 걸림

## ViewHolder란?

아이템 View 안의 하위 View들을 미리 저장해두는 객체.

ViewHolder가 없다면?

```java
textView = findViewById(R.id.text);
imageView = findViewById(R.id.image);
```

이걸 스크롤할 때마다 계속 실행하게 됨

ViewHolder가 있으면

```java
class ViewHolder {
    TextView text;
    ImageView image;
}
```

- 처음 한 번만 findViewById()
- 그 다음부터 꺼내쓰면 됨

## ListView에서 ViewHolder

ListView는 View를 자동으로 재활용하지만 

ViewHolder는 개발자가 직접 써야 함.

```java
if(converView == null) {
		converView == inflater.inflate(...);
		holder = new ViewHolder();
		holder.text = convertView.findViewById(...);
		converView.setTag(holder);
} else {
		holder = (ViewHolder) convertView.getTag();
		}
```

안 쓰면 ListView는 성능 박살됨

## RecyclerView에서 ViewHolder

RecyclerView는 ViewHolder 사용이 구조 자체에 포함됨

```java
class MyViewHolder extends RecyclerView.ViewHolder {
	TextView text;
}
```

- ViewHolder 무조건 써야 함
- View 재활용 + 데이터 바인딩 분리
- 성능 최적화 자동

→ RecyclerView는 ViewHolder가 강제임

## 비교

| 구분 | ListView | RecyclerView |
| --- | --- | --- |
| View 재사용 | O | O |
| ViewHolder | 선택 | 필수 |
| 성능 | 보통 | 좋음 |
| 구조 | 단순 | 명확 |

## 실생활 비유

- View = 책상
- findViewById = 서랍 하나하나 열어보기
- ViewHolder = 필요한 물건을 상자에 담아놓기

ViewHolder는 리스트 아이템의 하위 View를 미리 저장해 재사용함으로써, 스크롤 시 findViewById 호출을 줄여서 성능을 개선하기 위한 패턴이다. ListView는 선택 사항이지만 RecyclerView에서는 필수 구조이다.
