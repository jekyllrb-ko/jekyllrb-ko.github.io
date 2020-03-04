---
#title: Front Matter Defaults
title: 머리말 기본값
permalink: "/docs/configuration/front-matter-defaults/"
---

<!--
Using [front matter](/docs/front-matter/) is one way that you can specify configuration in the pages and posts for your site. Setting things like a default layout, or customizing the title, or specifying a more precise date/time for the post can all be added to your page or post front matter.
-->
페이지와 포스트에서 환경설정 값을 조정하는 방법 중 하나는 [머리말](/docs/frontmatter/)을 사용하는 것입니다. 기본 레이아웃 설정이나 제목 수정, 또는 더 자세한 날짜 / 시간 지정 등을 페이지나 포스트의 머리말에 입력할 수 있습니다.

<!--
Often times, you will find that you are repeating a lot of configuration options. Setting the same layout in each file, adding the same category - or categories - to a post, etc. You can even add custom variables like author names, which might be the same for the majority of posts on your blog.
-->
종종, 같은 내용의 환경설정들을 계속해서 반복 입력하고 있는 자신을 발견할 지도 모릅니다. 각각의 파일에 동일한 레이아웃을 설정하거나 여러 개의 포스트를 동일한 카테고리(들)에 추가하는 것 말이죠. 심지어는 작성자 이름처럼 블로그의 거의 모든 포스트에 동일하게 사용되는 값을 사용자 변수로 일일히 추가하게 될 수도 있습니다.

<!--
Instead of repeating this configuration each time you create a new post or page, Jekyll provides a way to set these defaults in the site configuration. To do this, you can specify site-wide defaults using the `defaults` key in the `_config.yml` file in your project's root directory.
-->
Jekyll 은 사이트 환경설정에 변수들의 기본값을 지정하는 방법을 제공하기 때문에, 새 포스트나 페이지를 추가할 때마다 이러한 환경설정들을 반복하지 않아도 됩니다.  그러기 위해서는, 프로젝트의 루트 디렉토리에 있는 `_config.yml` 파일에 `defaults` 라는 키를 사용하여 사이트에 전체에 사용되는 기본값을 정의할 수 있습니다.

<!--
The `defaults` key holds an array of scope/values pairs that define what defaults should be set for a particular file path, and optionally, a file type in that path.
-->
`defaults` 키에 여러 쌍의 범위/값(scope/values)을 배열로 입력할 수 있어, 특정 경로의 파일이나 파일 종류에 사용되어야 하는 디폴트 값을 정의할 수 있습니다.

<!--
Let's say that you want to add a default layout to all pages and posts in your site. You would add this to your `_config.yml` file:
-->
사이트의 모든 포스트와 페이지에 기본 레이아웃을 추가하는 경우를 생각해 봅시다. `_config.yml` 파일에 아래 내용을 추가하면 됩니다:

```yaml
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
    values:
      layout: "default"
```

<div class="note info">
<!--
  <h5>Stop and rerun `jekyll serve` command.</h5>
-->
  <h5>종료한 뒤 다시 `jekyll serve` 명령을 실행해주세요.</h5>
  <p>
<!--
    The <code>_config.yml</code> master configuration file contains global configurations
    and variable definitions that are read once at execution time. Changes made to <code>_config.yml</code>
    during automatic regeneration are not loaded until the next execution.
-->
    환경설정 파일인 <code>_config.yml</code> 에는 전역 환경설정과 전역 변수가 설정되어 있으며
    이것들은 실행 시 최초 한 번만 읽어들여집니다. 자동 재생성 모드에서도 <code>_config.yml</code>
    파일의 변경사항은 다시 실행하기 전까지는 반영되지 않습니다.
  </p>
  <p>
<!--
    Note <a href="/docs/datafiles">Data Files</a> are included and reloaded during automatic regeneration.
-->
    <a href="../datafiles">데이터 파일</a>의 변경사항은 반영됩니다.
  </p>
</div>

<!--
Here, we are scoping the `values` to any file that exists in the path `scope`. Since the path is set as an empty string, it will apply to **all files** in your project. You probably don't want to set a layout on every file in your project - like css files, for example - so you can also specify a `type` value under the `scope` key.
-->
여기서 우리는 `values` 의 범위를 경로 `scope` 에 존재하는 모든 파일로 제한하고 있습니다. 하지만 경로에 빈 문자열을 설정했기 때문에, 프로젝트 내의 **모든 파일** 에 적용될 것입니다. 프로젝트 내의 모든 파일에 한 레이아웃을 적용하길 원치 않을 수도 있습니다 - 예를 들자면, CSS 파일같이 말이죠 - 이런 경우엔 `scope` 키에 `type` 값을 지정할 수 있습니다.

<!--
```yaml
defaults:
  -
    scope:
      path: "" # an empty string here means all files in the project
      type: "posts" # previously `post` in Jekyll 2.2.
    values:
      layout: "default"
```
-->
```yaml
defaults:
  -
    scope:
      path: "" # 이 빈 문자열은 프로젝트의 모든 파일을 의미함
      type: "posts" # 이전 Jekyll 2.2 에서는 `post`
    values:
      layout: "default"
```

<!--
Now, this will only set the layout for files where the type is `posts`.
The different types that are available to you are `pages`, `posts`, `drafts` or any collection in your site. While `type` is optional, you must specify a value for `path` when creating a `scope/values` pair.
-->
이제, `type` 이 `posts` 인 파일에만 레이아웃이 설정될 것입니다.
`type` 의 값으로는 `pages`, `posts`, `drafts` 또는 사이트 내의 컬렉션 이름을 사용할 수 있습니다. `scope/values` 쌍을 생성할 때, `type` 은 선택사항이지만 `path` 는 반드시 정의해야 합니다.

<!--
As mentioned earlier, you can set multiple scope/values pairs for `defaults`.
-->
앞서 언급했던 것처럼, `defaults` 에 여러 개의 범위/값 쌍을 설정할 수 있습니다.

<!--
```yaml
defaults:
  -
    scope:
      path: ""
      type: "pages"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages" # previously `page` in Jekyll 2.2.
    values:
      layout: "project" # overrides previous default layout
      author: "Mr. Hyde"
```
-->
```yaml
defaults:
  -
    scope:
      path: ""
      type: "pages"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages" # 이전 Jekyll 2.2 에서는 `page` 
    values:
      layout: "project" # 이전 디폴트 레이아웃 설정을 덮어씀
      author: "Mr. Hyde"
```

<!--
With these defaults, all pages would use the `my-site` layout. Any html files that exist in the `projects/` folder will use the `project` layout, if it exists. Those files will also have the `page.author` [liquid variable](/docs/variables/) set to `Mr. Hyde`.
-->
이 디폴트 값으로 인하여, 모든 페이지는 `my-site` 레이아웃을 사용하게 됩니다. `projects/` 폴더 안에 있는 모든 HTML 파일들은 `project` 레이아웃을 사용하게 됩니다. 또한 이 파일들은 `Mr. Hyde` 라는 값을 가진 [Liquid 변수](/docs/variables/) `page.author` 도 갖게 됩니다.

<!--
```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # a collection in your site, in plural form
    values:
      layout: "default"
```
-->
```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # 사이트의 컬렉션"들"
    values:
      layout: "default"
```

<!--
In this example, the `layout` is set to `default` inside the
[collection](/docs/collections/) with the name `my_collection`.
-->
이 예제에서, `my_collection` 이라는 이름의 [컬렉션](/docs/collections/)
안에서는 `layout` 이 `default` 로 설정됩니다.

<!--
### Glob patterns in Front Matter defaults
-->
### 머리말 기본값에 글로브 패턴 사용

<!--
It is also possible to use glob patterns (currently limited to patterns that contain `*`) when matching defaults. For example, it is possible to set specific layout for each `special-page.html` in any subfolder of `section` folder. {%- include docs_version_badge.html version="3.7.0" -%}
-->
머리말 기본값에 글로브(glob) 패턴 (현재는 `*` 만 사용 가능함) 을 사용하는 것도 가능합니다.
예를 들면, `section` 폴더의 모든 하위 디렉토리 안에 있는 `special-page.html` 파일에 특정 레이아웃을 설정할 수 있습니다. {%- include docs_version_badge.html version="3.7.0" -%}

```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: "section/*/special-page.html"
    values:
      layout: "specific-layout"
```

<div class="note warning">
<!--
  <h5>Globbing and Performance</h5>
-->
  <h5>글로브 패턴과 성능</h5>
  <p>
<!--
    Please note that globbing a path is known to have a negative effect on
    performance and is currently not optimized, especially on Windows.
    Globbing a path will increase your build times in proportion to the size
    of the associated collection directory.
-->
    글로브 패턴을 사용하는 것은 성능에 부정적인 영향을 미친다고 알려져 있고
    현재 이 기능은, 특히 윈도우즈에, 최적화 되어있지 않습니다.
    글로브 패턴을 사용하면 관련된 컬렉션 디렉토리의 크기에 비례해서 빌드 시간이
    증가할 것입니다.
  </p>
</div>

<!--
### Precedence
-->
### 우선순위

<!--
Jekyll will apply all of the configuration settings you specify in the `defaults` section of your `_config.yml` file. You can choose to override settings from other scope/values pair by specifying a more specific path for the scope.
-->
Jekyll 은 `_config.yml` 파일의 `defaults` 섹션에 설정된 환경설정 값을 모두 적용합니다. 범위에 더 자세한 경로를 사용하면 선택적으로 다른 범위/값을 덮어쓸 수 있습니다.

<!--
You can see that in the second to last example above. First, we set the default page layout to `my-site`. Then, using a more specific path, we set the default layout for pages in the `projects/` path to `project`. This can be done with any value that you would set in the page or post front matter.
-->
끝에서 두 번째 예제의 내용처럼 말이죠. 먼저, 우리는 페이지 레이아웃 기본값을 `my-site` 로 설정했습니다. 그 다음, 더 자세한 경로를 사용해서, `projects/` 경로에 있는 페이지에 대해서만 레이아웃을 `project` 로 설정했습니다. 페이지나 포스트의 머리말에 사용하는 어떤 설정에든지 이 방법을 사용할 수 있습니다.

<!--
Finally, if you set defaults in the site configuration by adding a `defaults` section to your `_config.yml` file, you can override those settings in a post or page file. All you need to do is specify the settings in the post or page front matter. For example:
-->
마지막으로, `_config.yml` 파일에 `defaults` 섹션을 추가해서 사이트 환경설정 디폴트 값을 정의했어도, 페이지나 포스트에서 값을 덮어쓸 수 있습니다. 페이지나 포스트의 머리말에서 다시 해당 환경설정 값을 정의하면 됩니다. 예를 들면 다음과 같습니다:

<!--
```yaml
# In _config.yml
...
defaults:
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project"
      author: "Mr. Hyde"
      category: "project"
...
```
-->
```yaml
# _config.yml 파일
...
defaults:
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project"
      author: "Mr. Hyde"
      category: "project"
...
```

<!--
```yaml
# In projects/foo_project.md
---
author: "John Smith"
layout: "foobar"
---
The post text goes here...
```
-->
```yaml
# projects/foo_project.md 파일
---
author: "John Smith"
layout: "foobar"
---
여기부터는 포스트 내용입니다...
```

<!--
The `projects/foo_project.md` would have the `layout` set to `foobar` instead
of `project` and the `author` set to `John Smith` instead of `Mr. Hyde` when
the site is built.
-->
이제 사이트를 구축하면, `projects/foo_project.md` 파일의 `layout` 은 `project`
가 아닌 `foobar` 로, `author` 는 `Mr. Hyde` 가 아닌 `John Smith` 로 설정됩니다.
