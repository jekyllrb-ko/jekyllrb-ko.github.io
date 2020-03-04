---
#title: Liquid Options
title: Liquid 옵션
permalink: "/docs/configuration/liquid/"
---
<!--
Liquid's response to errors can be configured by setting `error_mode`. The
options are
-->
Liquid 의 에러 처리 방식은 `error_mode` 로 설정할 수 있습니다. 옵션은
다음과 같습니다.

<!--
- `lax` --- Ignore all errors.
- `warn` --- Output a warning on the console for each error.
- `strict` --- Output an error message and stop the build.
-->
- `lax` --- 모든 에러 무시
- `warn` --- 모든 에러에 대한 경고를 콘솔에 출력
- `strict` --- 에러 메시지를 출력하고 빌드를 종료

<!--
You can also configure Liquid's renderer to catch non-assigned variables and
non-existing filters by setting `strict_variables` and / or `strict_filters`
to `true` respectively. {% include docs_version_badge.html version="3.8.0" %}
-->
또한 Liquid 렌더러가 정의되지 않은 변수와 존재하지 않는 필터를 잡아내게 하려면
`strict_variables` 와 / 또는 `strict_filters` 를 `true` 로 설정하면 됩니다.
{% include docs_version_badge.html version="3.8.0" %}

<!--
Do note that while `error_mode` configures Liquid's parser, the `strict_variables`
and `strict_filters` options configure Liquid's renderer and are consequently,
mutually exclusive.
-->
한 가지, `error_mode` 는 Liquid 파서에 대한 설정이고
`strict_variables` 와 `strict_filters` 옵션은 Liquid 렌더러에 대한 설정이기 때문에,
서로 연관성이 없다는 것을 알아두어야 합니다.
