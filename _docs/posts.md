---
#title: Writing posts
title: 포스트 작성하기
permalink: /docs/posts/
---

<!--
One of Jekyll’s best aspects is that it is “blog aware”. What does this mean,
exactly? Well, simply put, it means that blogging is baked into Jekyll’s
functionality. If you write articles and publish them online, you can publish
and maintain a blog simply by managing a folder of text-files on your computer.
Compared to the hassle of configuring and maintaining databases and web-based
CMS systems, this will be a welcome change!
-->
Jekyll 의 가장 큰 특징 중 하나는 “블로그 지향적” 이라는 것입니다. 정확히 이게
무슨 뜻일까요? 간단히 말하면, 블로그가 Jekyll 의 기본 기능에 녹아들어 있다는
뜻입니다. 글을 작성하고 온라인에 게시하는 작업을 생각해봅시다.
자신의 컴퓨터 안에 있는 텍스트 파일과 폴더를 관리하는 것 만으로 블로그를 운영할 수 있습니다.
번거로운 데이터베이스 설정과 관리, 그리고 웹-기반 CMS
시스템과 비교해보면 정말 반가운 차이점이죠!

<!--
## The Posts Folder
-->
## 포스트 폴더

<!--
As explained on the [directory structure](../structure/) page, the `_posts`
folder is where your blog posts will live. These files are generally
[Markdown](https://daringfireball.net/projects/markdown/) or HTML, but can
be other formats with the proper converter installed.
All posts must have [YAML Front Matter](../frontmatter/), and they will be
converted from their source format into an HTML page that is part of your
static site.
-->
앞서 [디렉토리 구조](../structure/) 페이지에서 설명했듯이, 블로그 포스트는
`_posts` 폴더에 들어갑니다. 이 파일들은 일반적으로
[마크다운](https://daringfireball.net/projects/markdown/)이나 HTML 이지만,
적절한 변환기가 설치되어 있는 경우에는 다른 포맷일 수도 있습니다.
모든 포스트는 [YAML 머리말](../frontmatter/)을 포함해야만 하고, 최종적으로
원래의 포맷으로부터 변환 작업을 거쳐 당신의 사이트를 구성하는 HTML 페이지가
됩니다.

<!--
### Creating Post Files
-->
### 포스트 파일 생성하기

<!--
To create a new post, all you need to do is create a file in the `_posts`
directory. How you name files in this folder is important. Jekyll requires blog
post files to be named according to the following format:
-->
새 포스트를 생성하려면, `_posts` 디렉토리에 파일을 생성하기만 하면 됩니다.
이 때 중요한 것은 생성하는 파일의 이름입니다. Jekyll 이 이 파일을 블로그
포스트로 인식하게 하려면 파일명을 다음 형식에 맞춰야 합니다:

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

<div class="note">
<!--
  <h5>ProTip™: Link to other posts</h5>
  <p>
    Use the <a href="../templates/#linking-to-posts"><code>post_url</code></a>
    tag to link to other posts without having to worry about the URLs
    breaking when the site permalink style changes.
  </p>
-->
  <h5>ProTip™: 다른 포스트로 링크하기</h5>
  <p>
    <code><a href="../templates/#linking-to-posts">post_url</a></code> 태그를 사용하면
    사이트 고유주소 스타일이 바뀌는 경우에도 URL 이 잘못될 걱정을 할 필요가
    없습니다.
  </p>
</div>

<!--
### Content Formats
-->
### 컨텐츠 포맷

<!--
All blog post files must begin with [YAML Front Matter](../frontmatter/). After
that, it's simply a matter of deciding which format you prefer. Jekyll supports
[Markdown](https://daringfireball.net/projects/markdown/) out of the box,
and has [myriad extensions for other formats as well](/docs/plugins/#converters-1),
including the popular [Textile](http://redcloth.org/textile) format. These
formats each have their own way of marking up different types of content
within a post, so you should familiarize yourself with these formats and
decide which one best suits your needs.
-->
모든 블로그 포스트 파일 첫 부분에는 [YAML 머리말](../frontmatter/)을 작성해야만
합니다. 다음 할 일은 내용 작성에 사용할 포맷을 선택하는 것입니다. Jekyll 은
[마크다운](http://daringfireball.net/projects/markdown/)을 기본적으로 지원하며,
[Textile](http://redcloth.org/textile) 처럼 유명한 포맷 뿐만 아니라 [다른
포맷들을 위한 수많은 확장기능들](/docs/plugins/#converters-1)을 가지고
있습니다. 이 포맷들은 포스트 안의 다양한 컨텐츠를 마크업할 때 각각의 고유한
방식을 사용하므로, 이러한 특징들을 반드시 익혀서 자신의 요구사항에 들어맞는
포맷을 선택해야 합니다.

<div class="note info">
<!--
  <h5>Be aware of character sets</h5>
  <p>
    Content processors can modify certain characters to make them look nicer.
    For example, the <code>smart</code> extension in Redcarpet converts standard,
    ASCII quotation characters to curly, Unicode ones. In order for the browser
    to display those characters properly, define the charset meta value by
    including <code>&lt;meta charset=&quot;utf-8&quot;&gt;</code> in the
    <code>&lt;head&gt;</code> of your layout.
  </p>
-->
  <h5>캐릭터 세트에 주의하세요</h5>
  <p>
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
Chances are, at some point, you'll want to include images, downloads, or other
digital assets along with your text content. While the syntax for linking to
these resources differs between Markdown and Textile, the problem of working
out where to store these files in your site is something everyone will face.
-->
때때로 글 중간에 이미지, 다운로드 또는 그 밖에 다른 종류의 자원을 삽입해야할
때가 있습니다. 사용하는 포맷이 마크다운인지 Textile 인지에 따라 자원을 링크하는
문법에 차이가 있지만, 이 파일을 사이트 어디에 저장할 것인지 결정하는 것은 공통된
문제입니다.

<!--
There are a number of ways to include digital assets in Jekyll.
-->
Jekyll 에 다른 자료를 삽입하는 데에는 여러 가지 방법이 있습니다.

<!--
One common solution is to create a folder in the root of the project directory
called something like `assets`, into which any images, files
or other resources are placed. Then, from within any post, they can be linked
to using the site’s root as the path for the asset to include. Again, this will
depend on the way your site’s (sub)domain and path are configured, but here are
some examples in Markdown of how you could do this using the `absolute_url`
filter in a post.
-->
가장 일반적인 방법 중 하나는 프로젝트의 루트 디렉토리에 `assets` 같은 이름의
디렉토리를 만들고, 이미지와 파일, 그 밖의 다른 자원들을 보관하는 것입니다.
그 다음, 어느 포스트에서든지 링크하는 자원의 경로에 사이트 루트 경로를 포함시키면
됩니다. 다시 한 번 말하지만, 이것은 사이트의 (서브)도메인과 경로의 설정에 따라 각각 방법이 다릅니다. 하지만, 포스트의
`absolute_url` 필터를 사용하여 이 작업을 수행하는 마크다운 예제가 여기
있습니다.

<!--
Including an image asset in a post:
-->
포스트에 이미지를 삽입하려면:

{% raw %}
```markdown
... which is shown in the screenshot below:
![My helpful screenshot]({{ "/assets/screenshot.jpg" | absolute_url }})
```
{% endraw %}

<!--
Linking to a PDF for readers to download:
-->
PDF 다운로드 링크를 삽입하려면:

{% raw %}
```markdown
... you can [get the PDF]({{ "/assets/mydoc.pdf" | absolute_url }}) directly.
```
{% endraw %}

<div class="info">

</div>

<!--
## A typical post
-->
## 일반 포스트

<!--
Jekyll can handle many different iterations of the idea you might associate with a "post," however a standard blog style post, including a Title, Layout, Publishing Date, and Categories might look like this:
-->
이미 Jekyll 은 당신이 "포스트"에 관해 떠올릴 수 있을만한 다양한 아이디어들을 처리할 수 있는 능력을 가지고 있지만, 제목과 레이아웃, 게시일자, 카테고리를 가진 보편화된 블로그 스타일 포스트는 이렇게 생겼습니다:

```markdown
---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-11-17 16:16:01 -0600
categories: jekyll update
---

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `bundle exec jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.
```

<!--
Everything in between the first and second `---` are part of the YAML Front Matter, and everything after the second `---` will be rendered with Markdown and show up as "Content".
-->
처음 두 `---` 사이에 있는 모든 내용은 YAML 머리말에 속하고, 두 번째 `---` 이후의 모든 내용은 마크다운으로 렌더링되어 "컨텐츠"로서 출력될 것입니다.

<!--
## Displaying an index of posts
-->
## 포스트 목록 표시하기

<!--
It’s all well and good to have posts in a folder, but a blog is no use unless
you have a list of posts somewhere. Creating an index of posts on another page
(or in a [template](../templates/)) is easy, thanks to the [Liquid template
language](https://docs.shopify.com/themes/liquid/basics) and its tags. Here’s a
basic example of how to create a list of links to your blog posts:
-->
포스트를 폴더로 관리하는 것은 아무런 문제가 없는 아주 좋은 방법이지만, 어딘가에
포스트 목록을 두지 않는다면 쓸모 없는 블로그가 될 것입니다. 다른 페이지 (또는
[템플릿](../templates/)) 에 포스트 목록을 생성하는 것은 아주 쉬운데, 이것은 바로
[Liquid 템플릿 언어](https://docs.shopify.com/themes/liquid/basics)와 이에 포함된
태그 기능 덕분입니다. 여기, 포스트 링크 목록을 생성하는 기본적인 예시가 있습니다:

{% raw %}
```html
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
Of course, you have full control over how (and where) you display your posts,
and how you structure your site. You should read more about [how templates
work](../templates/) with Jekyll if you want to know more.
-->
물론, 자신의 포스트를 어디에 (그리고 어떻게) 표시할 것인지, 사이트를 어떻게
구성할 것인지는 당신 마음에 달렸습니다. 더 자세한 내용을 알고 싶다면, Jekyll
에서 [템플릿이 작동하는 방법](../templates/)을 읽어보세요.

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
## Displaying post categories or tags
-->
## 포스트의 카테고리와 태그 표시하기

<!--
Hey, that's pretty neat, but what about showing just some of your posts that are
related to each other? For that you can use any of the [variables definable in
Front Matter](https://jekyllrb.com/docs/frontmatter/). In the "typical post"
section you can see how to define categories. Simply add the categories to your
Front Matter as a [yaml
list](https://en.wikipedia.org/wiki/YAML#Basic_components).
-->
어때요, 꽤나 근사하긴 한데, 만약 다른 포스트에 연관된 몇몇 포스트들을 함께
표시해야 하는 경우는 어떻게 할까요? 이와 같은 경우엔 [머리말에 정의할 수 있는
변수들](../frontmatter/)을 사용하면 됩니다.
이미 "일반 포스트" 섹션에서 카테고리를 지정하는 방법을 보았습니다.
단순히 머리말에 [YAML 목록](https://en.wikipedia.org/wiki/YAML#Basic_components)으로
카테고리를 추가하는 것입니다.

<!--
Now that your posts have a category or multiple categories, you can make a page
or a template displaying just the posts in those categories you specify. Here's
a basic example of how to create a list of posts from a specific category.
-->
이제 하나 또는 여러 개의 카테고리가 할당된 포스트가 있으니, 당신이 지정한
카테고리에 속한 포스트들만 표시하는 페이지 또는 템플릿을 만들 수 있습니다. 여기
특정한 카테고리의 포스트 목록을 만드는 방법을 보여주는 간단한 예제가 있습니다.

<!--
First, in the `_layouts` directory create a new file called `category.html` - in
that file put (at least) the following:
-->
먼저, `_layouts` 디렉토리에 `category.html` 이라는 이름의 새 파일을 만듭니다 - 이
파일은 (최소한) 다음 내용을 가지고 있어야 합니다:

{% raw %}
```liquid
---
layout: page
---

{% for post in site.categories[page.category] %}
    <a href="{{ post.url | absolute_url }}">
      {{ post.title }}
    </a>
{% endfor %}
```
{% endraw %}

<!--
Next, in the root directory of your Jekyll install, create a new directory
called `category` and then create a file for each category you want to list. For
example, if you have a category `blog` then create a file in the new directory
called `blog.html` with at least
-->
다음, Jekyll 프로젝트의 최상위 디렉토리에, `category` 라는 이름의
새 디렉토리를 만들고 표시하고자 하는 카테고리별로 파일을 만듭니다.
예를 들어, `blog` 라는 카테고리가 있으면 새 디렉토리에 `blog.html`
이라는 파일을 만들고 다음 내용을 넣습니다.

```yaml
---
layout: category
title: Blog
category: blog
---
```

<!--
In this case, the listing pages will be accessible at `{baseurl}/category/blog.html`
-->
지금과 같은 경우, `{baseurl}/category/blog.html` 로 목록 페이지에 접근할 수 있습니다.

<!--
Although categories and tags are very similar, they are used to group posts,
there are a few differences between them.  Categories and sub-categories create
hierarchies that, by default, are reflected in the directory structure of your
site.  A post with the following header
-->
포스트를 그룹화한다는 점에서 카테고리와 태그는 매우 닮아있지만, 몇 가지 차이점
이 있습니다. 카테고리와 하위 카테고리는, 기본적으로, 계층을 형성해 사이트의
디렉토리 구조에 영향을 줍니다. 다음과 같은 헤더를 가진 포스트는
```yaml
---
layout: post
title: A Trip
category: [ blog, travel ]
---
```
<!--
will be accessible at `{baseurl}/blog/travel/year/month/day/A-Trip.html`.  On
the other hand, a tagged post
-->
`{baseurl}/blog/travel/year/month/day/A-Trip.html` 로 접근할 수 있습니다.
이와는 다르게, 태그된 포스트
```yaml
---
layout: post
title: A Trip
tags: [ blog, travel ]
---
```
<!--
will be saved as `{baseurl}/year/month/day/A-Trip.html`.  It is up to you to
create `{baseurl}/tag/blog.html` and `{baseurl}/tag/travel.html` the same way as
described above for categories.
-->
는 `{baseurl}/year/month/day/A-Trip.html` 에 저장됩니다. 위에 카테고리에 관한 설명처럼 `{baseurl}/tag/blog.html` 을 만들지 `{baseurl}/tag/travel.html` 을 만들지는 당신의 결정에 달려있습니다.

<!--
While this example is done with tags and categories, you can easily extend your
lists to filter by any other variable created with extensions.
-->
이 예제로 태그와 카테고리에 관한 모든 설명이 끝났지만, 목록의 기능을 확장하기
위해서 당신이 직접 만든 어떠한 변수든지 사용할 수 있습니다.

<!--
## Post excerpts
-->
## 포스트 발췌

<!--
Each post automatically takes the first block of text, from the beginning of
the content to the first occurrence of `excerpt_separator`, and sets it in the
post's data hash.
Take the above example of an index of posts. Perhaps you want to include
a little hint about the post's content by adding the first paragraph of each of
your posts:
-->
모든 포스트의 첫 블록 - 컨텐츠 시작부분부터 `excerpt_separator` 가 처음 나오는
부분까지 - 은 포스트의 데이터 해시에 저장됩니다.
위 포스트 목록 예제를 다시 살펴봅시다.
포스트 내용에 대한 작은 힌트를 주기 위해 각 포스트의 첫 문단을 목록에 추가하는
것이 가능합니다:

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

<!--
Because Jekyll grabs the first paragraph you will not need to wrap the excerpt
in `p` tags, which is already done for you. These tags can be removed with the
following if you'd prefer:
-->
발췌된 부분을 일부러 `p` 태그로 감쌀 필요가 없습니다. Jekyll 이 첫 문단을
잡아내어 대신 해주기 때문이죠. 원한다면 다음과 같이 입력하여 태그를 제거할 수도
있습니다:

{% raw %}
```liquid
{{ post.excerpt | remove: '<p>' | remove: '</p>' }}
```
{% endraw %}

<!--
If you don't like the automatically-generated post excerpt, it can be
explicitly overridden by adding an `excerpt` value to your post's YAML
Front Matter. Alternatively, you can choose to define a custom
`excerpt_separator` in the post's YAML front matter:
-->
자동으로 생성된 포스트 발췌가 마음에 들지 않는다면, 포스트의 YAML 머리말에
`excerpt` 변수를 추가하여 직접 원하는 내용으로 덮어쓸 수 있습니다. 아니면,
포스트의 YAML 머리말에 자신만의 `excerpt_separator` 를 정의하는 것도 고려해볼만
합니다:

```yaml
---
excerpt_separator: <!--more-->
---

Excerpt
<!--more-->
Out-of-excerpt
```

<!--
You can also set the `excerpt_separator` globally in your `_config.yml`
configuration file.
-->
자신의 환경설정 파일 `_config.yml` 에 전역적으로 `excerpt_separator` 를
설정하는것도 가능합니다.

<!--
Completely disable excerpts by setting your `excerpt_separator` to `""`.
-->
`excerpt_separator` 를 `""` 로 설정하면 발췌를 완전히 비활성화합니다.

<!--
Also, as with any output generated by Liquid tags, you can pass the
`| strip_html` filter to remove any html tags in the output. This is
particularly helpful if you wish to output a post excerpt as a
`meta="description"` tag within the post `head`, or anywhere else having
html tags along with the content is not desirable.
-->
또한, Liquid 태그로 생성된 모든 결과물에 대해서, `| strip_html` 필터를 추가하여
결과물에 포함된 모든 HTML 태그를 제거할 수 있습니다. 이 필터는 포스트 `head` 의
`meta="description"` 태그 안에 발췌 내용을 넣거나 HTML 태그가 들어가는 것이
부적절한 위치에 발췌 내용을 넣어야 하는 등의 몇몇 특별한 경우에 유용하게 사용할
수 있습니다.

<!--
## Highlighting code snippets
-->
## 코드 구문 강조

<!--
Jekyll also has built-in support for syntax highlighting of code snippets using
either Pygments or Rouge, and including a code snippet in any post is easy.
Just use the dedicated Liquid tag as follows:
-->
Jekyll 에는 Pygments 나 Rouge 를 활용한 코드 구문 강조가 기본적으로 포함되어
있으며, 포스트에 코드 내용을 삽입하는 것 또한 간단합니다. 다음과 같이 전용
Liquid 태그를 사용하기만 하면 됩니다:

{% raw %}
```liquid
{% highlight ruby %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}
```
{% endraw %}

<!--
And the output will look like this:
-->
결과는 이렇게 보일 것입니다:

```ruby
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
```

<div class="note">
<!--
  <h5>ProTip™: Show line numbers</h5>
  <p>
    You can make code snippets include line-numbers by adding the word
    <code>linenos</code> to the end of the opening highlight tag like this:
    <code>{% raw %}{% highlight ruby linenos %}{% endraw %}</code>.
  </p>
-->
  <h5>ProTip™: 줄 번호 표시하기</h5>
  <p>
    다음과 같이 강조 시작 태그 뒷부분에 <code>linenos</code> 를 추가하여 코드에
    줄 번호를 표시할 수 있습니다:
    <code>{% raw %}{% highlight ruby linenos %}{% endraw %}</code>.
  </p>
</div>

<!--
These basics should be enough to get you started writing your first posts. When
you’re ready to dig into what else is possible, you might be interested in
doing things like [customizing post permalinks](../permalinks/) or
using [custom variables](../variables/) in your posts and elsewhere on your
site.
-->
이로써 포스트를 작성하는데에 필요한 기초지식은 충분히 살펴보았습니다. 이 밖에 또
할 수 있는 것이 뭐가 있는지 좀 더 파고들 준비가 되면, [포스트 고유주소
수정](../permalinks/) 방법이나 포스트에 (뿐만 아니라 당신의 사이트 어느 곳에든)
[사용자 변수](../variables/)를 사용하는 방법 등에 관심을 가져보는 것도 좋습니다.

