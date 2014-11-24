---
layout: docs
title: 콜렉션
prev_section: variables
next_section: datafiles
permalink: /docs/collections/
---

<div class="note warning">
  <h5>콜렉션 기능은 안정적이지 않고 변경될 수도 있습니다</h5>
  <p>
    실험적인 기능으로서, 안정화가 될 때까지 API 가 자주 변경될 수 있습니다.
  </p>
</div>

페이지나 포스트만 있는 것은 아닙니다. 예를 들면, 프로젝트 내의 다양한 메소드라던지 팀의 멤버 목록, 아니면 컨퍼런스의 대화같은 것들을 문서화하고 싶을 수도 있습니다. 콜렉션 기능을 사용하면 기본적으로는 페이지나 포스트처럼 동작하지만, 고유한 네임스페이스와 속성을 가진 새로운 종류의 문서를 정의할 수 있습니다.

## 콜렉션 사용하기

### 1 단계: Jekyll 에게 콜렉션을 읽도록 지시하기

`_config.yml` 파일에 아래처럼 `my_collection` 부분은 자신의 콜렉션 이름으로 바꿔서 입력하세요:

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

### 2 단계: 컨텐츠 추가하기

설정한 콜렉션 이름에 맞는 폴더 (예시, `<source>/_my_collection`) 를 생성하고 문서를 추가합니다.
YAML 머리말은 원래대로 작동하며, 만약 머리말이 없다면 문서의 모든 내용은 `content` 속성에 들어갑니다.

주의: 폴더의 이름은 반드시 `_config.yml` 파일에 정의한 콜렉션에 `_` 문자를 붙인 것이어야 합니다.

### 3 단계: 콜렉션 내 문서를 독립적인 파일로 출력하기 (선택사항)

만약 콜렉션에 포함된 각각의 문서가 독립적인 버전으로 생성되게 하고 싶다면, `_config.yml` 파일의 콜렉션 정의부분에 `output` 키를 추가하고 `true` 라는 값을 설정합니다:

{% highlight yaml %}
collections:
  my_collection:
    output: true
{% endhighlight %}

이렇게 하면 콜렉션 안의 모든 문서가 각각 파일로 생성됩니다.
예를 들어, `_my_collection/some_subdir/some_doc.md` 라는 파일이 있다면,
Liquid 와 Markdown 변환기를 거쳐서
`<dest>/my_collection/some_subdir/some_doc.html` 로 만들어질 것입니다.

[고유주소](../permalinks/)를 가진 포스트와 마찬가지로, 콜렉션 메타데이터에 `permalink` 설정을 하면 문서 URL 은 변경될 수도 있습니다:

{% highlight yaml %}
collections:
  my_collection:
    output: true
    permalink: /awesome/:path/
{% endhighlight %}

예를 들어, `_my_collection/some_subdir/some_doc.md` 라는 파일이 있다면, 생성되는 파일의 경로는 `<dest>/awesome/some_subdir/some_doc/index.html` 가 됩니다.

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
        <p>알파벳과 숫자가 아닌 문자와 공백문자는 모두 하이픈으로 교체된, 문서의 기본 파일명.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>알파벳과 숫자가 아닌 문자와 공백문자는 모두 하이픈으로 교체된, 문서의 (<a href="/docs/frontmatter/">머리말</a>에 정의된) 소문자 제목. 만약 문서의 <a href="/docs/frontmatter/">머리말</a>에 제목이 정의되어 있지 않으면, <code>name</code> 와 동일하다.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output_ext</code></p>
      </td>
      <td>
        <p>생성되는 파일의 확장자</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## Liquid 속성

### 콜렉션

모든 콜렉션은 Liquid 변수인 `site` 로 접근할 수 있습니다. 예를 들어, `_albums` 에 있는 `albums` 콜렉션에 접근하려고 한다면, `site.albums` 를 사용하면 됩니다. 모든 콜렉션은 여러 문서들에 대한 배열입니다 (예시, `site.albums` 는 `site.pages` 와 `site.posts` 거의 유사함). 이 문서들의 속성에 접근하는 방법은 아래를 참고하세요.

콜렉션은 `site.collections` 로도 접근할 수 있으며, `_config.yml` 파일에 정의한 메타데이터와 다음 정보들도 사용할 수 있다:

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
        <p><code>relative_directory</code></p>
      </td>
      <td>
        <p>
          The path to the collections's source directory, relative to the site source.
          사이트 소스 디렉토리 기준, 콜렉션의 소스 디렉토리 상대 경로
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
          콜렉션의 문서들이 독립적인 파일로 출력될 것인지 여부
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>


### 문서

파일에 지정된 YAML 머리말뿐만 아니라, 각 문서는 다음과 같은 속성을 가지고 있습니다:

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
          문서의 (변환되지 않은) 컨텐츠. 만약 YAML 머리말이 없다면, 파일
          컨텐츠와 완전히 동일하다. YAML 머리말이 사용되었다면, 머리말을 제외한 컨텐츠와
          동일하다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
          <code>content</code> 를 기준으로, 변환된 문서
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
          렌더링 된 콜렉션의 URL. 파일은 자신이 속해있는 콜렉션의 이름이 사이트
          환경설정 파일의 <code>render</code> 키에 포함되어 있을 경우에만
          생성된다.
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
