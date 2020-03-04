---
#title: Tags Filters
title: 태그 필터
permalink: "/docs/liquid/tags/"
---
<!--
All of the standard Liquid
[tags](https://shopify.github.io/liquid/tags/control-flow/) are supported.
Jekyll has a few built in tags to help you build your site. You can also create
your own tags using [plugins](/docs/plugins/).
-->
표준 Liquid
[태그](https://shopify.github.io/liquid/tags/control-flow/)를 모두 지원합니다.
사이트 빌드를 돕는 태그도 몇 개 Jekyll 에 기본내장되어 있습니다. 게다가
[플러그인](/docs/plugins/)을 사용하면 자신만의 필터도 만들 수 있습니다.

<!--
## Includes
-->
## 조각파일

<!--
If you have page snippets that you use repeatedly across your site, an
[include](/docs/includes/) is the perfect way to make this more maintainable.
-->
사이트의 여기저기에 반복적으로 사용하는 페이지 토막이 있다면,
[조각파일](/docs/includes/)로 이러한 작업을 관리하는 것이 최선의 선택입니다.

<!--
## Code snippet highlighting
-->
## 코드 구문 강조

<!--
Jekyll has built in support for syntax highlighting of over 100 languages
thanks to [Rouge](http://rouge.jneen.net). Rouge is the default highlighter
in Jekyll 3 and above.
-->
[Rouge](http://rouge.jneen.net) 덕분에 Jekyll 은 100 개 이상의 언어에
대한 구문 강조 기능을 내장하고 있습니다.
Jekyll 3 와 그 이상의 버전에서는 Rouge 가 기본 구문 강조기입니다.

<div class="note warning">
<!--
  <p>Using Pygments has been deprecated and is not supported in
  Jekyll 4, the configuration setting <code>highlighter: pygments</code>
  now automatically falls back to using <em>Rouge</em> which is written in Ruby
  and 100% compatible with stylesheets for Pygments.</p>
-->
  <p>Pygments 를 사용하는 것은 권장되지 않았었고 현재 Jekyll 4 에서는
  지원되지 않기 때문에, 환경설정의 <code>highlighter: pygments</code> 는
  이제 자동으로 루비로 작성된 <em>Rough</em> 를 사용하게 바뀌며
  Pygments 용 스타일시트와 100% 호환됩니다.</p>
</div>

<!--
To render a code block with syntax highlighting, surround your code as follows:
-->
구문 강조가 적용된 코드 블럭을 출력하려면, 코드 앞뒤에 다음과 같이 작성합니다:

{% raw %}
```liquid
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}
```
{% endraw %}

<!--
The argument to the `highlight` tag (`ruby` in the example above) is the
language identifier. To find the appropriate identifier to use for the language
you want to highlight, look for the “short name” on the [Rouge
wiki](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers).
-->
`highlight` 태그에 전달한 인자 (위 예시에서는 `ruby`) 는
언어 식별자입니다. 각 언어에 해당하는 구문 강조용 식별자를
찾으려면, [Rouge
위키](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers)에서 “short name” 을 살펴보세요.

<div class="note">
<!--
  <h5>Jekyll processes all Liquid filters in code blocks</h5>
-->
  <h5>Jekyll 은 코드 블록 안에서도 Liquid 필터를 처리합니다</h5>
<!--
  <p>If you are using a language that contains curly braces, you
    will likely need to place <code>{&#37; raw &#37;}</code> and
    <code>{&#37; endraw &#37;}</code> tags around your code.
    Since {% include docs_version_badge.html version="4.0" %} you can add <code>render_with_liquid: false</code> in your front matter to disable Liquid entirely for a particular document.</p>
-->
  <p>만약 당신이 사용하려는 언어에 중괄호가 포함되어 있다면, 당신의
    코드 앞 뒤를 <code>{&#37; raw &#37;}</code> 와
    <code>{&#37; endraw &#37;}</code> 태그로 감싸야 할 것입니다.
    {% include docs_version_badge.html version="4.0" %} 버전부터 머리말에 <code>render_with_liquid: false</code> 를 추가해 문서 전체의 Liquid 를 비활성화할 수 있습니다.</p>
</div>

<!--
### Line numbers
-->
### 줄 번호

<!--
There is a second argument to `highlight` called `linenos` that is optional.
Including the `linenos` argument will force the highlighted code to include line
numbers. For instance, the following code block would include line numbers next
to each line:
-->
`highlight` 의 두 번째 파라메터인 `linenos` 는 선택사항입니다.
파라메터 `linenos` 를 추가하면 구문 강조된 코드에 줄 번호를
표시합니다. 예를 들어, 다음 코드 블록에는 각 줄에 줄 번호가
표시됩니다:

{% raw %}
```liquid
{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}
```
{% endraw %}

<!--
### Stylesheets for syntax highlighting
-->
### 구문 강조용 스타일시트

<!--
In order for the highlighting to show up, you’ll need to include a highlighting
stylesheet. For Pygments or Rouge you can use a stylesheet for Pygments, you
can find an example gallery 
[here](https://jwarby.github.io/jekyll-pygments-themes/languages/ruby.html) 
or from [its repository](https://github.com/jwarby/jekyll-pygments-themes).
-->
구문 강조를 작동시키려면, 구문 강조용 스타일시트를 추가해야 합니다.
Pygments 용 스타일시트를 Pygments 나 Rouge 에 사용할 수 있습니다.
예제 갤러리를
[여기](https://jwarby.github.io/jekyll-pygments-themes/languages/ruby.html)나
[해당 저장소](https://github.com/jwarby/jekyll-pygments-themes)에서 볼 수 있습니다.

<!--
Copy the CSS file (`native.css` for example) into your css directory and import
the syntax highlighter styles into your `main.css`:
-->
CSS 파일 (예를 들어 `native.css`) 을 css 디렉토리에 복사하고
`main.css` 에 구문강조 스타일을 임포트합니다:

```css
@import "native.css";
```

<!--
## Links
-->
## 링크

{: .note }
<!--
Since Jekyll {% include docs_version_badge.html version="v4.0"%} you don't need to prepend `link` and `post_url` tags with `site.baseurl`
-->
Jekyll {% include docs_version_badge.html version="v4.0"%} 부터 `link` 와 `post_url` 태그 앞에 `site.baseurl` 을 사용할 필요가 없습니다.

<!--
### Linking to pages {#link}
-->
### 페이지에 연결하기 {#link}

<!--
To link to a post, a page, collection item, or file, the `link` tag will generate the correct permalink URL for the path you specify. For example, if you use the `link` tag to link to `mypage.html`, even if you change your permalink style to include the file extension or omit it, the URL formed by the `link` tag will always be valid.
-->
게시물, 페이지, 콜렉션 항목 또는 파일에 연결하기 위해, `link` 태그가 당신이 지정한 경로에 대해 올바른 고유주소 URL 을 생성할 것입니다. 예를 들어, `mypage.html` 에 연결하기 위해 `link` 태그를 사용하면, 당신이 고유주소 스타일에 파일 확장자를 포함하도록 또는 포함하지 않도록 변경하더라도, `link` 태그는 언제나 올바른 URL 을 생성할 것입니다.

<!--
You must include the file's original extension when using the `link` tag. Here are some examples:
-->
`link` 태그를 사용할 때에는 반드시 파일을 실제 확장자를 명시해야 합니다. 여기 예시가 몇 개 있습니다:

{% raw %}
```liquid
{% link _collection/name-of-document.md %}
{% link _posts/2016-07-26-name-of-post.md %}
{% link news/index.html %}
{% link /assets/files/doc.pdf %}
```
{% endraw %}

<!--
You can also use the `link` tag to create a link in Markdown as follows:
-->
다음과 같이 마크다운 안에서도 `link` 태그를 사용해 링크를 생성할 수 있습니다:

{% raw %}
```liquid
[Link to a document]({% link _collection/name-of-document.md %})
[Link to a post]({% link _posts/2016-07-26-name-of-post.md %})
[Link to a page]({% link news/index.html %})
[Link to a file]({% link /assets/files/doc.pdf %})
```
{% endraw %}

<!--
The path to the post, page, or collection is defined as the path relative to the root directory (where your config file is) to the file, not the path from your existing page to the other page.
-->
게시물, 페이지 또는 콜렉션의 경로는 현재 페이지로부터 다른 페이지로의 상대 경로가 아니라, 최상위 디렉토리(환경설정 파일이 있는 위치)에서 해당 파일에 대한 상대 경로로 결정됩니다.

<!--
For example, suppose you're creating a link in `page_a.md` (stored in `pages/folder1/folder2`) to `page_b.md` (stored in  `pages/folder1`). Your path in the link would not be `../page_b.html`. Instead, it would be `/pages/folder1/page_b.md`.
-->
예를 들어, `page_a.md` (`pages/folder1/folder2` 에 저장되어 있음) 에 `page_b.md` (`pages/folder1` 에 저장되어 있음) 로의 링크를 생성한다고 생각해봅시다. 이 링크의 경로는 `../page_b.html` 이 아닙니다. 경로는 `/pages/folder1/page_b.md` 입니다.

<!--
If you're unsure of the path, add `{% raw %}{{ page.path }}{% endraw %}` to the page and it will display the path.
-->
정확한 경로를 모르겠다면, 해당 페이지에 `{% raw %}{{ page.path }}{% endraw %}` 를 추가해서 경로를 표시할 수 있습니다.

<!--
One major benefit of using the `link` or `post_url` tag is link validation. If the link doesn't exist, Jekyll won't build your site. This is a good thing, as it will alert you to a broken link so you can fix it (rather than allowing you to build and deploy a site with broken links).
-->
이 `link` 나 `post_url` 태그를 사용하는 가장 큰 장점은 링크 유효성 검사입니다. 해당 링크가 존재하지 않는다면, Jekyll 은 사이트를 빌드하지 않을 것입니다. 이는 깨진 링크에 대한 경고를 주어 고칠 기회를 얻을 수 있으므로 장점이라고 할 수 있습니다 (그렇지 않으면 깨진 링크를 가진 사이트를 배포하게 될 것입니다).

<!--
Note you cannot add filters to `link` tags. For example, you cannot append a string using Liquid filters, such as `{% raw %}{% link mypage.html | append: "#section1" %} {% endraw %}`. To link to sections on a page, you will need to use regular HTML or Markdown linking techniques.
-->
`link` 태그에는 필터를 추가할 수 없다는 것을 알아두세요. 예를 들어, `{% raw %}{% link mypage.html | append: "#section1" %} {% endraw %}` 처럼 Liquid 필터를 사용해 문자열을 추가할 수 없습니다. 페이지의 특정 부분에 링크하기 위해서는, 기본 HTML 링크나 마크다운 링크 방식을 사용해야 합니다.

<!--
### Linking to posts
-->
### 게시물에 연결하기

<!--
If you want to include a link to a post on your site, the `post_url` tag will generate the correct permalink URL for the post you specify.
-->
당신의 사이트 내 게시물에 대한 링크가 필요한 경우, `post_url` 태그를 사용하면 원하는 게시물에 대한 올바른 고유주소를 만들 수 있습니다.

{% raw %}
```liquid
{% post_url 2010-07-21-name-of-post %}
```
{% endraw %}

<!--
If you organize your posts in subdirectories, you need to include subdirectory path to the post:
-->
만약 게시물을 하위 디렉토리에 넣고 관리한다면, 하위 디렉토리 경로도 포함시켜야 합니다:

{% raw %}
```liquid
{% post_url /subdir/2010-07-21-name-of-post %}
```
{% endraw %}

<!--
There is no need to include the file extension when using the `post_url` tag.
-->
`post_url` 태그를 사용할 때는 파일 확장자를 지정할 필요가 없습니다.

<!--
You can also use this tag to create a link to a post in Markdown as follows:
-->
다음과 같이 마크다운에서도 이 태그를 사용하여 게시물 링크를 생성할 수 있습니다:

{% raw %}
```liquid
[Name of Link]({% post_url 2010-07-21-name-of-post %})
```
{% endraw %}
