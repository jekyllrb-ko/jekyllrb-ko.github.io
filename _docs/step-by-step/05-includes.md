---
layout: step
#title: Includes
title: 조각파일
position: 5
---
<!--
The site is coming together; however, there's no way to navigate between
pages. Let's fix that.
-->
사이트가 점점 그럴싸해지고 있습니다; 하지만, 페이지 사이의 네비게이션이
없네요. 고쳐봅시다.

<!--
Navigation should be on every page so adding it to your layout is the correct
place to do this. Instead of adding it directly to the layout, let's use this
as an opportunity to learn about includes.
-->
네비게이션은 모든 페이지에 있어야 하므로 레이아웃에 추가하는 것이 올바른
방법입니다. 레이아웃에 직접 추가하는 대신, 이 기회를 이용해 조각파일에 대하여
배워보도록 합니다.

<!--
## Include tag
-->
## Include 태그

<!--
The `include` tag allows you to include content from another file stored
in an `_includes` folder. Includes are useful for having a single source for
source code that repeats around the site or for improving the readability.
-->
`include` 태그를 사용하면 `_includes` 폴더에 저장된 조각파일의 내용을
포함시킬 수 있습니다. 조각파일은 사이트 여러곳에 반복되는 코드를 한 곳에서
관리하거나 사이트 소스코드의 가독성을 향상시키는데에 유용합니다.

<!--
Navigation source code can get complex so sometimes it's nice to move it into an
include.
-->
네비게이션을 구현하는 소스코드는 복잡한 경우가 많아 조각파일로 보관하는 것이
좋습니다.

<!--
## Include usage
-->
## 조각파일 사용법

<!--
Create a file for the navigation at `_includes/navigation.html` with the
following content:
-->
네비게이션을 위한 파일을 `_includes/navigation.html` 에 생성하고 다음 내용을
저장합니다:

```
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```

<!--
Try using the include tag to add the navigation to `_layouts/default.html`:
-->
include 태그를 사용해서 `_layouts/default.html` 에 네비게이션을 추가합니다:

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```
{% endraw %}

<!--
Open <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
in your browser and try switching between the pages.
-->
브라우저에서 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
를 열어 페이지 사이를 이동해봅니다.

<!--
## Current page highlighting
-->
## 현재 페이지 표시하기

<!--
Let's take this a step further and highlight the current page in the navigation.
-->
좀 더 깊게 파고들어서 네비게이션에 현재 페이지를 표시하는 방법을 알아봅시다.

<!--
`_includes/navigation.html` needs to know the URL of the page it's inserted into
so it can add styling. Jekyll has useful [variables](/docs/variables/) available
one of which is `page.url`.
-->
스타일을 추가하려면 `_includes/navigation.html` 은 자신이 삽입된 페이지의 URL 을
알 필요가 있습니다. Jekyll 에서 사용할 수 있는 유용한 [변수들](/docs/variables/)
중 `page.url` 이라는 변수가 있습니다.

<!--
Using `page.url` you can check if each link is the current page and color it red
if true:
-->
`page.url` 을 사용해서 각 링크가 현재 페이지인지 확인하고 만약 그렇다면 빨간색으로
표시합니다:

{% raw %}
```liquid
<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>
```
{% endraw %}

<!--
Take a look at <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
and see your red link for the current page.
-->
브라우저에서 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
을 열어 현재 페이지 링크가 빨간색인지 확인합니다.

<!--
There's still a lot of repetition here if you wanted to add a new item to the
navigation or change the highlight color. In the next step we'll address this.
-->
네비게이션에 새 페이지를 추가하거나 색을 변경하고자 하는 경우 여전히 중복된
코드가 많이 발생합니다. 다음 단계에서 이에 대해 다뤄보겠습니다.
