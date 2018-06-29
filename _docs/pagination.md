---
#title: Pagination
title: 페이지 나누기
permalink: /docs/pagination/
---

<!--
With many websites &mdash; especially blogs &mdash; it’s very common to
break the main listing of posts up into smaller lists and display them over
multiple pages. Jekyll offers a pagination plugin, so you can automatically
generate the appropriate files and folders you need for paginated listings.
-->
많은 웹사이트 &mdash; 특히 블로그 &mdash; 들에서 전체 포스트 목록을 작은
목록으로 나누어 여러 페이지로 보여주는 방법을 보통 많이들 사용합니다. Jekyll 은
페이지 나누기 플러그인을 제공하기 때문에, 여러 페이지로 목록을 나눌 때 필요한
파일과 폴더들을 자동으로 생성할 수 있습니다.

<!--
For Jekyll 3, include the `jekyll-paginate` plugin in your Gemfile and in
your `_config.yml` under `plugins`. For Jekyll 2, this is standard.
-->
Jekyll 3 에서는, Gemfile 과 `_config.yml` 의 `plugins` 에 `jekyll-paginate` 를
추가하세요. Jekyll 2 에는 기본적으로 포함되어 있습니다.

<div class="note info">
<!--
  <h5>Pagination only works within HTML files</h5>
  <p>
    Pagination does not work from within Markdown or Textile files from
    your Jekyll site. Pagination works when called from within the HTML
    file, named <code>index.html</code>, which optionally may reside in and
    produce pagination from within a subdirectory, via the
    <code>paginate_path</code> configuration value.
  </p>
-->
  <h5>페이지 나누기는 오직 HTML 파일에서만 작동합니다</h5>
  <p>
    페이지 나누기는 마크다운이나 Textile 파일 안에서 작동하는 것이 아닙니다. 페이지
    나누기는 파일명이 <code>index.html</code> 인 HTML 파일 안에서 호출되거나
    환경설정 <code>paginate_path</code> 로 설정된 하위 디렉토리 안에서 동작합니다.


  </p>
</div>

<!--
## Enable pagination
-->
## 페이지 나누기 활성화

<!--
To enable pagination for posts on your blog, add a line to the `_config.yml` file that
specifies how many items should be displayed per page:
-->
포스트에 페이지 나누기 기능을 사용하려면, 한 페이지에 보여주는 항목 개수에
대한 설정을 `_config.yml` 파일에 추가하세요:

```yaml
paginate: 5
```

<!--
The number should be the maximum number of Posts you’d like to be displayed
per-page in the generated site.
-->
생성된 사이트의 한 페이지 당 표시하고자 하는 포스트의 최대 개수를 입력하면
됩니다.

<!--
You may also specify the destination of the pagination pages:
-->
이렇게 나뉘어진 페이지가 생성될 위치도 지정할 수 있습니다:

```yaml
paginate_path: "/blog/page:num/"
```

<!--
This will read in `blog/index.html`, send it each pagination page in Liquid as
`paginator` and write the output to `blog/page:num/`, where `:num` is the
pagination page number, starting with `2`. If a site has 12 posts and specifies
`paginate: 5`, Jekyll will write `blog/index.html` with the first 5 posts, `blog/page2/index.html` with the next 5 posts
and `blog/page3/index.html` with the last 2 posts into the destination
directory.
-->
이 설정은 `blog/index.html` 에서 사용되어, 나뉘어진 각 페이지는 이 값을
`paginator` 라는 Liquid 로 받게 되며 결과물은 `blog/page:num/` 에 만들어집니다.
여기서 `:num` 은 `2` 부터 시작하는 페이지 번호입니다. 사이트가 12 개의 포스트를
가지고 있고 `pagenate: 5` 라고 설정되어 있는 경우, Jekyll 은 처음 5 개의
포스트로 `blog/index.html` 을 만들고, 다음 5 개의 포스트로 `blog/page2/index.html` 을,
마지막 2 개의 포스트로는 `blog/page3/index.html` 을 만들게 됩니다.

<div class="note warning">
<!--
  <h5>Don't set a permalink</h5>
  <p>
    Setting a permalink in the front matter of your blog page will cause
    pagination to break. Just omit the permalink.
  </p>
-->
  <h5>고유주소 설정은 하지 마세요</h5>
  <p>
    블로그 페이지의 머리말에 고유주소를 설정하면 페이지 나누기가 작동하지
    않습니다. 고유주소는 설정하지 마세요.
  </p>
</div>

<div class="note info">
<!--
  <h5>Pagination for categories, tags and collections</h5>
  <p>
    The more recent <a href="https://github.com/sverrirs/jekyll-paginate-v2">jekyll-paginate-v2</a> plugin supports more features. See the <a href="https://github.com/sverrirs/jekyll-paginate-v2/tree/master/examples">pagination examples</a> in the repository.
    <strong>This plugin is not supported by GitHub Pages</strong>.
  </p>
-->
  <h5>카테고리와 태그, 콜렉션의 페이지 나누기</h5>
  <p>
    최신 버전의 <a href="https://github.com/sverrirs/jekyll-paginate-v2">jekyll-paginate-v2</a> 플러그인은 더 많은 기능을 지원합니다. 저장소에서 <a href="https://github.com/sverrirs/jekyll-paginate-v2/tree/master/examples">페이지 나누기 예제</a>를 살펴보세요.
    <strong>GitHub Pages 에서는 이 플러그인을 지원하지 않습니다</strong>.
  </p>
</div>

<!--
## Liquid Attributes Available
-->
## 사용가능한 Liquid 속성

<!--
The pagination plugin exposes the `paginator` liquid object with the following
attributes:
-->
페이지 나누기 플러그인이 제공하는 Liquid 객체 `paginator` 의 속성은 다음과
같습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Attribute</th>
      <th>Description</th>
-->
      <th>속성</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
<!--
      <td><p><code>page</code></p></td>
      <td><p>current page number</p></td>
-->
      <td><p><code>page</code></p></td>
      <td><p>현재 페이지 번호</p></td>
    </tr>
    <tr>
<!--
      <td><p><code>per_page</code></p></td>
      <td><p>number of posts per page</p></td>
-->
      <td><p><code>per_page</code></p></td>
      <td><p>페이지 당 포스트 개수</p></td>
    </tr>
    <tr>
<!--
      <td><p><code>posts</code></p></td>
      <td><p>a list of posts for the current page</p></td>
-->
      <td><p><code>posts</code></p></td>
      <td><p>현재 페이지의 포스트 목록</p></td>
    </tr>
    <tr>
<!--
      <td><p><code>total_posts</code></p></td>
      <td><p>total number of posts in the site</p></td>
-->
      <td><p><code>total_posts</code></p></td>
      <td><p>사이트의 전체 포스트 개수</p></td>
    </tr>
    <tr>
<!--
      <td><p><code>total_pages</code></p></td>
      <td><p>number of pagination pages</p></td>
-->
      <td><p><code>total_pages</code></p></td>
      <td><p>전체 페이지 수</p></td>
    </tr>
    <tr>
<!--
      <td><p><code>previous_page</code></p></td>
      <td>
          <p>
              page number of the previous pagination page,
              or <code>nil</code> if no previous page exists
          </p>
      </td>
-->
      <td><p><code>previous_page</code></p></td>
      <td>
          <p>
              이전 페이지 번호,
              없으면 <code>nil</code>
          </p>
      </td>
    </tr>
    <tr>
<!--
      <td><p><code>previous_page_path</code></p></td>
      <td>
          <p>
              path of previous pagination page,
              or <code>nil</code> if no previous page exists
          </p>
      </td>
-->
      <td><p><code>previous_page_path</code></p></td>
      <td>
          <p>
              이전 페이지 경로,
              없으면 <code>nil</code>
          </p>
      </td>
    </tr>
    <tr>
<!--
      <td><p><code>next_page</code></p></td>
      <td>
          <p>
              page number of the next pagination page,
              or <code>nil</code> if no subsequent page exists
          </p>
      </td>
-->
      <td><p><code>next_page</code></p></td>
      <td>
          <p>
              다음 페이지 번호,
              없으면 <code>nil</code>
          </p>
      </td>
    </tr>
    <tr>
<!--
      <td><p><code>next_page_path</code></p></td>
      <td>
          <p>
              path of next pagination page,
              or <code>nil</code> if no subsequent page exists
          </p>
      </td>
-->
      <td><p><code>next_page_path</code></p></td>
      <td>
          <p>
              다음 페이지 경로,
              없으면 <code>nil</code>
          </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note info">
<!--
  <h5>Pagination does not support tags or categories</h5>
  <p>Pagination pages through every post in the <code>posts</code>
  variable unless a post has <code>hidden: true</code> in its YAML Front Matter.
  It does not currently allow paging over groups of posts linked
  by a common tag or category. It cannot include any collection of
  documents because it is restricted to posts.</p>
-->
  <h5>페이지 나누기는 태그나 카테고리를 지원하지 않습니다</h5>
  <p>페이지 나누기는 각 포스트의 YAML 머리말에
  <code>hidden: true</code> 가 없는 한 <code>posts</code> 변수 안의 모든 포스트를 나눕니다.
  태그나 카테고리로 구분된 포스트 묶음을 페이지로 나누는 것은
  현재 허용되지 않습니다.  포스트에만 국한되기 때문에
  문서 콜렉션에도 적용할 수 없습니다.</p>
</div>

<!--
## Render the paginated Posts
-->
## 페이지로 나눠진 포스트 렌더링하기

<!--
The next thing you need to do is to actually display your posts in a list using
the `paginator` variable that will now be available to you. You’ll probably
want to do this in one of the main pages of your site. Here’s one example of a
simple way of rendering paginated Posts in a HTML file:
-->
그 다음 해야 할 일은 목록에 들어있는 포스트를 `paginator` 변수를 사용하여 실제로
출력하는 것입니다. 보통은 사이트의 메인 페이지들 중 하나에 이 작업을 하게 될
것입니다. 여러 페이지로 나뉘어진 포스트를 HTML 파일에 표시하는 방법 중 하나가
여기 있습니다:

{% raw %}
```liquid
---
layout: default
title: My Blog
---

<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
  <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="date">{{ post.date }}</span>
  </p>
  <div class="content">
    {{ post.content }}
  </div>
{% endfor %}

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" class="previous">Previous</a>
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">Page: {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>
```
{% endraw %}

<div class="note warning">
<!--
  <h5>Beware the page one edge-case</h5>
  <p>
    Jekyll does not generate a ‘page1’ folder, so the above code will not work
    when a <code>/page1</code> link is produced. See below for a way to handle
    this if it’s a problem for you.
  </p>
-->
  <h5>첫 페이지 경계조건에 주의하세요</h5>
  <p>
    Jekyll 은 ‘page1’ 폴더를 생성하지 않기 때문에, 위 코드는 <code>/page1</code>
    링크에 대하여 올바르게 작동하지 않습니다.
    만약 이것이 문제가 된다면 아래에서 설명하는 방법을 참고하세요.
  </p>
</div>

<!--
The following HTML snippet should handle page one, and render a list of each
page with links to all but the current page.
-->
아래 HTML 코드는 첫 번째 페이지와 함께 나머지 페이지들의 링크도 올바르게
처리합니다.

{% raw %}
```liquid
{% if paginator.total_pages > 1 %}
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a>
  {% else %}
    <span>&laquo; Prev</span>
  {% endif %}

  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
      <em>{{ page }}</em>
    {% elsif page == 1 %}
      <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
    {% else %}
      <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  {% endfor %}

  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a>
  {% else %}
    <span>Next &raquo;</span>
  {% endif %}
</div>
{% endif %}
```
{% endraw %}
