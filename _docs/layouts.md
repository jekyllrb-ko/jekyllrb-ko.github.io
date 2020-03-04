---
#title: Layouts
title: 레이아웃
description: placeholder
permalink: /docs/layouts/
---
<!--
Layouts are templates that wrap around your content. They allow you to have the
source code for your template in one place so you don't have to repeat things
like your navigation and footer on every page.
-->
레이아웃은 컨텐츠를 포장하는 템플릿입니다. 템플릿을 위한 코드를 한 곳에 보관할
수 있게 해주기 때문에 모든 페이지에 네비게이션이나 푸터를 반복해서 입력할 필요가
없습니다.

<!--
Layouts live in the `_layouts` directory. The convention is to have a base
template called `default.html` and have other layouts [inherit](#inheritance)
from this as needed.
-->
레이아웃은 `_layouts` 디렉토리에 위치합니다. 관례적으로 `default.html` 라는
이름의 기본 템플릿을 가지고 필요에 따라 [상속](#inheritance)해서 다른 레이아웃을
만듭니다.

<div class="note">
<!--
  <h5>Layouts Directory</h5>
-->
  <h5>레이아웃 디렉토리</h5>
  <p>
<!--
    Jekyll looks for the <code>_layouts</code> directory either at the root of
    your site's <code>source</code> or at the root of your theme.
-->
    Jekyll 은 사이트 <code>source</code> 의 루트 또는 테마의 루트에서
    <code>_layouts</code> 디렉토리를 찾습니다.
  </p>
  <p>
<!--
    While you can configure the directory name in which your layouts can reside by
    setting the <code>layouts_dir</code> key in your config file, the directory
    itself should be located at the root of your site's <code>source</code> directory.
-->
    환경설정 파일에 <code>layouts_dir</code> 키를 설정해서 레이아웃이 위치하는
    디렉토리의 이름을 변경할 수 있지만, 해당 디렉토리는 반드시 사이트의
    <code>source</code> 디렉토리에 위치해야만 합니다.
  </p>
</div>


<!--
## Usage
-->
## 사용법

<!--
The first step is to put the template source code in `default.html`. `content`
is a special variable, the value is the rendered content of the post or page
being wrapped.
-->
첫 단계는 `default.html` 에 템플릿 소스코드를 입력하는 것입니다. `content` 라는
특별한 변수가 있는데, 그 값은 포스트나 페이지의 렌더링 된
컨텐츠입니다.



{% raw %}
```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/css/style.css">
  </head>
  <body>
    <nav>
      <a href="/">Home</a>
      <a href="/blog/">Blog</a>
    </nav>
    <h1>{{ page.title }}</h1>
    <section>
      {{ content }}
    </section>
    <footer>
      &copy; to me
    </footer>
  </body>
</html>
```
{% endraw %}

<!--
You have full access to the front matter of the origin. In the
example above, `page.title` comes from the page front matter.
-->
당신은 머리말에 대해 완전한 접근권한을 가지고 있습니다. 위
예제에서, `page.title` 은 페이지의 머리말로부터 비롯된 것입니다.

<!--
Next you need to specify what layout you're using in your page's front matter.
You can also use
[front matter defaults](/docs/configuration/front-matter-defaults/) to save you
from having to set this on every page.
-->
그 다음 할 일은 어떤 레이아웃을 사용할 것인지 페이지의 머리말에 명시하는 것입니다.
그리고 [머리말 기본값](/docs/configuration/front-matter-defaults/)을 사용하면
모든 페이지에 같은 내용을 입력하지 않아도 됩니다.

```
---
title: My First Page
layout: default
---

This is the content of my page
```

<!--
The rendered output of this page is:
-->
이 페이지의 렌더링된 결과물입니다:

```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>My First Page</title>
    <link rel="stylesheet" href="/css/style.css">
  </head>
  <body>
    <nav>
      <a href="/">Home</a>
      <a href="/blog/">Blog</a>
    </nav>
    <h1>My First Page</h1>
    <section>
      This is the content of my page
    </section>
    <footer>
      &copy; to me
    </footer>
  </body>
</html>
```


<!--
## Inheritance
-->
## 상속 {#inheritance}

<!--
Layout inheritance is useful when you want to add something to an existing
layout for a portion of documents on your site. A common example of this is
blog posts, you might want a post to display the date and author but otherwise
be identical to your base layout.
-->
레이아웃 상속은 이미 존재하는 레이아웃에 무언가 추가해서 사이트의 일부 문서에만
적용하고자 할 때 유용합니다. 이에 대한 간단한 예시로 블로그 포스트를 들 수
있는데, 포스트에는 날짜와 작성자를 표시하지만 나머지는 기본 레이아웃과 똑같이
보이게 하는 것입니다.

<!--
To achieve this you need to create another layout which specifies your original
layout in front matter. For example this layout will live at
`_layouts/post.html`:
-->
이를 위해서는 새 레이아웃을 만들어 그 머리말에 원래의 레이아웃을 지정해야
합니다. 다음은 `_layouts/post.html` 라는 이름의 레이아웃
예시입니다:

{% raw %}
```
---
layout: default
---
<p>{{ page.date }} - Written by {{ page.author }}</p>

{{ content }}
```
{% endraw %}

<!--
Now posts can use this layout while the rest of the pages use the default.
-->
이제 포스트에는 이 레이아웃을 사용하고 다른 페이지들에는 기본 레이아웃을 사용합니다.

<!--
## Variables
-->
## 변수

<!--
You can set front matter in layouts, the only difference is when you're
using in Liquid, you need to use the `layout` variable instead of `page`. For
example:
-->
레이아웃에도 머리말을 설정할 수 있는데, 유일한 차이점은 Liquid 를
사용할 때, `page` 대신 `layout` 을 사용해야 한다는 것입니다. 예를
들면 다음과 같습니다:

{% raw %}
```
---
city: San Francisco
---
<p>{{ layout.city }}</p>

{{ content }}
```
{% endraw %}
