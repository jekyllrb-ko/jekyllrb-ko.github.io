---
#title: Front Matter
title: 머리말
permalink: /docs/frontmatter/
---

<!--
The front matter is where Jekyll starts to get really cool. Any file that
contains a [YAML](http://yaml.org/) front matter block will be processed by
Jekyll as a special file. The front matter must be the first thing in the file
and must take the form of valid YAML set between triple-dashed lines. Here is a
basic example:
-->
Jekyll 의 수 많은 멋진 기능들 중 그 첫 번째는 바로 머리말입니다. Jekyll 은
[YAML](http://yaml.org/) 머리말 블록을 가진 모든 파일을 특별한 파일로 인식하여
처리합니다. 머리말은 반드시 올바른 YAML 형식으로 작성되어야 하며, 대시문자 3
개로 감싸서 파일의 맨 첫 부분에 위치해야 합니다. 가장 기본적인 형태를 예로 들면
다음과 같습니다:

```yaml
---
layout: post
title: Blogging Like a Hacker
---
```

<!--
Between these triple-dashed lines, you can set predefined variables (see below
for a reference) or even create custom ones of your own. These variables will
then be available to you to access using Liquid tags both further down in the
file and also in any layouts or includes that the page or post in question
relies on.
-->
이 대시문자 사이에 사전-정의 변수 (설명은 아래를 참고하세요) 를 사용할 수 있고,
심지어 자신만의 고유 변수를 정의하는 것도 가능합니다. 해당 파일은 물론 해당
페이지 또는 포스트에 연결된 레이아웃이나 include 파일에서도 Liquid 태그를
사용하여 이 변수들에 접근할 수 있습니다.


<div class="note warning">
<!--
  <h5>UTF-8 Character Encoding Warning</h5>
  <p>
    If you use UTF-8 encoding, make sure that no <code>BOM</code> header
    characters exist in your files or very, very bad things will happen to
    Jekyll. This is especially relevant if you’re running
    <a href="../windows/">Jekyll on Windows</a>.
  </p>
-->
  <h5>UTF-8 문자 인코딩 주의사항</h5>
  <p>
    만일 UTF-8 인코딩을 사용한다면, BOM 헤더 문자가 포함되어 있지는 않는지
    확인하세요. 그렇지 않으면 Jekyll 에 아주, 아주 안좋은 일이 벌어집니다.
    이것은 <a href="../windows/">Jekyll 을 Windows 에서 사용</a>할 때에만
    발생하는 문제입니다.
  </p>
</div>

<div class="note">
<!--
  <h5>ProTip™: Front Matter Variables Are Optional</h5>
  <p>
    If you want to use <a href="../variables/">Liquid tags and variables</a>
    but don’t need anything in your front matter, just leave it empty! The set
    of triple-dashed lines with nothing in between will still get Jekyll to
    process your file. (This is useful for things like CSS and RSS feeds!)
  </p>
-->
  <h5>ProTip™: 머리말의 변수는 필수가 아닙니다</h5>
  <p>
    만약 <a href="../variables/">Liquid 태그와 변수</a>는 사용하고 싶은데
    머리말에는 넣을만한 내용이 하나도 없다면, 그냥 비워두세요! 3 중 대시 사이에
    아무 내용이 없어도, Jekyll 은 해당 파일을 처리합니다. (CSS 나 RSS 피드같은
    파일에 유용합니다!)
  </p>
</div>

<!--
## Predefined Global Variables
-->
## 사전-정의 전역 변수

<!--
There are a number of predefined global variables that you can set in the
front matter of a page or post.
-->
페이지 또는 포스트의 머리말에 사용할 수 있는 다양한 사전-정의 전역 변수가
있습니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Variable</th>
      <th>Description</th>
-->
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>layout</code></p>
      </td>
      <td>
<!--
        <p>

          If set, this specifies the layout file to use. Use the layout file
          name without the file extension. Layout files must be placed in the
          <code>_layouts</code> directory.

        </p>
-->
        <p>

          사용할 레이아웃 파일을 지정한다. 레이아웃 파일명에서 확장자를 제외한
          나머지 부분만 입력한다. 레이아웃 파일은 반드시 <code>_layouts</code>
          디렉토리에 존재해야 한다.

        </p>
        <ul>
          <li>
            Using <code>null</code> will produce a file without using a layout
            file. However this is overridden if the file is a post/document and has a
            layout defined in the <a href="../configuration/#front-matter-defaults">
            frontmatter defaults</a>.
          </li>
          <li>
            Starting from version 3.5.0, using <code>none</code> in a post/document will
            produce a file without using a layout file regardless of frontmatter defaults.
            Using <code>none</code> in a page, however, will cause Jekyll to attempt to
            use a layout named "none".
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>permalink</code></p>
      </td>
      <td>
<!--
        <p>

          If you need your processed blog post URLs to be something other than
          the site-wide style (default <code>/year/month/day/title.html</code>), then you can set
          this variable and it will be used as the final URL.

        </p>
-->
        <p>

          생성된 블로그 포스트 URL 을 사이트 전역 스타일 (디폴트 설정:
          <code>/year/month/day/title.html</code>)이 아닌 다른 스타일로 만드려면, 이
          변수를 사용하여 최종 URL 을 설정하면 된다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>published</code></p>
      </td>
      <td>
<!--
        <p>
          Set to false if you don’t want a specific post to show up when the
          site is generated.
        </p>
-->
        <p>
          사이트가 생성되었을 때 특정 포스트가 나타나지 않게 하려면 false 로
          설정하라.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
  <h5>ProTip™: Render Posts Marked As Unpublished</h5>
  <p>
    To preview unpublished pages, simply run `jekyll serve` or `jekyll build`
    with the `--unpublished` switch. Jekyll also has a handy <a href="../drafts/">drafts</a>
    feature tailored specifically for blog posts.
  </p>
</div>

<!--
## Custom Variables
-->
## 사용자-정의 변수

Any variables in the front matter that are not predefined are mixed into the
data that is sent to the Liquid templating engine during the conversion. For
instance, if you set a title, you can use that in your layout to set the page
title:
변환 작업 중, 사전-정의된 변수가 아닌 모든 머리말 변수들은 데이터로
정리되어 Liquid 템플릿 엔진에 전달됩니다. 예를 들어, title 변수를
설정하면 레이아웃에서 페이지 제목을 입력할 때 사용할 수
있습니다:

```liquid
<!DOCTYPE HTML>
<html>
  <head>
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    …
```

<!--
## Predefined Variables for Posts
-->
## 포스트의 사전-정의 변수

<!--
These are available out-of-the-box to be used in the front matter for a post.
-->
포스트에서 사용할 수 있는 특별한 머리말 변수들입니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Variable</th>
      <th>Description</th>
-->
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
<!--
        <p>
          A date here overrides the date from the name of the post. This can be
          used to ensure correct sorting of posts. A date is specified in the
          format <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code>; hours, minutes, seconds, and timezone offset
          are optional.
        </p>
-->
        <p>
          여기에 지정한 날짜가 포스트 이름에 있는 날짜보다 더 우선순위가 높다.
          포스트를 올바르게 정렬하기 위해 사용할 수 있는 기능이다. 날짜 형식은
          <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code> 이다; 시간, 분, 초와 타임존
          오프셋은 선택사항이다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>category</code></p>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>

          Instead of placing posts inside of folders, you can specify one or
          more categories that the post belongs to. When the site is generated
          the post will act as though it had been set with these categories
          normally. Categories (plural key) can be specified as a <a
          href="https://en.wikipedia.org/wiki/YAML#Basic_components">YAML list</a> or a
          space-separated string.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>tags</code></p>
      </td>
      <td>
        <p>

          Similar to categories, one or multiple tags can be added to a post.
          Also like categories, tags can be specified as a <a
          href="https://en.wikipedia.org/wiki/YAML#Basic_components">YAML list</a> or a
          space-separated string.

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
<!--
  <h5>ProTip™: Don't repeat yourself</h5>
  <p>
    If you don't want to repeat your frequently used front matter variables
    over and over, just define <a href="../configuration/#front-matter-defaults" title="Front Matter defaults">defaults</a>
    for them and only override them where necessary (or not at all). This works
    both for predefined and custom variables.
  </p>
-->
  <h5>ProTip™: 같은 일을 반복하지 마세요</h5>
  <p>
    자주 사용하는 머리말 변수를 계속 반복해서 입력하고 싶지 않으면, 해당 변수에
    대한 <a href="../configuration/#front-matter-defaults" title="Front Matter defaults">기본값</a>을
    정의하고, 필요한 곳에서만 다른 값으로 덮어쓰세요. 사전-정의 변수와
    사용자-정의 변수 모두 이 방법을 적용할 수 있습니다.
  </p>
</div>
