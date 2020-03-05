---
layout: step
#title: Front Matter
title: 머리말
position: 3
---
<!--
Front matter is a snippet of [YAML](http://yaml.org/) which sits between two
triple-dashed lines at the top of a file. Front matter is used to set variables
for the page, for example:
-->
머리말은 파일의 맨 처음에 세 개의 대시문자로 감싼 [YAML](http://yaml.org/)
코드 조각입니다. 머리말은 해당 페이지에 대한 변수를 설정하는데에
사용됩니다. 예시:

```yaml
---
my_number: 5
---
```

<!--
Front matter variables are available in Liquid under the `page` variable. For
example to output the variable above you would use:
-->
머리말 변수는 Liquid 에서 `page` 변수로 사용할 수 있습니다. 예를 들어
위 변수를 출력하기 위해서는 다음과 같이 합니다:

{% raw %}
```liquid
{{ page.my_number }}
```
{% endraw %}

<!--
## Use front matter
-->
## 머리말을 사용하세요

<!--
Let's change the `<title>` on your site to populate using front matter:
-->
머리말을 사용해서 사이트의 `<title>` 을 바꿔봅시다:

{% raw %}
```liquid
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
{% endraw %}

<!--
Note that in order for Jekyll to process any liquid tags on your page,
you _must_ include front matter on it. The most minimal snippet of front matter
you can include is:
-->
Jekyll 이 당신의 페이지의 Liquid 태그를 처리하도록 하려면, _반드시_
머리말이 있어야 한다는 사실을 잊지마세요. 가장 단순한 형태의 머리말은 다음과
같습니다:

```yaml
---
---
```

<!--
You may still be wondering why you'd output it this way as it takes
more source code than raw HTML. In this next step, you'll see why we've
been doing this.
-->
여전히 왜 순수 HTML 보다 더 많은 코드가 필요한 이런 방식을 사용해야
하는지 궁금할 것입니다. 다음 단계에서, 왜 이런 것들을 하고 있었는지
그 이유를 알 수 있습니다.
