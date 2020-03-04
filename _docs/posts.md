---
#title: Posts
title: 포스트
permalink: /docs/posts/
redirect_from:
  - /docs/drafts/
---

<!--
Blogging is baked into Jekyll. You write blog posts as text files and Jekyll
provides everything you need to turn it into a blog.
-->
Jekyll 에는 블로그 기능이 완전히 반영되어 있습니다. 당신은 텍스트 파일로 블로그
포스트를 작성하고 Jekyll 은 그것을 블로그로 변환하는데 필요한 모든것을 제공합니다.

<!--
## The Posts Folder
-->
## 포스트 폴더

<!--
The `_posts` folder is where your blog posts live. You typically write posts
in [Markdown](https://daringfireball.net/projects/markdown/), HTML is
also supported.
-->
당신의 블로그 포스트가 사는 곳은 `_posts` 폴더입니다. 포스트는 일반적으로
[마크다운](https://daringfireball.net/projects/markdown/)으로 작성하며, HTML
또한 지원합니다.

<!--
## Creating Posts
-->
## 포스트 생성하기

<!--
To create a post, add a file to your `_posts` directory with the following
format:
-->
포스트를 생성하려면, `_posts` 디렉토리에 파일을 추가하고 다음과 같은
형식으로 내용을 작성합니다:

```
YEAR-MONTH-DAY-title.MARKUP
```

<!--
Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit
numbers, and `MARKUP` is the file extension representing the format used in the
file. For example, the following are examples of valid post filenames:
-->
여기서 `YEAR` 는 네 자리의 숫자, `MONTH` 와 `DAY` 는 두 자리 숫자이고, 확장자
부분의 `MARKUP` 은 파일에 사용된 마크다운 포맷입니다. 올바른 포스트 파일명을
예로 들면 다음과 같습니다:

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.md
```

<!--
All blog post files must begin with [front matter](/docs/front-matter/) which is
typically used to set a [layout](/docs/layouts/) or other meta data. For a simple
example this can just be empty:
-->
모든 블로그 포스트 파일은 [머리말](/docs/front-matter/)로 시작되어야 하며, 이것은
일반적으로 [레이아웃](/docs/layouts/) 이나 다른 메타 데이터를 설정하는데 사용됩니다.
아무 내용이 없는 것도 가능합니다:

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!
```

<div class="note">
<!--
  <h5>ProTip™: Link to other posts</h5>
-->
  <h5>ProTip™: 다른 포스트로 링크하기</h5>
  <p>
<!--
    Use the <a href="/docs/liquid/tags/#linking-to-posts"><code>post_url</code></a>
    tag to link to other posts without having to worry about the URLs
    breaking when the site permalink style changes.
-->
    <code><a href="/docs/liquid/tags/#linking-to-posts">post_url</a></code> 태그를 사용하면
    사이트 고유주소 스타일이 바뀌는 경우에도 URL 이 잘못될 걱정을 할 필요가
    없습니다.
  </p>
</div>

<div class="note info">
<!--
  <h5>Be aware of character sets</h5>
-->
  <h5>캐릭터 세트에 주의하세요</h5>
  <p>
<!--
    Content processors can modify certain characters to make them look nicer.
    For example, the <code>smart</code> extension in Redcarpet converts standard,
    ASCII quotation characters to curly, Unicode ones. In order for the browser
    to display those characters properly, define the charset meta value by
    including <code>&lt;meta charset=&quot;utf-8&quot;&gt;</code> in the
    <code>&lt;head&gt;</code> of your layout.
-->
    컨텐츠 처리기는 특정 문자들을 변경할 수 있어서 결과물을 더 좋게 보이게
    합니다. 예를 들어, Redcarpet 변환 기본방식의 <code>smart</code> 확장기능은
    ASCII 인용 부호를 유니코드 문자로 바꿉니다. 따라서, 이러한 문자들이
    브라우저에 올바르게 표시되게 하려면, 레이아웃 파일의 <code>&lt;head&gt;</code>
    에 <code>&lt;meta charset=&quot;utf-8&quot;&gt;</code> 라고 입력하여 캐릭터
    세트 메타 정보를 정의해야 합니다.
  </p>
</div>

<!--
## Including images and resources
-->
## 이미지와 자원 삽입하기

<!--
At some point, you'll want to include images, downloads, or other
digital assets along with your text content. One common solution is to create
a folder in the root of the project directory called something like `assets`,
into which any images, files or other resources are placed. Then, from within
any post, they can be linked to using the site’s root as the path for the asset
to include. The best way to do this depends on the way your site’s (sub)domain
and path are configured, but here are some simple examples in Markdown:
-->
때때로 글 중간에 이미지, 다운로드 또는 그 밖에 다른 종류의 자원을
삽입해야할 때가 있습니다. 가장 일반적인 방법 중 하나는
프로젝트의 루트 디렉토리에 `assets` 같은 이름의 디렉토리를 만들고,
이미지와 파일, 그 밖의 다른 자원들을 보관하는 것입니다. 그 다음, 어느
포스트에서든지 링크하는 자원의 경로에 사이트 루트 경로를
포함시키면 됩니다. 이를 위한 최선의 방법은 사이트의 (서브)도메인과
경로 설정에 따라 다르지만, 여기 몇 가지 단순한 마크다운 예제가 있습니다:

<!--
Including an image asset in a post:
-->
포스트에 이미지를 삽입:

```markdown
... which is shown in the screenshot below:
![My helpful screenshot](/assets/screenshot.jpg)
```

<!--
Linking to a PDF for readers to download:
-->
PDF 다운로드 링크를 삽입:

```markdown
... you can [get the PDF](/assets/mydoc.pdf) directly.
```

<!--
## Displaying an index of posts
-->
## 포스트 목록 표시하기

<!--
Creating an index of posts on another page should be easy thanks to
[Liquid](https://docs.shopify.com/themes/liquid/basics) and its tags. Here’s a
simple example of how to create a list of links to your blog posts:
-->
별도의 페이지에 포스트 목록을 생성하는 것은
[Liquid](https://docs.shopify.com/themes/liquid/basics) 와 이에 포함된 태그 기능을 사용하면 쉽습니다. 여기,
포스트 링크 목록을 생성하는 간단한 예시가 있습니다:

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

<!--
You have full control over how (and where) you display your posts,
and how you structure your site. You should read more about [how templates
work](/docs/templates/) with Jekyll if you want to know more.
-->
포스트를 어떻게 (그리고 어디에) 표시할 것인지, 사이트를 어떻게 구성할 것인지,
전부 다 제어할 수 있습니다. 더 자세한 내용을 알고 싶다면, Jekyll 에서 [템플릿이
작동하는 방법](/docs/templates/)을 읽어보세요.

<!--
Note that the `post` variable only exists inside the `for` loop above. If
you wish to access the currently-rendering page/posts's variables (the
variables of the post/page that has the `for` loop in it), use the `page`
variable instead.
-->
위 예제에서 `post` 변수는 오직 `for` 루프 안에서만 존재한다는 것에 주의하세요.
만약 현재 렌더링중인 페이지/포스트의 변수 (`for` 루프를 포함하고 있는
포스트/페이지의 변수) 에 접근하고자 한다면, `post` 대신 `page` 변수를
사용하세요.

<!--
## Categories and Tags
-->
## 카테고리와 태그

<!--
Jekyll has first class support for categories and tags in blog posts. The difference
between categories and tags is a category can be part of the URL for a post
whereas a tag cannot.
-->
Jekyll 은 블로그 포스트의 카테고리와 태그에 대한 최고 수준의 지원을 제공합니다. 카테고리와
태그의 차이점은 카테고리는 포스트의 URL 에 포함될 수 있으며
태그는 안된다는 점입니다.

<!--
To use these, first set your categories and tags in front matter:
-->
이 기능을 사용하려면, 머리말에 카테고리와 태그를 설정합니다:

```yaml
---
layout: post
title: A Trip
categories: [blog, travel]
tags: [hot, summer]
---
```

<!--
Jekyll makes the categories available to us at `site.categories`. Iterating over
`site.categories` on a page gives us another array with two items, the first
item is the name of the category and the second item is an array of posts in that
category.
-->
Jekyll 은 `site.categories` 로 카테고리를 사용할 수 있게 해줍니다. 페이지에서
`site.categories` 에 반복문을 적용하면 두 항목으로 구성된 또 다른 배열을 사용할 수 있는데,
첫 번째 항목은 카테고리의 이름이고 두 번째 항목은 해당 카테고리의 포스트
배열입니다.

{% raw %}
```liquid
{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
```
{% endraw %}

<!--
For tags it's exactly the same except the variable is `site.tags`.
-->
태그는 변수가 `site.tags` 라는 것만 제외하면 완벽히 동일합니다.

<!--
## Post excerpts
-->
## 포스트 발췌

<!--
You can access a snippet of a posts's content by using `excerpt` variable on a
post. By default this is the first paragraph of content in the post, however it
can be customized by setting a `excerpt_separator` variable in front matter or
`_config.yml`.
-->

```markdown
---
excerpt_separator: <!--more-->
---

Excerpt with multiple paragraphs

Here's another paragraph in the excerpt.
<!--more-->
Out-of-excerpt
```

<!--
Here's an example of outputting a list of blog posts with an excerpt:
-->
다음은 발췌와 함께 블로그 포스트 목록을 출력하는 예시입니다:

{% raw %}
```liquid
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

## Drafts

<!--
Drafts are posts without a date in the filename. They're posts you're still
working on and don't want to publish yet. To get up and running with drafts,
create a `_drafts` folder in your site's root and create your first draft:
-->
초안이란 파일명에 날짜가 없는 포스트입니다. 현재 작성중이기 때문에 아직은
온라인에 게시하고 싶지 않은 포스트를 의미합니다. 초안 기능을 사용하려면,
사이트의 루트 디렉토리에 `_drafts` 폴더를 만들고 초안을 생성하면 됩니다:


```
.
├── _drafts
│   └── a-draft-post.md
...
```

<!--
To preview your site with drafts, run `jekyll serve` or `jekyll build`
with the `--drafts` switch. Each will be assigned the value modification time
of the draft file for its date, and thus you will see currently edited drafts
as the latest posts.
-->
초안을 포함해서 사이트를 미리보기 하려면, `jekyll serve` 나 `jekyll build`
명령에 `--drafts` 스위치를 추가해서 실행하세요. 초안의 작성시간에
해당 파일의 수정시간을 할당하기 때문에, 현재 작업중인 초안이
가장 최신 포스트인 것처럼 표시됩니다.
