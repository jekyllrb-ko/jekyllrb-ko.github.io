---
#title: Environments
title: 환경
permalink: "/docs/configuration/environments/"
---
<!--
In the `build` (or `serve`) arguments, you can specify a Jekyll environment
and value. The build will then apply this value in any conditional statements
in your content.
-->
`build` (혹은 `serve`) 파라메터로, Jekyll 환경변수와
그 값을 설정할 수 있습니다.  이 환경변수는 빌드 시에 사이트의 모든 조건문에서
사용됩니다.

<!--
For example, suppose you set this conditional statement in your code:
-->
예를 들어, 당신의 코드에 이런 조건문이 있다고 가정합시다:

{% raw %}
```liquid
{% if jekyll.environment == "production" %}
   {% include disqus.html %}
{% endif %}
```
{% endraw %}

<!--
When you build your Jekyll site, the content inside the `if` statement won't be
run unless you also specify a `production` environment in the build command,
like this:
-->
Jekyll 사이트를 빌드할 때, 빌드 명령에 환경변수 `production` 을
다음과 같이 정의하지 않으면 `if` 절 안에 들어있는 코드는 실행되지
않습니다:

```sh
JEKYLL_ENV=production jekyll build
```

<!--
Specifying an environment value allows you to make certain content available
only within specific environments.
-->
환경변수 값을 설정함으로써
특정 환경에서만 사용되는 컨텐츠를 만들 수 있습니다.

<!--
The default value for `JEKYLL_ENV` is `development`. Therefore if you omit
`JEKYLL_ENV` from the build arguments, the default value will be
`JEKYLL_ENV=development`. Any content inside
{% raw %}`{% if jekyll.environment == "development" %}`{% endraw %} tags will
automatically appear in the build.
-->
`JEKYLL_ENV` 의 디폴트 값은 `development` 입니다. 따라서
`build` 의 파라메터에 `JEKYLL_ENV` 를 생략하면,
`JEKYLL_ENV=development` 가 디폴트 값으로 사용됩니다. 빌드 시
{% raw %}`{% if jekyll.environment == "development" %}`{% endraw %} 태그
안의 모든 컨텐츠가 출력될 것입니다.

<!--
Your environment values can be anything you want (not just `development` or
`production`). Some elements you might want to hide in development
environments include Disqus comment forms or Google Analytics. Conversely,
you might want to expose an "Edit me in GitHub" button in a development
environment but not include it in production environments.
-->
당신이 원하는 어떤 것이든 환경변수 값으로 사용할 수 있습니다 (반드시 `development` 나
`production` 일 필요는 없습니다). Disqus 댓글란이나 Google Analytics 처럼
개발환경에서는 표시하고 싶지 않은 요소가 있을 수 있습니다. 반대로,
"GitHub 에서 수정" 버튼은 개발환경에서 노출시키고
운영환경에는 포함시키지 않을 수도 있습니다.

<!--
By specifying the option in the build command, you avoid having to change
values in your configuration files when moving from one environment to another.
-->
빌드 명령에 옵션을 정의함으로써, 한 환경에서 다른 환경으로
환경설정 파일의 값을 수정하지 않고 이동할 수 있습니다.

<div class="note info">
  <p>
<!--
    To switch part of your config settings depending on the environment, use the <a href="/docs/configuration/options/#build-command-options">build command option</a>, for example <code>--config _config.yml,_config_development.yml</code>. Settings in later files override settings in earlier files.
-->
    환경설정의 일부분을 원하는 환경에 따라 전환하려면, <a href="/docs/configuration/options/#build-command-options">빌드 명령어 옵션</a>을 사용하세요. 예, <code>--config _config.yml,_config_development.yml</code>. 설정들의 적용 우선순위는 설정파일 순서의 역순입니다.
  </p>
</div>
