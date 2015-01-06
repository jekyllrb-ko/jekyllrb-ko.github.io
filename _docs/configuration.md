---
layout: docs
title: 환경설정
prev_section: structure
next_section: frontmatter
permalink: /docs/configuration/
---

당신이 상상하는 어떤 형태의 사이트든지 Jekyll 로 만들 수 있습니다. 이 모든 것은
강력하고 유연한 환경설정 옵션 덕분이죠. 옵션은 사이트 루트 디렉토리의
`_config.yml` 파일에 지정하거나, 터미널에서 실행파일 `jekyll` 에 플래그로 지정할
수 있습니다.


## 환경설정

### 전역 환경설정

다음 표는 Jekyll 에서 사용할 수 있는 환경설정과 그에 해당하는 <code
class="option">옵션</code> (설정 파일에 사용함) 과 <code
class="flag">플래그</code> (명령어에 사용함) 들의 목록입니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>설정</th>
      <th>
        <span class="option">옵션</span>과 <span class="flag">플래그</span>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Site Source</strong></p>
        <p class="description">Jekyll 이 파일을 읽는 디렉토리를 변경합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">source: DIR</code></p>
        <p><code class="flag">-s, --source DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Site Destination</strong></p>
        <p class="description">Jekyll 이 파일을 쓰는 디렉토리를 변경합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">destination: DIR</code></p>
        <p><code class="flag">-d, --destination DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Safe</strong></p>
        <p class="description"><a href="../plugins/">사용자 플러그인</a>을 비활성화하고 심볼릭 링크를 무시합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">safe: BOOL</code></p>
        <p><code class="flag">--safe</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Exclude</strong></p>
        <p class="description">
          특정 디렉토리나 파일을 변환되지 않도록 제외시킵니다. 기준 경로는 Site
          Source 디렉토리이며, 이 디렉토리 바깥의 다른 경로는 지정할 수
          없습니다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">exclude: [DIR, FILE, ...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Include</strong></p>
        <p class="description">
          특정 디렉토리나 파일을 변환 작업에 강제로 포함시킵니다. 대표적인 예로
          <code>.htaccess</code> 를 포함시키는 것이 있는데, 점으로 시작하는
          파일은 기본적으로 제외되기 때문입니다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">include: [DIR, FILE, ...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Keep files</strong></p>
        <p class="description">
          사이트 생성 전 Site Destination 을 정리할 때, 보존할 파일을
          지정합니다. Jekyll 이 아닌 다른 빌드 환경으로부터 생성되는
          파일들에 대해 유용하게 사용할 수 있습니다.
          <code>destination</code> 을 기준으로 하는 상대경로를 입력합니다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">keep_files: [DIR, FILE, ...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Time Zone</strong></p>
        <p class="description">
            사이트 생성에 사용할 타임존을 지정합니다. 환경변수인 <code>TZ</code>
            가 설정되며, 루비가 날짜와 시간을 생성/수정할 때 사용합니다.
            <a href="http://en.wikipedia.org/wiki/Tz_database">IANA Time Zone
            Database</a> 의 모든 항목을 사용할 수 있습니다 (예,
            <code>America/New_York</code>). <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">여기</a>에서
            사용할 수 있는 모든 값의 목록을 찾을 수 있습니다. 기본값은 자신의 OS
            에 설정된 로컬 타임존입니다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">timezone: TIMEZONE</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Encoding</strong></p>
        <p class="description">
            파일의 인코딩을 지정합니다 (Ruby 1.9 또는 이후 버전에서만 사용
            가능).
            2.0.0 버전부터는 기본값이 <code>utf-8</code> 이고, 2.0.0 이전
            버전에서는 <code>nil</code> 이며, 이 때 사용되는 실제값은 Ruby 의
            기본값인 <code>ASCII-8BIT</code> 입니다.
            사용할 수 있는 인코딩은
            <code>ruby -e 'puts Encoding::list.join("\n")'</code> 명령으로 확인할 수 있습니다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">encoding: ENCODING</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p class='name'><strong>Defaults</strong></p>
        <p class='description'>
            <a href="../frontmatter/" title="YAML Front Matter">YAML 머리말</a>
            변수들의 기본값을 지정합니다.
        </p>
      </td>
      <td class='align-center'>
        <p><a href="#front-matter-defaults" title="details">아래 내용</a> 참조</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>사이트 생성 시 <code>&lt;destination&gt;</code> 폴더가 정리됩니다</h5>
  <p>
    사이트를 생성하면 자동적으로 <code>&lt;destination&gt;</code> 안의
    파일들이 지워집니다. 사이트에서 생성하지 않는 파일들은 모두 사라질
    것입니다. 중요한 폴더는 절대 <code>&lt;destination&gt;</code> 으로
    지정하면 안됩니다;
    대신, 파일을 웹 서버에 복사하기 전에 임시로 보관할 폴더를 지정하세요.
  </p>
</div>

### Build 명령어 옵션

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>설정</th>
      <th><span class="option">옵션</span>과 <span class="flag">플래그</span></th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Regeneration</strong></p>
        <p class="description">파일이 수정되었을 때 자동으로 사이트를 다시 생성합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-w, --watch</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Configuration</strong></p>
        <p class="description">자동적으로 사용되는 <code>_config.yml</code> 대신 설정파일을 직접 선택합니다. 여러 파일에 동일한 옵션이 설정되어 있으면, 마지막 설정파일의 내용을 사용합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--config FILE1[,FILE2,...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Drafts</strong></p>
        <p class="description">초안 기능을 사용합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--drafts</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Future</strong></p>
        <p class="description">미래 시간의 포스트를 게시합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">future: BOOL</code></p>
        <p><code class="flag">--future</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>LSI</strong></p>
        <p class="description">관련된 포스트들에 대한 인덱스를 생성합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">lsi: BOOL</code></p>
        <p><code class="flag">--lsi</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Limit Posts</strong></p>
        <p class="description">포스트의 수를 제한합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">limit_posts: NUM</code></p>
        <p><code class="flag">--limit_posts NUM</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Force polling</strong></p>
        <p class="description">감시 기능을 강제로 활성화합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--force_polling</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Verbose output</strong></p>
        <p class="description">결과를 자세하게 출력합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-V, --verbose</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Silence Output</strong></p>
        <p class="description">사이트 빌드 시 발생하는 일반 메시지를 출력하지
        않습니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-q, --quiet</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

### Serve 명령 옵션

`serve` 명령은 아래 나열된 옵션 뿐만 아니라 `build` 명령의 옵션도 사용할 수
있습니다. 먼저 `build` 작업에 해당 옵션들이 사용된 후에 `serve` 작업이
수행됩니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>설정</th>
      <th><span class="option">옵션</span>과 <span class="flag">플래그</span></th>
    </tr>
  </thead>
  <tbody>
    <tr class="setting">
      <td>
        <p class="name"><strong>Local Server Port</strong></p>
        <p class="description">주어진 포트 번호를 Listen 합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">port: PORT</code></p>
        <p><code class="flag">--port PORT</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Local Server Hostname</strong></p>
        <p class="description">주어진 호스트네임으로 Listen 합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">host: HOSTNAME</code></p>
        <p><code class="flag">--host HOSTNAME</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Base URL</strong></p>
        <p class="description">주어진 URL 로 웹사이트를 작동시킵니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">baseurl: URL</code></p>
        <p><code class="flag">--baseurl URL</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Detach</strong></p>
        <p class="description">터미널에서 서버를 분리합니다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">detach: BOOL</code></p>
        <p><code class="flag">-B, --detach</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Skips the initial site build.</strong></p>
        <p class="description">서버 실행 전의 사이트 빌드를 건너 뜁니다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--skip-initial-build</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>환경설정 파일에 탭 문자를 사용하지 마세요</h5>
  <p>
    파싱 에러가 발생하거나 기본 설정값이 사용될 것입니다. 대신 띄어쓰기를
    사용하세요.
  </p>
</div>

## 머리말 기본값

페이지와 포스트에서 환경설정 값을 지정하는 방법 중 하나는 [YAML 머리말](../frontmatter/)을 사용하는 것입니다. 기본 레이아웃이나 제목 변경, 또는 더 자세한 날짜/시간 등을 페이지나 포스트의 머리말에 입력할 수 있습니다.

각각의 파일에 동일한 레이아웃을 설정하거나 여러 포스트들에 동일한 카테고리 - 또는 카테고리들 - 추가하기 등, 여러개의 환경설정 옵션을 반복해서 입력하고 있는 자신을 종종 발견할 수도 있습니다. 작성자 이름처럼 블로그의 거의 모든 포스트에 동일하게 사용되곤 하는 값들은 사용자 변수로 추가할 수 있습니다.

Jekyll 은 이러한 기본값들을 사이트 환경설정에 지정할 수 있는 방법을 제공하기 때문에 새 포스트나 새 페이지를 추가할 때마다 이러한 환경설정들을 반복하지 않아도 됩니다. 그러기 위해서는, 프로젝트의 루트 디렉토리에 있는 `_config.yml` 파일에 `defaults` 라는 키를 사용하여 사이트 전반적인 기본값을 정의할 수 있습니다.

`defaults` 키에 여러 쌍의 범위/값을 배열로 입력할 수 있어, 특정 경로의 파일이나 파일 종류에 사용되어야 하는 기본값을 정의할 수 있습니다.

사이트의 모든 포스트와 페이지에 기본 레이아웃을 추가하는 경우를 생각해 봅시다. `_config.yml` 파일에 아래 내용을 추가하면 됩니다:

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # 여기에서 빈 문자열은 프로젝트 내의 모든 파일을 의미합니다
    values:
      layout: "default"
{% endhighlight %}

여기서 우리는 `values` 의 범위를 범위 경로 안에 존재하는 모든 파일로 제한하고 있습니다. 하지만 여기선 경로가 비어 있으므로, 프로젝트 내의 **모든 파일** 에 적용될 것입니다. 프로젝트 내의 모든 파일에 한 레이아웃을 적용하지 않는 경우도 있을 것입니다 - 예를 들자면, css 파일같이 말이죠 - 그렇다면 `scope` 키 아래에 `type` 값을 지정할 수 있습니다.

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # 여기에서 빈 문자열은 프로젝트 내의 모든 파일을 의미합니다
      type: "posts" # Jekyll 2.2 이전에는 `post` 였음.
    values:
      layout: "default"
{% endhighlight %}

이제 `posts` 타입인 파일에만 레이아웃이 설정될 것입니다.
타입으로는 사이트의 어느 콜렉션이나 `pages`, `posts`, `drafts` 를 사용할 수 있습니다. `scope/values` 쌍을 생성할 때 `type` 은 선택사항이지만 `path` 는 반드시 정의해야 합니다.

앞서 언급했던 것처럼, `defaults` 에 여러 개의 scope/values 쌍을 설정할 수 있습니다.

{% highlight yaml %}
defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project" # 앞의 default 레이아웃을 덮어씁니다
      author: "Mr. Hyde"
{% endhighlight %}

이 기본값들로 인하여, 모든 포스트는 `my-site` 레이아웃을 사용하게 됩니다. `projects/` 폴더 안의 모든 HTML 파일들은 `project` 레이아웃을 사용하게 됩니다. 또한 이 파일들은 `project` 라는 카테고리 뿐만 아니라 `Mr. Hyde` 라고 설정된 `page.author` [Liquid 변수](../variables/)도 갖게 됩니다.

{% highlight yaml %}
collections:
  - my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # a collection in your site, in plural form
    values:
      layout: "default"
{% endhighlight %}

이 예제에서는 `my_collection` 이라는 이름의 [콜렉션](../collections) 안에 `layout` 이 `default` 로 설정됩니다.

### 우선순위

Jekyll 은 `_config.yml` 파일의 `defaults` 섹션에 설정된 환경설정 값들을 모두 적용합니다. 하지만, 범위에 더 자세한 경로를 사용해서 다른 범위/값을 덮어쓰도록 선택할 수 있습니다.

이미 바로 위의 예제에서 본 것과 같습니다. 먼저, 우리는 기본 레이아웃을 `my-site` 로 설정했습니다. 다음, 더 자세한 경로를 사용해서, `projects/` 안 파일들의 기본 레이아웃은 `project` 로 설정했습니다. 페이지나 포스트의 머리말에 설정하는 어떠한 값에도 이 방법을 사용할 수 있습니다.

마지막으로, `_config.yml` 파일에 `defaults` 섹션을 추가해서 설정한 사이트 환경설정 기본값이 있다면, 포스트나 페이지에서 덮어쓸 수 있습니다. 포스트나 페이지의 머리말에서 해당 환경설정을 다시 하기만 하면 됩니다. 예를 들면:

{% highlight yaml %}
# _config.yml 에는
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
{% endhighlight %}

{% highlight yaml %}
# projects/foo_project.md 에는
---
author: "John Smith"
layout: "foobar"
---
포스트 내용이 들어가는 자리...
{% endhighlight %}

이제 사이트를 구축하면 `projects/foo_project.md` 는 `layout` 으로 `project` 대신 `foobar` 를, `author` 로는 `Mr. Hyde` 대신 `John Smith` 를 갖게 됩니다.

## 환경설정 기본값

다음은 Jekyll 이 기본값으로 사용하는 환경설정 옵션들입니다. 환경설정 파일이나
명령어에 다음 옵션들이 명시적으로 지정되어 있지 않으면, 이 설정값들이
사용됩니다.

<div class="note warning">
  <h5>Kramdown 옵션 중 두 개는 지원하지 않습니다</h5>
  <p>
    현재 <code>remove_block_html_tags</code> 와
    <code>remove_span_html_tags</code> 는 Kramdown HTML 변환기에 포함되어 있지
    않기 때문에, Jekyll 에서도 지원하지 않습니다.
  </p>
</div>

{% highlight yaml %}
# 파일 종류별 위치
source:      .
destination: ./_site
plugins:     ./_plugins
layouts:     ./_layouts
data_source: ./_data
collections: null

# 읽기 처리방법
safe:         false
include:      [".htaccess"]
exclude:      []
keep_files:   [".git", ".svn"]
encoding:     "utf-8"
markdown_ext: "markdown,mkdown,mkdn,mkd,md"
textile_ext:  "textile"

# 컨텐츠 필터링
show_drafts: null
limit_posts: 0
future:      true
unpublished: false

# 플러그인
whitelist: []
gems:      []

# 변환
markdown:    kramdown
highlighter: pygments
lsi:         false
excerpt_separator: "\n\n"

# 서버 작동
detach:  false
port:    4000
host:    127.0.0.1
baseurl: "" # does not include hostname

# 구버전 호환성
relative_permalinks: false

# 출력 방식
permalink:     date
paginate_path: /page:num
timezone:      null

quiet:    false
defaults: []

# 마크다운 처리기
maruku:
  use_tex:    false
  use_divs:   false
  png_engine: blahtex
  png_dir:    images/latex
  png_url:    /images/latex
  fenced_code_blocks: true

rdiscount:
  extensions: []

redcarpet:
  extensions: []

kramdown:
  auto_ids:       true
  footnote_nr:    1
  entity_output:  as_char
  toc_levels:     1..6
  smart_quotes:   lsquo,rsquo,ldquo,rdquo
  enable_coderay: false

  coderay:
    coderay_wrap:              div
    coderay_line_numbers:      inline
    coderay_line_number_start: 1
    coderay_tab_width:         4
    coderay_bold_every:        10
    coderay_css:               style

redcloth:
  hard_breaks: true
{% endhighlight %}

## 마크다운 옵션

Jekyll 은 다양한 마크다운 엔진을 지원하며, 부가기능을 가지고 있는 것도 있습니다.

### Redcarpet

Redcarpet 을 사용하려면 `extensions` 설정에 문자열을 배열 형식으로 지정하면 됩니다. 배열 안에 들어갈 값은 `Redcarpet::Markdown` 클래스의 확장기능 이름이며, 배열 안에 지정된 각각의 확장기능이 `true` 로 설정됩니다.

Jekyll 이 처리할 수 있는 두 가지의 특별한 Redcarpet 확장기능이 있습니다:

- `no_fenced_code_blocks` --- Jekyll 의  `fenced_code_blocks` 확장기능 (틸데나 백틱문자 3 개로 코드 블록을 구분하는 기능) 기본값은 `true` 인데, GitHub 에 이 기능이 오래전부터 채택되어 있어서 점점 필수요소가 되어가고 있습니다. Redcarpet 자체적으로는 `fenced_code_blocks` 확장기능이 비활성화 되어 있습니다; 반대로 되어 있는 이 버전을 대신 사용해서 코드 테두리를 비활성화 해도 됩니다.

또한, 첫 번째 구분자 바로 뒤에 언어를 명시하여 구문강조를 사용할 수도 있습니다:

        ```ruby
        # ...ruby code
        ```

코드 블록 테두리와 구문 강조기를 모두 활성화하면, 정적인 구문 강조가 가능합니다; 구문 강조기를 전혀 쓰지 않으면, 여러 자바스크립트 기반 코드 구문 강조 라이브러리 작동에 도움이 되는 `class="LANGUAGE"` 속성이 `<code>` 요소에 추가됩니다.

- `smart` --- 이 의사(pseudo) 확장기능은 SmartyPants 를 활성화하여, 따옴표를 인쇄용 따옴표로 변환하고 긴 줄표 (`---`) 와 작은 줄표 (`--`) 를 사용할 수 있게 해줍니다.

이 외의 다른 확장기능들은 Redcarpet 의 확장기능과 이름이 동일하며, `smart` 를 제외한 다른 모든 렌더링 옵션들은 사용할 수 없습니다. [확장기능 목록은 Redcarpet 의 README 파일을 확인하세요][redcarpet_extensions]. 이 README 파일은 현재 버전의 Redcarpet 에 대한 내용입니다: Jekyll 은 현재 v2.2.x 를 사용하고 있으며, `footnotes` 와 `highlight` 같은 확장기능들은 버전 3.0.0 이후부터 추가 되었습니다. 가장 많이 사용되는 확장기능들은 다음과 같습니다:

- `tables`
- `no_intra_emphasis`
- `autolink`

[redcarpet_extensions]: https://github.com/vmg/redcarpet/blob/v2.2.2/README.markdown#and-its-like-really-simple-to-use

### Kramdown

앞서 언급된 기본값 기능뿐만 아니라, `input` 옵션의 값을 "GFM" 으로 지정해서 Github Flavored Markdown 인식 기능을 켤 수 있습니다.

예를 들면, `_config.yml` 파일에 이렇게 입력합니다:

    kramdown:
      input: GFM

### 사용자 마크다운 처리기

만약 자신만의 마크다운 처리기를 작성하는데에 관심이 있다면, 당신은 아주 운이 좋습니다! `Jekyll::Converters::Markdown` 네임스페이스에 새 클래스를 생성하세요:

{% highlight ruby %}
class Jekyll::Converters::Markdown::MyCustomProcessor
  def initialize(config)
    require 'funky_markdown'
    @config = config
  rescue LoadError
    STDERR.puts 'You are missing a library required for Markdown. Please run:'
    STDERR.puts '  $ [sudo] gem install funky_markdown'
    raise FatalException.new("Missing dependency: funky_markdown")
  end

  def convert(content)
    ::FunkyMarkdown.new(content).convert
  end
end
{% endhighlight %}

자신의 클래스를 생성한 후, `_plugins` 폴더에 플러그인으로 설정하거나 gem 으로 올바르게 설정했다면, `_config.yml` 에 다음과 같이 지정합니다:

{% highlight yaml %}
markdown: MyCustomProcessor
{% endhighlight %}
