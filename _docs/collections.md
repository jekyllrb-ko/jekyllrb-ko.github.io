---
#title: Collections
title: 콜렉션
permalink: /docs/collections/
---

<!--
Not everything is a post or a page. Maybe you want to document the various
methods in your open source project, members of a team, or talks at a
conference. Collections allow you to define a new type of document that behave
like Pages or Posts do normally, but also have their own unique properties and
namespace.
-->
페이지나 포스트가 전부는 아닙니다. 자신의 오픈 소스 프로젝트에 포함된 다양한
메소드나 팀 멤버들의 목록, 또는 컨퍼런스 대화 내용을 문서화하려는 경우도
생각해볼 수 있습니다. 콜렉션 기능을 사용하면 기본적으로는 페이지나 포스트처럼
동작하지만, 고유한 네임스페이스와 속성이 추가된 새로운 종류의 문서를 정의할 수
있습니다.

<!--
## Using Collections
-->
## 콜렉션 사용하기

<!--
To start using collections, follow these 3 steps:
-->
콜렉션을 사용하려면, 다음 세 단계를 따르세요:

<!--
* [Step 1: Tell Jekyll to read in your collection](#step1)
* [Step 2: Add your content](#step2)
* [Step 3: Optionally render your collection's documents into independent files](#step3)
-->
* [1 단계: Jekyll 에게 콜렉션을 읽도록 지시하기](#step1)
* [2 단계: 컨텐츠 추가하기](#step2)
* [3 단계: 콜렉션 내 문서를 독립적인 파일로 렌더링하기 (선택사항)](#step3)

<!--
### Step 1: Tell Jekyll to read in your collection {#step1}
-->
### 1 단계: Jekyll 에게 콜렉션을 읽도록 지시하기 {#step1}

<!--
Add the following to your site's `_config.yml` file, replacing `my_collection`
with the name of your collection:
-->
자신의 `_config.yml` 파일에 아래의 내용을 추가하고, `my_collection` 부분은
자신의 콜렉션 이름으로 바꾸세요:

```yaml
collections:
- my_collection
```

<!--
You can optionally specify metadata for your collection in the configuration:
-->
원한다면 콜렉션에 관련된 메타데이터를 정의할 수도 있습니다:

```yaml
collections:
  my_collection:
    foo: bar
```

<!--
Default attributes can also be set for a collection:
-->
콜렉션 속성들에 대한 기본값을 설정할 수도 있습니다:

```yaml
defaults:
  - scope:
      path: ""
      type: my_collection
    values:
      layout: page
```

<div class="note">
  <h5>콜렉션을 한 곳에 모으세요 {%- include docs_version_badge.html version="3.7.0" -%}</h5>

<!--
  <p>You can optionally specify a directory to store all your collections in the same place with <code>collections_dir: my_collections</code>.</p>
-->
  <p>선택사항으로서, 당신의 모든 콜렉션을 한 곳에 보관하기 위해 <code>collections_dir: my_collections</code> 로 디렉토리를 지정할 수 있습니다.</p>

<!--
  <p>Then Jekyll will look in <code>my_collections/_books</code> for the <code>books</code> collection, and
  in <code>my_collections/_recipes</code> for the <code>recipes</code> collection.</p>
-->
  <p>그럼 Jekyll 은 <code>books</code> 콜렉션에 대해서는 <code>my_collections/_books</code> 를,
  <code>recipes</code> 콜렉션에 대해서는 <code>my_collections/_recipes</code> 를 참고합니다.</p>
</div>

<div class="note warning">
<!--
  <h5>Be sure to move posts into custom collections directory</h5>
-->
  <h5>포스트를 콜렉션 디렉토리로 옮기세요</h5>

<!--
  <p>If you specify a directory to store all your collections in the same place with <code>collections_dir: my_collections</code>, then you will need to move your <code>_posts</code> directory to <code>my_collections/_posts</code>. Note that, the name of your collections directory cannot start with an underscore (`_`).</p>
-->
  <p>모든 콜렉션을 한 곳에 보관하려고 <code>collections_dir: my_collections</code> 로 디렉토리를 지정한 후에는, <code>_posts</code> 디렉토리를 <code>my_collections/_posts</code> 로 옮겨야 합니다. 한 가지 기억해야할 것은, 콜렉션을 보관하는 디렉토리 이름은 밑줄(`_`)로 시작할 수 없다는 것입니다.</p>
</div>

<!--
### Step 2: Add your content {#step2}
-->
### 2 단계: 컨텐츠 추가하기 {#step2}

<!--
Create a corresponding folder (e.g. `<source>/_my_collection`) and add
documents. YAML front matter is processed if the front matter exists, and everything
after the front matter is pushed into the document's `content` attribute. If no YAML front
matter is provided, Jekyll will not generate the file in your collection.
-->
설정한 콜렉션 이름에 맞는 폴더 (예시, `<source>/_my_collection`) 를 생성하고
문서를 추가합니다. 만약 YAML 머리말이 존재한다면 먼저 처리되고, 머리말 이후의 모든
내용은 문서의 `content` 속성에 들어갑니다. YAML 머리말이 없는 경우에는, 콜렉션에
파일이 생성되지 않습니다.

<div class="note info">
<!--
  <h5>Be sure to name your directories correctly</h5>
  <p>
The folder must be named identically to the collection you defined in
your <code>_config.yml</code> file, with the addition of the preceding <code>_</code> character.
  </p>
-->
  <h5>디렉토리 이름이 올바른지 확인하세요</h5>
  <p>
폴더의 이름은 반드시 <code>_config.yml</code> 파일에 정의한 콜렉션 이름 앞에 <code>_</code>
문자를 붙인 것이어야 합니다.
  </p>
</div>

<!--
### Step 3: Optionally render your collection's documents into independent files {#step3}
-->
### 3 단계: 콜렉션 내 문서를 독립적인 파일로 렌더링하기 (선택사항) {#step3}

<!--
If you'd like Jekyll to create a public-facing, rendered version of each
document in your collection, set the `output` key to `true` in your collection
metadata in your `_config.yml`:
-->
만약 콜렉션에 포함된 각각의 문서가 독립적인 버전으로 생성되게 하고 싶다면,
`_config.yml` 파일의 콜렉션 정의부분에 `output` 키를 추가하고 그 값을 `true` 로
설정합니다:

```yaml
collections:
  my_collection:
    output: true
```

<!--
This will produce a file for each document in the collection.
For example, if you have `_my_collection/some_subdir/some_doc.md`,
it will be rendered using Liquid and the Markdown converter of your
choice and written out to `<dest>/my_collection/some_subdir/some_doc.html`.
-->
이렇게 하면 콜렉션 안의 모든 문서가 각각 파일로 생성됩니다.
예를 들어, `_my_collection/some_subdir/some_doc.md` 라는 파일이 있다면,
당신이 선택한 마크다운 변환기와 Liquid 를 거쳐서
`<dest>/my_collection/some_subdir/some_doc.html` 로 만들어질 것입니다.

<!--
If you wish a specific page to be shown when accessing `/my_collection/`,
simply add `permalink: /my_collection/index.html` to a page.
To list items from the collection, on that page or any other, you can use:
-->
`/my_collection/` 에 접근할 때 특정한 페이지가 표시되도록 하고 싶다면,
그냥 페이지에 `permalink: /my_collection/index.html` 를 추가하세요.
해당 페이지 혹은 그 밖의 다른 곳에서 콜렉션의 아이템을 나열하려면, 이렇게 하세요:

{% raw %}
```liquid
{% for item in site.my_collection %}
  <h2>{{ item.title }}</h2>
  <p>{{ item.description }}</p>
  <p><a href="{{ item.url }}">{{ item.title }}</a></p>
{% endfor %}
```
{% endraw %}

<div class="note info">
<!--
  <h5>Don't forget to add YAML for processing</h5>
  <p>
  Files in collections that do not have front matter are treated as
  <a href="/docs/static-files">static files</a> and simply copied to their
  output location without processing.
  </p>
-->
  <h5>페이지 변환이 필요하다면 YAML 을 잊지 마세요</h5>
  <p>
  파일이 콜렉션에 포함되어 있다 할지라도 머리말이 없으면
  <a href="/docs/static-files">정적 파일</a>로 취급되어, 아무런 처리 과정을
  거치지 않고 출력 경로에 단순 복사됩니다.
  </p>
</div>

<!--
## Configuring permalinks for collections {#permalinks}
-->
## 콜렉션에 고유주소 설정하기 {#permalinks}

<!--
If you wish to specify a custom pattern for the URLs where your Collection pages
will reside, you may do so with the [`permalink` property](../permalinks/):
-->
콜렉션 페이지가 갖게될 URL 에 자신만의 패턴을 지정하고 싶은 경우, [`permalink` 속성](../permalinks/)을 사용할 수 있습니다:

```yaml
collections:
  my_collection:
    output: true
    permalink: /:collection/:name
```

<!--
### Examples
-->
### 예시

<!--
For a collection with the following source file structure,
-->
다음과 같은 소스 파일 구조에서,

```
_my_collection/
└── some_subdir
    └── some_doc.md
```

<!--
each of the following `permalink` configurations will produce the document structure shown below it.
-->
환경설정 `permalink` 의 값과 그에 따라 생성되는 문서 구조는 다음과 같습니다.


* **기본값**
  `permalink: /:collection/:path` 와 동일.

  ```
  _site/
  ├── my_collection
  │   └── some_subdir
  │       └── some_doc.html
  ...
  ```
* `permalink: pretty`
  `permalink: /:collection/:path/` 와 동일.

  ```
  _site/
  ├── my_collection
  │   └── some_subdir
  │       └── some_doc
  │           └── index.html
  ...
  ```
* `permalink: /doc/:path`

  ```
  _site/
  ├── doc
  │   └── some_subdir
  │       └── some_doc.html
  ...
  ```
* `permalink: /doc/:name`

  ```
  _site/
  ├── doc
  │   └── some_doc.html
  ...
  ```
* `permalink: /:name`

  ```
  _site/
  ├── some_doc.html
  ...
  ```

<!--
### Template Variables
-->
### 템플릿 변수

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
        <p><code>:collection</code></p>
      </td>
      <td>
<!--
        <p>Label of the containing collection.</p>
-->
        <p>콜렉션의 제목</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:path</code></p>
      </td>
      <td>
<!--
        <p>Path to the document relative to the collection's directory.</p>
-->
        <p>콜렉션 디렉토리에 상대적인 문서의 경로</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:name</code></p>
      </td>
      <td>
<!--
        <p>The document's base filename, with every sequence of spaces
        and non-alphanumeric characters replaced by a hyphen.</p>
-->
        <p> 문서의 기본 파일명 (알파벳과 숫자가 아닌 문자와 공백문자는 모두
        하이픈으로 교체됨).</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:title</code></p>
      </td>
      <td>
<!--
        <p>
          The <code>:title</code> template variable will take the
          <code>slug</code> <a href="/docs/frontmatter/">front matter</a>
          variable value if any is present in the document; if none is
          defined then <code>:title</code> will be equivalent to
          <code>:name</code>, aka the slug generated from the filename.
        </p>
-->
        <p>
          만약 문서에 <a href="/docs/frontmatter/">머리말</a>이 존재한다면
          머리말 변수 <code>slug</code> 의 값이 템플릿 변수
          <code>:title</code> 에 사용된다; 아무것도 정의되지 않았다면,
          파일명으로부터 슬러그가 생성되듯이, <code>:title</code> 은
          <code>:name</code> 과 동일하다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:output_ext</code></p>
      </td>
      <td>
<!--
        <p>Extension of the output file. (Included by default and usually unnecessary.)</p>
-->
        <p>출력 파일의 확장자. (기본적으로 포함되어 있고 일반적으로 불필요함.)</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Liquid Attributes
-->
## Liquid 속성

<!--
### Collections
-->
### 콜렉션

<!--
Each collection is accessible as a field on the `site` variable. For example, if
you want to access the `albums` collection found in `_albums`, you'd use
`site.albums`.
-->
모든 콜렉션은 `site` 변수의 한 필드로서 접근할 수 있습니다. 예를 들어, `_albums`
에 있는 `albums` 콜렉션에 접근하려고 한다면, `site.albums` 를 사용하면 됩니다.

<!--
Each collection is itself an array of documents (e.g., `site.albums` is an array of documents, much like `site.pages` and
`site.posts`). See the table below for how to access attributes of those documents.
-->
콜렉션 그 자체는 문서들에 대한 배열입니다 (예시, `site.albums` 는 `site.pages` 와 `site.posts` 거의 유사함).
이 문서들의 속성에 접근하는 방법은 아래 표를 참고하세요.

<!--
The collections are also available under `site.collections`, with the metadata
you specified in your `_config.yml` (if present) and the following information:
-->
콜렉션은 `site.collections` 로도 접근할 수 있으며, `_config.yml` 파일에
정의한 메타데이터와 다음 정보들도 사용할 수 있습니다:

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
        <p><code>label</code></p>
      </td>
      <td>
<!--
        <p>
          The name of your collection, e.g. <code>my_collection</code>.
        </p>
-->
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
<!--
        <p>
          An array of <a href="#documents">documents</a>.
        </p>
-->
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
<!--
        <p>
          An array of static files in the collection.
        </p>
-->
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
<!--
        <p>
          The path to the collection's source directory, relative to the site
          source.
        </p>
-->
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
<!--
        <p>
          The full path to the collections's source directory.
        </p>
-->
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
<!--
        <p>
          Whether the collection's documents will be output as individual
          files.
        </p>
-->
        <p>
          콜렉션의 문서들이 독립적인 파일로 출력될 것인지에 대한 여부

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note info">
<!--
  <h5>A Hard-Coded Collection</h5>
-->
  <h5>고정된 콜렉션</h5>
<!--
  <p>In addition to any collections you create yourself, the
  <code>posts</code> collection is hard-coded into Jekyll. It exists whether
  you have a <code>_posts</code> directory or not. This is something to note
  when iterating through <code>site.collections</code> as you may need to
  filter it out.</p>
-->
  <p>당신이 직접 생성한 콜렉션 외에, Jekyll 에는 <code>posts</code>
  라는 고정된 콜렉션이 있습니다. 이 콜렉션은 <code>_posts</code> 디렉토리와
  관계 없이 항상 존재합니다. 이를 기억해두어야 하는 이유는
  <code>site.collections</code> 값을 순회하는 경우 걸러내야 할 필요가 있을지도
  모르기 때문입니다.</p>
<!--
  <p>You may wish to use filters to find your collection:
  <code>{% raw %}{{ site.collections | where: "label", "myCollection" | first }}{% endraw %}</code></p>
-->
  <p>원하는 콜렉션을 찾기위해 필터를 사용하는 방법입니다:
  <code>{% raw %}{{ site.collections | where: "label", "myCollection" | first }}{% endraw %}</code></p>
</div>

<div class="note info">
<!--
  <h5>Collections and Time</h5>
-->
  <h5>콜렉션과 시간</h5>
<!--
  <p>Except for documents in hard-coded default collection <code>posts</code>, all documents in collections
    you create, are accessible via Liquid irrespective of their assigned date, if any, and therefore renderable.
  </p>
-->
  <p>고정된 기본 콜렉션 <code>posts</code> 의 문서를 제외한, 당신이 직접 생성한 콜렉션의 모든 문서는
  날짜가 지정되어 있는 경우에도 그와 관계없이 Liquid 변수로 접근이 가능합니다. 따라서 모든 문서가 생성됩니다.
  </p>
<!--
  <p>However documents are attempted to be written to disk only if the concerned collection
    metadata has <code>output: true</code>. Additionally, future-dated documents are only written if
    <code>site.future</code> <em>is also true</em>.
  </p>
-->
  <p>하지만 메타데이터에 <code>output: true</code> 를 가진 콜렉션의 문서들만 생성됩니다.
  또한, 미래-시간의 문서는 <code>site.future</code> 가 <em>참</em> 인 경우에만 생성됩니다.
  </p>
<!--
  <p>More fine-grained control over documents being written to disk can be exercised by setting
    <code>published: false</code> (<em><code>true</code> by default</em>) in the document's front matter.
  </p>
-->
  <p>문서 생성에 대한 더 세밀한 조정은 문서의 머리말에
  <code>published: false</code> 설정(<em>기본값 <code>true</code></em>)으로 가능합니다.
  </p>
</div>


<!--
### Documents
-->
### 문서 {#documents}

<!--
In addition to any YAML Front Matter provided in the document's corresponding
file, each document has the following attributes:
-->
모든 문서는 파일에 지정된 YAML 머리말뿐만 아니라, 다음과 같은 속성도 가지고
있습니다:

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
        <p><code>content</code></p>
      </td>
      <td>
<!--
        <p>
          The (unrendered) content of the document. If no YAML Front Matter is
          provided, Jekyll will not generate the file in your collection. If
          YAML Front Matter is used, then this is all the contents of the file
          after the terminating
          `---` of the front matter.
        </p>
-->
        <p>
          문서의 (변환되지 않은) 컨텐츠.
          YAML 머리말이 없다면, Jekyll 은 콜렉션에 어떠한 파일도 생성하지 않는다.
          YAML 머리말이 사용되었다면, 이 변수는 머리말의 종료표시인 `---`
          이후의 모든
          내용이다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
<!--
        <p>
          The rendered output of the document, based on the
          <code>content</code>.
        </p>
-->
        <p>
          <code>content</code> 에 기반하여 렌더링 된,
          문서의 출력
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>path</code></p>
      </td>
      <td>
<!--
        <p>
          The full path to the document's source file.
        </p>
-->
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
<!--
        <p>
          The path to the document's source file relative to the site source.
        </p>
-->
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
<!--
        <p>
          The URL of the rendered collection. The file is only written to the destination when the collection to which it belongs has <code>output: true</code> in the site's configuration.
          </p>
-->
        <p>
          렌더링 된 콜렉션의 URL. 사이트 환경설정에 <code>output: true</code> 를 가지고 있는 콜렉션의 파일들만 Site Destination 에 생성된다.
          </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
<!--
        <p>
          The name of the document's collection.
        </p>
-->
        <p>
          해당 문서가 포함된 콜렉션의 이름
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
<!--
        <p>
          The date of the document's collection.
        </p>
-->
        <p>
          문서가 속한 콜렉션의 날짜
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Accessing Collection Attributes
-->
## 콜렉션 속성 사용하기

<!--
Attributes from the YAML front matter can be accessed as data anywhere in the
site. Using the above example for configuring a collection as `site.albums`,
you might have front matter in an individual file structured as follows (which
must use a supported markup format, and cannot be saved with a `.yaml`
extension):
-->
YAML 머리말에 있는 속성은 데이터로서 사이트 내 어느 곳에서든 사용할 수
있습니다. 위 예제를 사용하여 `site.albums` 라는 콜렉션을 설정하는 경우,
개별 파일로 된 다음과 같은 구조의 머리말을 생각해볼 수 있습니다. (반드시
지원하는 마크업 언어로 작성해야 하며, `.yaml` 확장자가 아니어야
합니다):

```yaml
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
```

<!--
Every album in the collection could be listed on a single page with a template:
-->
다음 템플릿을 사용하면 콜렉션 내의 모든 앨범을 한 페이지에 출력할 수 있습니다:

```liquid
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
```
