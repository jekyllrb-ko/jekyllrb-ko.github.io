---
layout: docs
title: 콜렉션
permalink: /docs/collections/
---

<div class="note warning">
  <h5>콜렉션 기능은 안정적이지 않고 변경될 수도 있습니다</h5>
  <p>
    실험 단계의 기능으로서, 안정화 되기 전까지 API 가 변경될 수도 있습니다.
  </p>
</div>

페이지나 포스트가 전부는 아닙니다. 자신의 오픈 소스 프로젝트에 포함된 다양한
메소드나 팀 멤버들의 목록, 또는 컨퍼런스 대화 내역들을 문서화하려는 경우도
생각해볼 수 있습니다. 콜렉션 기능을 사용하면 기본적으로는 페이지나 포스트처럼
동작하지만, 고유한 네임스페이스와 속성이 추가된 새로운 종류의 문서를 정의할 수
있습니다.

## 콜렉션 사용하기

### 1 단계: Jekyll 에게 콜렉션을 읽도록 지시하기

자신의 `_config.yml` 파일에 아래의 내용을 추가하고, `my_collection` 부분은
자신의 콜렉션 이름으로 바꾸세요:

{% highlight yaml %}
collections:
- my_collection
{% endhighlight %}

원한다면 콜렉션에 관련된 메타데이터를 정의할 수도 있습니다:

{% highlight yaml %}
collections:
  my_collection:
    foo: bar
{% endhighlight %}

콜렉션 속성들에 대한 기본값을 설정할 수도 있습니다:

{% highlight yaml %}
defaults:
  - scope:
      path: ""
      type: my_collection
    values:
      layout: page
{% endhighlight %}

### 2 단계: 컨텐츠 추가하기

설정한 콜렉션 이름에 맞는 폴더 (예시, `<source>/_my_collection`) 를 생성하고
문서를 추가합니다. YAML 머리말이 있다면 문서의 부가정보가 되며, 이후의 모든
내용은 문서의 `content` 속성에 들어갑니다. YAML 머리말이 없는 경우에는, 콜렉션에
파일이 생성되지 않습니다.

<div class="note info">
  <h5>디렉토리 이름이 올바른지 확인하세요</h5>
  <p>
폴더의 이름은 반드시 `_config.yml` 파일에 정의한 콜렉션 이름 앞에 <code>_</code>
문자를 붙인 것이어야 합니다.
  </p>
</div>

### 3 단계: 콜렉션 내 문서를 독립적인 파일로 렌더링하기 (선택사항)

만약 콜렉션에 포함된 각각의 문서가 독립적인 버전으로 생성되게 하고 싶다면,
`_config.yml` 파일의 콜렉션 정의부분에 `output` 키를 추가하고 그 값을 `true` 로
설정합니다:

{% highlight yaml %}
collections:
  my_collection:
    output: true
{% endhighlight %}

이렇게 하면 콜렉션 안의 모든 문서가 각각 파일로 생성됩니다.
예를 들어, `_my_collection/some_subdir/some_doc.md` 라는 파일이 있다면,
당신이 선택한 Markdown 변환기와 Liquid 를 거쳐서
`<dest>/my_collection/some_subdir/some_doc.html` 로 만들어질 것입니다.

[고유주소](../permalinks/)를 가진 포스트와 마찬가지로, 콜렉션 메타데이터에
`permalink` 를 설정해서 문서 URL 을 변경할 수 있습니다:

{% highlight yaml %}
collections:
  my_collection:
    output: true
    permalink: /awesome/:path/
{% endhighlight %}

예를 들어, `_my_collection/some_subdir/some_doc.md` 라는 파일이 있다면, 생성되는
파일의 경로는 `<dest>/awesome/some_subdir/some_doc/index.html` 가 됩니다.

<div class="note info">
  <h5>페이지 변환이 필요하다면 YAML 을 잊지 마세요</h5>
  <p>
  파일이 콜렉션에 포함되어 있다 할지라도 머리말이 없으면
  <a href="/docs/static-files">정적 파일</a>로 취급되어, 아무런 처리 과정을
  거치지 않고 출력 경로에 단순 복사됩니다.
  </p>
</div>

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
        <p>콜렉션의 제목</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>path</code></p>
      </td>
      <td>
        <p>콜렉션 디렉토리에 상대적인 문서의 경로</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>name</code></p>
      </td>
      <td>
        <p> 문서의 기본 파일명 (알파벳과 숫자가 아닌 문자와 공백문자는 모두
        하이픈으로 교체됨).</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>문서의 (<a href="/docs/frontmatter/">머리말</a>에 정의된) 소문자 제목 (알파벳과 숫자가 아닌 문자와 공백문자는 모두 하이픈으로 교체됨). 만약 문서의 <a href="/docs/frontmatter/">머리말</a>에 제목이 정의되어 있지 않으면, <code>name</code> 과 동일하다.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output_ext</code></p>
      </td>
      <td>
        <p>출력 파일의 확장자</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## Liquid 속성

### 콜렉션

모든 콜렉션은 Liquid 변수인 `site` 로 접근할 수 있습니다. 예를 들어, `_albums`
에 있는 `albums` 콜렉션에 접근하려고 한다면, `site.albums` 를 사용하면 됩니다.
모든 콜렉션은 여러 문서들에 대한 배열입니다 (예시, `site.albums` 는 `site.pages`
와 `site.posts` 거의 유사함). 이 문서들의 속성에 접근하는 방법은 아래를
참고하세요.

콜렉션은 `site.collections` 로도 접근할 수 있으며, `_config.yml` 파일에 정의한
메타데이터와 다음 정보들도 사용할 수 있습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>label</code></p>
      </td>
      <td>
        <p>
          콜렉션의 이름. 예시, <code>my_collection</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>docs</code></p>
      </td>
      <td>
        <p>
          <a href="#documents">문서</a>들의 배열.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>files</code></p>
      </td>
      <td>
        <p>
          콜렉션 내의 정적 파일 배열.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>relative_directory</code></p>
      </td>
      <td>
        <p>
          콜렉션 소스 디렉토리
          (Site Source 디렉토리를 기준으로 한 상대 경로)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>directory</code></p>
      </td>
      <td>
        <p>
          콜렉션 소스 디렉토리 전체 경로
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
          콜렉션의 문서들이 독립적인 파일로 출력될 것인지에 대한 여부

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>


### 문서

모든 문서는 파일에 지정된 YAML 머리말뿐만 아니라, 다음과 같은 속성들도 가지고
있습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>content</code></p>
      </td>
      <td>
        <p>
          문서의 (변환되지 않은) 컨텐츠.
          YAML 머리말이 없다면, Jekyll 은 콜렉션에 어떠한 파일도 생성하지 않는다.
          YAML 머리말이 사용되었다면, 머리말의 종료표시인 `---` 이후의 모든
          내용이 이 변수에 담긴다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
          <code>content</code> 를 기초하여 렌더링된 출력 문서

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>path</code></p>
      </td>
      <td>
        <p>
          문서 소스 파일의 전체 경로
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>relative_path</code></p>
      </td>
      <td>
        <p>
          사이트 소스 경로를 기준으로 한, 문서 소스 파일의 상대 경로
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>url</code></p>
      </td>
      <td>
        <p>
          렌더링 된 콜렉션의 URL.
          사이트 환경설정 파일의 <code>render</code> 키에 이름이 명시된 콜렉션의
          파일들만 Site Destination 에 생성된다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
        <p>
          해당 문서가 포함된 콜렉션의 이름
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 콜렉션 속성 사용하기

YAML 머리말에 있는 속성들은 데이터로서 사이트 내 어느 곳에서든 사용할 수
있습니다. 콜렉션을 `site.albums` 로 설정하는 위 예제를 사용할 때, 다음과 같은
구조의 머리말을 가진 개별 파일이 있을 수 있습니다 (반드시 지원하는 마크업 언어로
작성해야 하며, `.yaml` 확장자가 아니어야 합니다):


{% highlight yaml %}
title: "Josquin: Missa De beata virgine and Missa Ave maris stella"
artist: "The Tallis Scholars"
director: "Peter Phillips"
works:
  - title: "Missa De beata virgine"
    composer: "Josquin des Prez"
    tracks:
      - title: "Kyrie"
        duration: "4:25"
      - title: "Gloria"
        duration: "9:53"
      - title: "Credo"
        duration: "9:09"
      - title: "Sanctus & Benedictus"
        duration: "7:47"
      - title: "Agnus Dei I, II & III"
        duration: "6:49"
{% endhighlight %}

다음 템플릿을 사용하면 콜렉션 내의 모든 앨범을 한 페이지에 출력할 수 있습니다:

{% highlight html %}
{% raw %}
{% for album in site.albums %}
  <h2>{{ album.title }}</h2>
  <p>Performed by {{ album.artist }}{% if album.director %}, directed by {{ album.director }}{% endif %}</p>
  {% for work in album.works %}
    <h3>{{ work.title }}</h3>
    <p>Composed by {{ work.composer }}</p>
    <ul>
    {% for track in work.tracks %}
      <li>{{ track.title }} ({{ track.duration }})</li>
    {% endfor %}
    </ul>
  {% endfor %}
{% endfor %}
{% endraw %}
{% endhighlight %}
