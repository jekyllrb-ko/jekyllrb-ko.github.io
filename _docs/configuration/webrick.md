---
#title: WEBrick Options
title: WEBrick 옵션
permalink: "/docs/configuration/webrick/"
---
<!--
You can provide custom headers for your site by adding them to `_config.yml`
-->
자신의 사이트에 커스텀 헤더를 사용하려면 `_config.yml` 에 추가하면 됩니다

```yaml
# File: _config.yml
webrick:
  headers:
    My-Header: My-Value
    My-Other-Header: My-Other-Value
```

<!--
### Defaults
-->
### 기본설정

<!--
Jekyll provides by default `Content-Type` and `Cache-Control` response
headers: one dynamic in order to specify the nature of the data being served,
the other static in order to disable caching so that you don't have to fight
with Chrome's aggressive caching when you are in development mode.
-->
Jekyll 은 응답 헤더 `Content-Type` 과 `Cache-Control` 를 기본
제공합니다: 전자는 데이터가 처리되는 방식을 결정하기 위한 동적 헤더이고,
후자는 캐시를 비활성화하는 정적 헤더로서 크롬 개발자 모드에서 사용되는 공격적인
캐시 방식에 신경을 쓸 필요가 없어집니다.
