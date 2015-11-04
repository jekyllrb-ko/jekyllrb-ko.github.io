---
layout: docs
title: 환경설정
permalink: /docs/configuration/
---

Jekyll 을 사용하면 당신이 상상할 수 있는 어떤 형태의 사이트든지 만들 수
있습니다. 이 모든 것은 Jekyll 의 강력하고 유연한 환경설정 옵션 덕분이죠.
이 옵션들을 정의하는 방법은 두 가지로, 사이트 루트 디렉토리의 `_config.yml`
파일에 정의하는 방법과 터미널에서 `jekyll` 을 실행할 때 플래그로 지정하는 방법이
있습니다.

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
        <p class="description">Jekyll 이 읽어들일 파일들의 경로를 변경한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">source: DIR</code></p>
        <p><code class="flag">-s, --source DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Site Destination</strong></p>
        <p class="description">Jekyll 이 생성할 파일들의 경로를 변경한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">destination: DIR</code></p>
        <p><code class="flag">-d, --destination DIR</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Safe</strong></p>
        <p class="description"><a href="../plugins/">사용자 플러그인</a>을 비활성화하고 심볼릭 링크를 무시한다.</p>
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
          특정 디렉토리나 파일을 변환되지 않도록 제외시킨다. Site Source 를
          기준으로 한 상대경로로 정의하며, Site Source 디렉토리 바깥의 다른
          경로는 지정할 수 없다.
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
          특정 디렉토리나 파일을 변환 작업에 강제로 포함시킨다. 대표적인 예로는
          <code>.htaccess</code> 가 있는데, 점으로 시작하는 파일은 제외하는 것이
          디폴트 방식이기 때문이다.
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
          사이트 생성 전 Site Destination 을 초기화 때, 그대로 보관할 파일을
          지정한다. Jekyll 이 아닌 다른 빌드 시스템에서 생성하는 파일이나
          데이터에 유용하게 쓰이는 옵션이다.
          <code>destination</code> 기준으로 하여 상대경로로 입력한다.
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
            사이트 생성에 사용할 타임존을 지정한다. 이 옵션은 루비가 날짜와
            시간을 생성/수정할 때 사용하는 환경변수인 <code>TZ</code> 를
            설정한다. <a href="http://en.wikipedia.org/wiki/Tz_database">IANA Time Zone Database</a>
            의 모든 항목을 사용할 수 있다 (예, <code>America/New_York</code>).
            사용할 수 있는 모든 설정값들의 목록은 <a href="http://en.wikipedia.org/wiki/List_of_tz_database_time_zones">
            여기</a>에서 찾을 수 있다. 기본값은 자신의 OS 에 설정된 로컬
            타임존이다.
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
            파일의 인코딩을 지정한다. Ruby 1.9 또는 이후 버전에서만 사용
            가능하다).
            디폴트값은 2.0.0 버전부터 <code>utf-8</code> 이고, 2.0.0 이전
            버전에서는 Ruby 디폴트값인 <code>ASCII-8BIT</code> 를 사용하는
            <code>nil</code> 이었다.
            사용할 수 있는 인코딩 목록을 확인하는 명령어는
            <code>ruby -e 'puts Encoding::list.join("\n")'</code> 이다.
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
            변수들의 디폴트 값을 설정한다.
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
  <h5>사이트 생성 시 Site Destination 폴더가 정리됩니다</h5>
  <p>
    사이트를 생성할 때, <code>&lt;destination&gt;</code> 안의 파일들을 자동으로
    지웁니다 (디폴트). 사이트에서 생성하지 않는 파일들은 모두 사라질 것입니다.
    <code>&lt;keep_files&gt;</code> 환경설정 옵션을 사용하여 유지할 파일들을
    선택할 수 있습니다.
  </p>
  <p>
    중요한 디렉토리는 절대 <code>&lt;destination&gt;</code> 으로 지정하면 안됩니다;
    웹 서버로 옮길 파일을 임시로 보관할 경로를 입력하세요.
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
        <p class="description">파일이 수정되었을 때 사이트를 자동으로 다시 생성한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-w, --[no-]watch</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Configuration</strong></p>
        <p class="description"><code>_config.yml</code> 대신 사용할 환경설정 파일을 직접 선택한다. 여러 파일에 동일한 옵션이 설정되어 있으면, 마지막 설정파일의 내용을 사용한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--config FILE1[,FILE2,...]</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Drafts</strong></p>
        <p class="description">초안 기능을 사용한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--drafts</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Environment</strong></p>
        <p class="description">빌드 시 임의의 환경변수 값을 사용한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">JEKYLL_ENV=production</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Future</strong></p>
        <p class="description">포스트의 게시 시간을 현재 시간 이후로 설정할 수 있다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">future: BOOL</code></p>
        <p><code class="flag">--future</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>LSI</strong></p>
        <p class="description">관련된 포스트들에 대한 인덱스를 생성한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">lsi: BOOL</code></p>
        <p><code class="flag">--lsi</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Limit Posts</strong></p>
        <p class="description">포스트의 수를 제한한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">limit_posts: NUM</code></p>
        <p><code class="flag">--limit_posts NUM</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Force polling</strong></p>
        <p class="description">감시 기능을 강제로 활성화한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">--force_polling</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Verbose output</strong></p>
        <p class="description">결과를 자세하게 출력한다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-V, --verbose</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Silence Output</strong></p>
        <p class="description">사이트 빌드 시 발생하는 일반 메시지를 출력하지
        않는다.</p>
      </td>
      <td class="align-center">
        <p><code class="flag">-q, --quiet</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>증분 빌드</strong></p>
        <p class="description">
            실험 기능인 증분 빌드를 활성화한다. 증분 빌드란 변경된 페이지나
            포스트만을 다시 빌드하는 기능으로서, 규모가 큰 사이트에서 눈에 띄는
            성능 향상을 가져올 수 있다. 하지만 특정한 상황에서는 사이트 생성에
            문제가 생길 수도 있다.
        </p>
      </td>
      <td class="align-center">
        <p><code class="option">incremental: BOOL</code></p>
        <p><code class="flag">-I, --incremental</code></p>
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
        <p class="description">Listen 포트 번호를 설정한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">port: PORT</code></p>
        <p><code class="flag">--port PORT</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Local Server Hostname</strong></p>
        <p class="description">Listen 호스트명을 설정한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">host: HOSTNAME</code></p>
        <p><code class="flag">--host HOSTNAME</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Base URL</strong></p>
        <p class="description">주어진 URL 로 웹사이트를 작동시킨다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">baseurl: URL</code></p>
        <p><code class="flag">--baseurl URL</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Detach</strong></p>
        <p class="description">터미널에서 서버를 분리한다.</p>
      </td>
      <td class="align-center">
        <p><code class="option">detach: BOOL</code></p>
        <p><code class="flag">-B, --detach</code></p>
      </td>
    </tr>
    <tr class="setting">
      <td>
        <p class="name"><strong>Skips the initial site build.</strong></p>
        <p class="description">사이트 빌드를 건너뛰고 서버를 실행한다.</p>
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

## 빌드 시점에 Jekyll 환경변수 설정하기

`build` (혹은 `serve`) 전달인자로, Jekyll 환경변수와 그 값을 설정할 수 있습니다.  이 환경변수는 빌드 시에 사이트의 모든 조건문에서 사용됩니다.

예를 들어, 당신의 코드에 이런 조건문이 있다고 가정합시다:

{% highlight liquid %}
{% raw %}
{% if jekyll.environment == "production" %}
   {% include disqus.html %}
{% endif %}
{% endraw %}
{% endhighlight %}

Jekyll 사이트를 빌드할 때, 다음과 같이 빌드 명령에 환경변수 `production` 을 정의하지 않으면 `if` 절 안에 들어있는 코드는 실행되지 않습니다:

{% highlight sh %}
JEKYLL_ENV=production jekyll build 
{% endhighlight %}

환경변수 값을 설정함으로써 특정 환경에서만 사용되는 컨텐츠를 만들 수 있습니다.

`JEKYLL_ENV` 의 디폴트 값은 `development` 입니다. 따라서 `build` 의 전달인자에 `JEKYLL_ENV` 를 생략하면, `JEKYLL_ENV=development` 가 디폴트 값으로 사용됩니다. 빌드 시 `{% raw %}{% if jekyll.environment == "development" %}{% endraw %}` 태그 안의 모든 컨텐츠가 출력될 것입니다.

당신이 원하는 어떤 것이든 환경변수 값으로 사용할 수 있습니다 (꼭 `development` 나 `production` 이지 않아도 됩니다). Disqus 댓글란이나 Google Analytics 처럼 개발환경에서는 표시하고 싶지 않은 요소들이 있을 수 있습니다. 반대로, "GitHub 에서 수정" 버튼은 개발환경에서 노출시키고 운영환경에는 포함시키지 않을 수도 있습니다.

환경설정 파일의 값을 수정하지 않고도, 빌드 명령에 이 옵션을 사용함으로써 한 환경에서 다른 환경으로 이동할 수 있습니다.

## 머리말 기본값

페이지와 포스트에서 환경설정 값을 조정하는 방법 중 하나는 [YAML 머리말](../frontmatter/)을 사용하는 것입니다. 기본 레이아웃 설정이나 제목 수정, 또는 더 자세한 날짜/시간 지정 등을 페이지나 포스트의 머리말에 입력할 수 있습니다.

종종, 같은 내용의 환경설정들을 계속해서 반복 입력하고 있는 자신을 발견할 지도 모릅니다. 각각의 파일에 동일한 레이아웃을 설정하거나 여러 개의 포스트를 동일한 카테고리(들)에 추가하는 것 말이죠. 심지어는 작성자 이름처럼 블로그의 거의 모든 포스트에 동일하게 사용되는 값을 사용자 변수로 일일히 추가하게 될 수도 있습니다.

Jekyll 은 사이트 환경설정에 변수들의 기본값을 지정하는 방법을 제공하기 때문에, 새 포스트나 페이지를 추가할 때마다 이러한 환경설정들을 반복하지 않아도 됩니다.  그러기 위해서는, 프로젝트의 루트 디렉토리에 있는 `_config.yml` 파일에 `defaults` 라는 키를 사용하여 사이트에 전체에 사용되는 기본값을 정의할 수 있습니다.

`defaults` 키에 여러 쌍의 범위/값(scope/values)을 배열로 입력할 수 있어, 특정 경로의 파일이나 파일 종류에 사용되어야 하는 디폴트 값을 정의할 수 있습니다.

사이트의 모든 포스트와 페이지에 기본 레이아웃을 추가하는 경우를 생각해 봅시다. `_config.yml` 파일에 아래 내용을 추가하면 됩니다:

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # 이 빈 문자열은 프로젝트 내의 모든 파일을 의미한다
    values:
      layout: "default"
{% endhighlight %}

여기서 우리는 `values` 의 범위를 특정 경로에 존재하는 모든 파일로 제한하고 있습니다. 하지만 경로에 빈 문자열을 설정했기 때문에, 프로젝트 내의 **모든 파일** 에 적용될 것입니다. 프로젝트 내의 모든 파일에 한 레이아웃을 적용하길 원치 않을 수도 있습니다 - 예를 들자면, css 파일같이 말이죠 - 이런 경우엔 `scope` 키에 `type` 값을 지정할 수 있습니다.

{% highlight yaml %}
defaults:
  -
    scope:
      path: "" # 이 빈 문자열은 프로젝트 내의 모든 파일을 의미한다
      type: "posts" # 과거 Jekyll 2.2 의 `post`.
    values:
      layout: "default"
{% endhighlight %}

이제, `type` 이 `posts` 인 파일에만 레이아웃이 설정될 것입니다.
`type` 의 값으로는 `pages`, `posts`, `drafts` 또는 사이트 내의 콜렉션 이름을 사용할 수 있습니다. `scope/values` 쌍을 생성할 때, `type` 은 선택사항이지만 `path` 는 반드시 정의해야 합니다.

앞서 언급했던 것처럼, `defaults` 에 여러 개의 범위/값 쌍을 설정할 수 있습니다.

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
      type: "pages" # 과거 Jekyll 2.2 의 `page`.
    values:
      layout: "project" # 앞의 디폴트 레이아웃 설정을 덮어쓴다
      author: "Mr. Hyde"
{% endhighlight %}

이 디폴트 값들로 인하여, 모든 포스트는 `my-site` 레이아웃을 사용하게 됩니다. `projects/` 폴더 안에 있는 모든 HTML 파일들은 `project` 레이아웃을 사용하게 됩니다. 또한 이 파일들은 `project` 라는 카테고리에 속하게 될 뿐만 아니라, `Mr.  Hyde` 라는 값을 가진 [Liquid 변수](../variables/) `page.author` 도 갖게 됩니다.

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

이 예제에서는 `my_collection` 이라는 이름의 [콜렉션](../collections/) 안에 `layout` 이 `default` 로 설정됩니다.

### 우선순위

Jekyll 은 `_config.yml` 파일의 `defaults` 섹션에 설정된 환경설정 값들을 모두 적용합니다. 하지만, 범위에 더 자세한 경로를 사용하면 선택적으로 다른 범위/값을 덮어쓸 수 있습니다.

앞선 예제에서 이미 살펴본 것과 같습니다. 먼저, 우리는 기본 레이아웃을 `my-site` 로 설정했습니다. 그 다음, 더 자세한 경로를 사용해서, `projects/` 경로에 있는 파일들에 대해서만 레이아웃을 `project` 로 설정했습니다. 페이지나 포스트의 머리말에 사용하는 어떤 설정에든지 이 방법을 사용할 수 있습니다.

마지막으로, `_config.yml` 파일에 `defaults` 섹션을 추가해서 사이트 환경설정 디폴트 값을 정의했어도, 페이지나 포스트에서 값을 덮어쓸 수 있습니다. 페이지나 포스트의 머리말에서 다시 해당 환경설정 값을 정의하면 됩니다. 예를 들면 다음과 같습니다:

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
여기부터는 포스트 내용이 들어갑니다...
{% endhighlight %}

이제 사이트를 구축하면, `projects/foo_project.md` 파일의 `layout` 은 `project`
가 아닌 `foobar` 로, `author` 는 `Mr. Hyde` 가 아닌 `John Smith` 로 설정됩니다.


## 환경설정 디폴트 값

다음은 Jekyll 의 환경설정 옵션들에 대한 디폴트 값 목록입니다. 명령행이나
환경설정 파일에 명시적으로 지정하여 환경설정 옵션의 값을 변경할 수 있습니다.


<div class="note warning">
  <h5>Kramdown 옵션 중 지원하지 않는 두 가지 옵션이 있습니다</h5>
  <p>
    Kramdown HTML 변환기에 <code>remove_block_html_tags</code> 와
    <code>remove_span_html_tags</code> 가 포함되어 있지 않기 때문에, 현재 Jekyll
    에서도 지원하지 않습니다.
  </p>
</div>

{% highlight yaml %}
# 파일 종류별 위치
source:       .
destination:  ./_site
plugins_dir:  ./_plugins
layouts_dir:  ./_layouts
data_dir:     ./_data
includes_dir: ./_includes
collections:  null

# 읽기 처리방법
safe:         false
include:      [".htaccess"]
exclude:      []
keep_files:   [".git", ".svn"]
encoding:     "utf-8"
markdown_ext: "markdown,mkdown,mkdn,mkd,md"

# 컨텐츠 필터링
show_drafts: null
limit_posts: 0
future:      false
unpublished: false

# 플러그인
whitelist: []
gems:      []

# 변환
markdown:    kramdown
highlighter: rouge
lsi:         false
excerpt_separator: "\n\n"
incremental: false

# 서버 작동
detach:  false
port:    4000
host:    127.0.0.1
baseurl: "" # does not include hostname

# 출력 방식
permalink:     date
paginate_path: /page:num
timezone:      null

quiet:    false
defaults: []

# 마크다운 처리기
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
{% endhighlight %}

## 마크다운 옵션

Jekyll 은 다양한 마크다운 렌더러를 지원하며, 몇몇은 추가 옵션을 가지고 있기도
합니다.

### Redcarpet

Redcarpet 을 사용하려면 `extensions` 라는 하위-설정에 문자열을 배열 형식으로
지정하면 됩니다. 배열 안에 들어갈 문자열은 `Redcarpet::Markdown` 클래스의
확장기능 이름이며, 배열 안에 지정된 문자열에 해당하는 확장기능의 값이 `true` 로
설정됩니다.

Jekyll 이 처리할 수 있는 두 가지의 특별한 Redcarpet 확장기능이 있습니다:

- `no_fenced_code_blocks` --- Jekyll 에서 `fenced_code_blocks` 확장기능 (틸데나
백틱문자 3 개로 코드 블록을 구분하는 기능) 의 디폴트 값은 `true` 인데,
아마도 오래전부터 GitHub 에서 이 방식으로 채택하고 있어서 점점 필수적으로
받아들여지고 있습니다. Redcarpet 자체적으로는 `fenced_code_blocks` 확장기능이
비활성화 되어 있습니다; 반대로 작동하는 이 버전을 대신 사용해서 코드 테두리를
비활성화 해도 됩니다.

또한, 첫 번째 구분자 바로 뒤에 언어를 명시하면 구문강조가 가능하다는 것도
알아두세요:

        ```ruby
        # ...ruby code
        ```

코드 블록 테두리와 구문 강조기를 모두 활성화하면, 완전한 코드 구문 강조가
가능합니다; 구문 강조기능을 전혀 사용하지 않으면, `<code>` 요소에
`class="LANGUAGE"` 속성이 추가되어 자바스크립트 기반으로 작성된, 다양한 코드
구문 강조 라이브러리들의 작동에 도움이 됩니다.

- `smart` --- 이 의사(pseudo) 확장기능은 SmartyPants 를 활성화하여, 따옴표를
  인쇄용 따옴표로 변환하고 긴 줄표 (`---`) 와 작은 줄표 (`--`) 를 사용할 수 있게 해줍니다.

이 외의 다른 확장기능들은 Redcarpet 의 확장기능과 동일한 이름을 갖고 있으며,
렌더러 옵션들 중 `smart` 를 제외한 다른 모든 옵션들은 사용할 수 없습니다.
[사용할 수 있는 확장기능 목록은 Redcarpet 의 README 파일을
확인하세요][redcarpet_extensions].  올바른 버전의 Redcarpet README 파일을
읽고있는 것인지 반드시 확인하세요: Jekyll 은 현재 v3.2.x 를 사용하고 있습니다.
자주 사용하는 확장기능은 다음과 같습니다:

- `tables`
- `no_intra_emphasis`
- `autolink`

[redcarpet_extensions]: https://github.com/vmg/redcarpet/blob/v3.2.2/README.markdown#and-its-like-really-simple-to-use

### Kramdown

앞서 언급한 디폴트 마크다운 뿐만 아니라, Github Flavored Markdown 도 인식하도록
설정하려면 `input` 옵션의 값을 "GFM" 으로 지정하면 됩니다.

다음은 `_config.yml` 파일에 추가해야 할 설정 예시입니다:

    kramdown:
      input: GFM

### 사용자 마크다운 처리기

새로운 마크다운 처리기 제작방법에 관심이 있다면, 운이 좋군요! `Jekyll::Converters::Markdown` 네임스페이스에 새 클래스를 생성하세요:

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

클래스 생성을 마친 후 `_plugins` 폴더에 플러그인으로 설정하거나 gem 으로
설정하는 작업을 올바르게 끝마쳤다면, `_config.yml` 에 다음과 같이 입력합니다:

{% highlight yaml %}
markdown: MyCustomProcessor
{% endhighlight %}
