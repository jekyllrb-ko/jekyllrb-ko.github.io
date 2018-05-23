---
#title: Variables
title: 변수
permalink: /docs/variables/
---

<!--
Jekyll traverses your site looking for files to process. Any files with [YAML
front matter](../frontmatter/) are subject to processing. For each of these
files, Jekyll makes a variety of data available via the [Liquid templating
system](https://github.com/Shopify/liquid/wiki). The
following is a reference of the available data.
-->
Jekyll 은 작업이 필요한 파일을 찾아 사이트 내부를 이리저리 돌아다닙니다. 작업
대상은 [YAML 머리말](../frontmatter/)을 가진 모든 파일입니다. Jekyll 은 [Liquid
템플릿 시스템](https://github.com/Shopify/liquid/wiki)을 통해 각각의 작업 대상
파일마다 다양한 데이터를 생성합니다. 사용할 수 있는 데이터 목록은 다음과
같습니다.

<!--
## Global Variables
-->
## 전역 변수

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
      <td><p><code>site</code></p></td>
      <td><p>

<!--
          Sitewide information + configuration settings from
          <code>_config.yml</code>. See below for details.
-->
          사이트 정보 + <code>_config.yml</code> 의 환경설정 정보. 더 자세한
          내용은 아래를 참조하시오.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page</code></p></td>
      <td><p>

<!--
        Page specific information + the <a href="../frontmatter/">YAML front
        matter</a>. Custom variables set via the YAML Front Matter will be
        available here. See below for details.
-->
        해당 페이지 고유 정보 + <a href="../frontmatter/">YAML 머리말</a>. YAML
        머리말에 설정한 사용자 변수도 여기에 포함된다. 더 자세한 내용은 아래를
        참조하시오.

      </p></td>
    </tr>
    <tr>
      <td><p><code>layout</code></p></td>
      <td><p>

        Layout specific information + the <a href="../frontmatter/">YAML front
        matter</a>. Custom variables set via the YAML Front Matter in
        layouts will be available here.

      </p></td>
    </tr>
    <tr>
      <td><p><code>content</code></p></td>
      <td><p>

<!--
        In layout files, the rendered content of the Post or Page being wrapped.
        Not defined in Post or Page files.
-->
        레이아웃에 포함된 포스트 또는 페이지 컨텐츠. 포스트나 페이지 파일에는
        정의되어 있지 않다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>paginator</code></p></td>
      <td><p>

<!--
        When the <code>paginate</code> configuration option is set, this
        variable becomes available for use. See <a
        href="../pagination/">Pagination</a> for details.
-->
        이 변수는 환경설정 옵션 <code>paginate</code> 가 설정되어 있을 때 사용할
        수 있다. 더 자세한 내용에 대해서는 <a href="../pagination/">페이지
        나누기</a>를 참조하시오.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Site Variables
-->
## 사이트 변수

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
      <td><p><code>site.time</code></p></td>
      <td><p>

<!--
        The current time (when you run the <code>jekyll</code> command).
-->
        현재 시간 (<code>jekyll</code> 명령을 실행한 시간).

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.pages</code></p></td>
      <td><p>

<!--
        A list of all Pages.
-->
        모든 페이지 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.posts</code></p></td>
      <td><p>

<!--
        A reverse chronological list of all Posts.
-->
        시간 역순의 모든 포스트 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.related_posts</code></p></td>
      <td><p>

<!--
        If the page being processed is a Post, this contains a list of up to ten
        related Posts. By default, these are the ten most recent posts.
        For high quality but slow to compute results, run the
        <code>jekyll</code> command with the <code>--lsi</code> (<a href="https://en.wikipedia.org/wiki/Latent_semantic_analysis#Latent_semantic_indexing">latent semantic indexing</a>) option. Also note GitHub Pages does not support the <code>lsi</code> option when generating sites.
-->
        처리중인 파일이 포스트인 경우에, 최대 10 개의 연관 포스트 목록이 이
        변수에 할당된다. 디폴트로 가장 최신 포스트 10 개를 가리킨다. 느린 속도를
        감수하고 고품질의 결과를 얻으려면, <code>jekyll</code>명령을
        <code>--lsi</code> (<a href="https://en.wikipedia.org/wiki/Latent_semantic_analysis#Latent_semantic_indexing">latent semantic indexing</a>) 옵션과 함께 실행하시오.
        단, GitHub Pages 가 사이트를 생성할 때는 <code>lsi</code> 옵션을 지원하지 않는다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.static_files</code></p></td>
      <td><p>

<!--
        A list of all <a href="/docs/static-files/">static files</a> (i.e.
        files not processed by Jekyll's converters or the Liquid renderer).
        Each file has three properties: <code>path</code>,
        <code>modified_time</code> and <code>extname</code>.
-->
        <a href="/docs/static-files/">정적 파일</a> (다시 말해, Jekyll 의
        변환기나 Liquid 렌더러가 처리하지 않는 파일들) 전체 목록. 모든 파일은 세
        가지 속성을 갖고 있다: <code>path</code> 와 <code>modified_time</code>,
        <code>extname</code>.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.html_pages</code></p></td>
      <td><p>

<!--
        A subset of `site.pages` listing those which end in `.html`.
-->
        `.html` 로 끝나는 `site.pages` 목록의 하위 세트.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.html_files</code></p></td>
      <td><p>

<!--
        A subset of `site.static_files` listing those which end in `.html`.
-->
        `.html` 로 끝나는 `site.static_files` 목록의 하위 세트.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.collections</code></p></td>
      <td><p>

<!--
        A list of all the collections.
-->
        모든 콜렉션 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.data</code></p></td>
      <td><p>

<!--
        A list containing the data loaded from the YAML files located in the <code>_data</code> directory.
-->
        <code>_data</code> 디렉토리 안의 YAML 파일에서 읽어들인 데이터 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.documents</code></p></td>
      <td><p>

<!--
        A list of all the documents in every collection.
-->
        각 콜렉션의 모든 문서 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.categories.CATEGORY</code></p></td>
      <td><p>

<!--
        The list of all Posts in category <code>CATEGORY</code>.
-->
        <code>CATEGORY</code> 카테고리에 속한 모든 포스트 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.tags.TAG</code></p></td>
      <td><p>

<!--
        The list of all Posts with tag <code>TAG</code>.
-->
        <code>TAG</code> 태그가 붙은 모든 포스트 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.url</code></p></td>
      <td><p>

        Contains the url of your site as it is configured in the <code>_config.yml</code>.
        For example, if you have <code>url: http://mysite.com</code>
        in your configuration file, then it will be accessible in Liquid as
        <code>site.url</code>. For the development environment there is
        <a href="/news/#3-siteurl-is-set-by-the-development-server">an exception</a>,
        if you are running <code>jekyll serve</code> in a development environment
        <code>site.url</code> will be set to the value of <code>host</code>,
        <code>port</code>, and SSL-related options. This defaults to
        <code>url: http://localhost:4000</code>.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.[CONFIGURATION_DATA]</code></p></td>
      <td><p>

<!--
        All the variables set via the command line and your
        <code>_config.yml</code> are available through the <code>site</code>
        variable. For example, if you have <code>foo: bar</code>
        in your configuration file, then it will be accessible in Liquid as <code>site.foo</code>.
        Jekyll does not parse changes to <code>_config.yml</code> in
        <code>watch</code> mode, you must restart Jekyll to see changes to variables.
-->
        명령행이나 <code>_config.yml</code> 을 통해 설정된 모든 변수들은
        <code>site</code> 변수를 통해 사용할 수 있다. 예를 들어, 환경설정 파일에
        <code>foo: bar</code> 가 있다면, <code>site.foo</code> 와 같이 Liquid 로 접근할 수 있다.
        <code>watch</code> 모드가 켜진 경우에도 <code>_config.yml</code> 파일의 변경사항은 자동으로
        적용되지 않기 때문에, 변경된 변수를 적용하려면 Jekyll 을 재시작해야
        한다.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Page Variables
-->
## 페이지 변수

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
      <td><p><code>page.content</code></p></td>
      <td><p>

<!--
        The content of the Page, rendered or un-rendered depending upon
        what Liquid is being processed and what <code>page</code> is.
-->
        페이지의 컨텐츠. 어떤 Liquid 처리가 되었는지, 어떤 <code>page</code>
        인지에 따라 렌더링 되었을 수도 아닐 수도 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.title</code></p></td>
      <td><p>

<!--
        The title of the Page.
-->
        페이지의 제목.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.excerpt</code></p></td>
      <td><p>

<!--
        The un-rendered excerpt of a document.
-->
        렌더링 되지 않은, 문서의 발췌 부분.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.url</code></p></td>
      <td><p>

<!--
        The URL of the Post without the domain, but
        with a leading slash, e.g.
        <code>/2008/12/14/my-post.html</code>
-->
        도메인을 제외하고,
        슬래시 문자로 시작하는 포스트 URL. 예시,
        <code>/2008/12/14/my-post.html</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.date</code></p></td>
      <td><p>

<!--
        The Date assigned to the Post. This can be overridden in a Post’s front
        matter by specifying a new date/time in the format
        <code>YYYY-MM-DD HH:MM:SS</code> (assuming UTC), or
        <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code> (to specify a time zone using
        an offset from UTC. e.g. <code>2008-12-14 10:30:00 +0900</code>).
-->
        포스트에 할당된 날짜.
        포스트의 머리말에 <code>YYYY-MM-DD HH:MM:SS</code> (UTC 기준),
        또는 <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code>
        (UTC 오프셋을 사용한 타임 존 지정. 예시, <code>2008-12-14 10:30:00 +0900</code>)
        형식으로 새로운 날짜/시간을 지정하여 덮어쓸 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.id</code></p></td>
      <td><p>

<!--
        An identifier unique to a document in a Collection or a Post (useful in RSS feeds). e.g.
-->
        포스트나 콜렉션의 문서에 대한 유일한 식별자 (RSS 피드에 유용함). 예시,
        <code>/2008/12/14/my-post</code>
        <code>/my-collection/my-document</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.categories</code></p></td>
      <td><p>

<!--
        The list of categories to which this post belongs. Categories are
        derived from the directory structure above the <code>_posts</code>
        directory. For example, a post at
        <code>/work/code/_posts/2008-12-24-closures.md</code> would have this
        field set to <code>['work', 'code']</code>. These can also be specified
        in the <a href="../frontmatter/">YAML Front Matter</a>.
-->
        이 포스트가 속한 카테고리들의 목록. <code>_posts</code> 디렉토리의 상위
        디렉토리 구조가 카테고리를 결정한다. 예를 들어,
        경로가 <code>/work/code/_posts/2008-12-24-closures.md</code> 인
        포스트에서는 이 변수가 <code>['work', 'code']</code> 로 설정되어 있다.
        이 변수는 <a href="../frontmatter/">YAML 머리말</a>에서도 설정할 수
        있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.tags</code></p></td>
      <td><p>

<!--
        The list of tags to which this post belongs. These can be specified in
        the <a href="../frontmatter/">YAML Front Matter</a>.
-->
        포스트에 붙어있는 태그 목록. 이 변수는 <a href="../frontmatter/">YAML
        머리말</a>에 설정할 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.path</code></p></td>
      <td><p>

<!--
        The path to the raw post or page. Example usage: Linking back to the
        page or post’s source on GitHub. This can be overridden in the
        <a href="../frontmatter/">YAML Front Matter</a>.
-->
        페이지 또는 포스트의 실제 경로. 활용 예시: 페이지 또는 포스트에 대한
        GitHub 소스를 링크하기. 이 변수는 <a href="../frontmatter/">YAML
        머리말</a>에서 덮어쓸 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.next</code></p></td>
      <td><p>

<!--
        The next post relative to the position of the current post in
        <code>site.posts</code>. Returns <code>nil</code> for the last entry.
-->
        <code>site.posts</code> 의 포스트 중에서 현재 포스트 위치를 기준으로 한
        다음 포스트의 상대 경로. 마지막 항목이라면 <code>nil</code> 을 반환한다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.previous</code></p></td>
      <td><p>

<!--
        The previous post relative to the position of the current post in
        <code>site.posts</code>. Returns <code>nil</code> for the first entry.
-->
        <code>site.posts</code> 의 포스트 중에서 현재 포스트 위치를 기준으로 한
        이전 포스트의 상대 경로. 첫 번째 항목이라면 <code>nil</code> 을 반환한다.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
<!--
  <h5>ProTip™: Use Custom Front Matter</h5>
  <p>

    Any custom front matter that you specify will be available under
    <code>page</code>. For example, if you specify <code>custom_css: true</code>
    in a page’s front matter, that value will be available as
    <code>page.custom_css</code>.

  </p>
-->
  <h5>ProTip™: 사용자 머리말을 사용하세요</h5>
  <p>

    모든 사용자 머리말은 <code>page</code> 로 사용할 수 있습니다.
    예를 들어,
    페이지 머리말에 <code>custom_css: true</code> 를 설정한 경우,
    <code>page.custom_css</code> 로 해당 값을 사용할 수 있습니다.

  </p>
  <p>

    If you specify front matter in a layout, access that via <code>layout</code>.
    For example, if you specify <code>class: full_page</code>
    in a layout’s front matter, that value will be available as
    <code>layout.class</code> in the layout and its parents.

  </p>
</div>

## Paginator

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
      <td><p><code>paginator.per_page</code></p></td>
<!--
      <td><p>Number of Posts per page.</p></td>
-->
      <td><p>페이지 당 포스트 수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.posts</code></p></td>
<!--
      <td><p>Posts available for that page.</p></td>
-->
      <td><p>해당 페이지의 포스트들.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.total_posts</code></p></td>
<!--
      <td><p>Total number of Posts.</p></td>
-->
      <td><p>전체 포스트 개수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.total_pages</code></p></td>
<!--
      <td><p>Total number of pages.</p></td>
-->
      <td><p>전체 페이지 개수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.page</code></p></td>
<!--
      <td><p>The number of the current page.</p></td>
-->
      <td><p>현재 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.previous_page</code></p></td>
<!--
      <td><p>The number of the previous page.</p></td>
-->
      <td><p>이전 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.previous_page_path</code></p></td>
<!--
      <td><p>The path to the previous page.</p></td>
-->
      <td><p>이전 페이지 경로.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.next_page</code></p></td>
<!--
      <td><p>The number of the next page.</p></td>
-->
      <td><p>다음 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.next_page_path</code></p></td>
<!--
      <td><p>The path to the next page.</p></td>
-->
      <td><p>다음 페이지 경로.</p></td>
    </tr>
  </tbody>
</table>
</div>

<div class="note info">
<!--
  <h5>Paginator variable availability</h5>
  <p>

    These are only available in index files, however they can be located in a
    subdirectory, such as <code>/blog/index.html</code>.

  </p>
-->
  <h5>Paginator 변수 사용 위치</h5>
  <p>

    이 변수들은 오직 인덱스 파일에서만 사용할 수 있지만,
    <code>/blog/index.html</code> 같은 하위 디렉토리 인덱스 파일도 해당됩니다.

  </p>
</div>
