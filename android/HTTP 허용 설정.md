# 2025-08-07

안드로이드에서는 `networkSecurityConfig`라는 걸 설정해서

ㄴ 특정 도메인은 **HTTP 허용**할 수 있게 해줌

### 1. `res/xml/network_security_config.xml` 만들기

```xml
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">43.201.199.73</domain>
    </domain-config>
</network-security-config>
```

> 여기에 HTTP를 허용하고 싶은 IP나 도메인을 넣기
> 

### 2. `AndroidManifest.xml`에 추가하기

```xml

<applicationandroid:networkSecurityConfig="@xml/network_security_config"
    ... >
```

> 이걸 <application> 태그 안에 꼭 넣어줘야 함
>
