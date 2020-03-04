---
#title: Collections
title: 컬렉션
permalink: /docs/collections/
---

<!--
Collections are a great way to group related content like members of a team or
talks at a conference.
-->
컬렉션은 서로 관련된 정보들 (예를 들면, 팀 멤버들의 목록, 또는 컨퍼런스 대화 내용) 을
그룹화하는데 아주 좋습니다.

<!--
## Setup
-->
## 셋업

<!--
To use a Collection you first need to define it in your `_config.yml`. For
example here's a collection of staff members:
-->
컬렉션을 사용하려면 먼저 `_config.yml` 에 컬렉션을 정의해야 합니다. 다음은
스태프 멤버 컬렉션에 대한 예시입니다:

```yaml
collections:
  - staff_members
```

<!--
In this case `collections` is defined as a sequence (i.e array) with no additional metadata defined for each collection.
You can optionally specify metadata for your collection by defining `collections` as a mapping (i.e hashmap) instead of sequence, and then defining additional fields in it:
-->
여기서 `collections` 는 시퀀스로 (예, 배열) 각각의 컬렉션에 대한 부가적인 메타데이터 없이 정의되었습니다.
컬렉션에 메타데이터를 지정하고 싶다면 컬렉션을 시퀀스가 아닌 매핑 (예, 해시맵) 으로 정의한 뒤, 그 안에 부가적인 필드들을 정의합니다:

```yaml
collections:
  staff_members:
    people: true
```

{: .note .info}
<!--
When defining a collection as a sequence, its pages will not be rendered by
default. To enable this, <code>output: true</code> must be specified on the
collection, which requires defining the collection as a mapping. For more
information, see the section <a href="#output">Output</a>.
-->
컬렉션을 시퀀스로 정의할 때, 포함된 페이지들이 자동으로 렌더링되지
않습니다. 이를 활성화하려면, 컬렉션에 <code>output: true</code> 가 지정되어
있어야 하는데, 이는 컬렉션을 매핑으로 정의하는 것과 같습니다. 더 자세한
내용은, <a href="#output">출력</a> 섹션을 참고하세요.

<div class="note">
<!--
  <h5>Gather your collections {%- include docs_version_badge.html version="3.7.0" -%}</h5>
-->
  <h5>컬렉션을 한 곳에 모으세요 {%- include docs_version_badge.html version="3.7.0" -%}</h5>

<!--
  <p>You can optionally specify a directory to store all your collections in the same place with <code>collections_dir: my_collections</code>.</p>
-->
  <p>선택사항으로서, 당신의 모든 컬렉션을 한 곳에 보관하기 위해 <code>collections_dir: my_collections</code> 로 디렉토리를 지정할 수 있습니다.</p>

<!--
  <p>Then Jekyll will look in <code>my_collections/_books</code> for the <code>books</code> collection, and
  in <code>my_collections/_recipes</code> for the <code>recipes</code> collection.</p>
-->
  <p>그럼 Jekyll 은 <code>books</code> 컬렉션에 대해서는 <code>my_collections/_books</code> 를,
  <code>recipes</code> 컬렉션에 대해서는 <code>my_collections/_recipes</code> 를 참고합니다.</p>
</div>

<div class="note warning">
<!--
  <h5>Be sure to move drafts and posts into custom collections directory</h5>
-->
  <h5>초안과 포스트를 컬렉션 디렉토리로 옮기세요</h5>

<!--
  <p>If you specify a directory to store all your collections in the same place with <code>collections_dir: my_collections</code>, then you will need to move your <code>_drafts</code> and <code>_posts</code> directory to <code>my_collections/_drafts</code> and <code>my_collections/_posts</code>. Note that, the name of your collections directory cannot start with an underscore (`_`).</p>
-->
  <p>모든 컬렉션을 한 곳에 보관하려고 <code>collections_dir: my_collections</code> 로 디렉토리를 지정한 후에는, <code>_drafts</code> 와 <code>_posts</code> 디렉토리를 <code>my_collections/_drafts</code> 와 <code>my_collections/_posts</code> 로 옮겨야 합니다. 한 가지 기억해야할 것은, 컬렉션을 보관하는 디렉토리 이름은 밑줄(`_`)로 시작할 수 없다는 것입니다.</p>
</div>

<!--
## Add content
-->
## 컨텐츠 추가하기 {#add_content}

<!--
Create a corresponding folder (e.g. `<source>/_staff_members`) and add
documents. Front matter is processed if the front matter exists, and everything
after the front matter is pushed into the document's `content` attribute. If no front
matter is provided, Jekyll will consider it to be a [static file](/docs/static-files/)
and the contents will not undergo further processing. If front matter is provided,
Jekyll will process the file contents into the expected output.
-->
설정한 컬렉션 이름에 맞는 폴더 (예시, `<source>/_staff_members`) 를 생성하고
문서를 추가합니다. 만약 머리말이 존재한다면 먼저 처리되고, 머리말 이후의 모든
내용은 문서의 `content` 속성에 들어갑니다. 머리말이 없는
경우, Jekyll 은 해당 파일을 [정적 파일](/docs/static-files/)로
간주하여 해당 파일의 내용은 처리과정을 거치지 않을 것입니다. 머리말이 있다면,
Jekyll 은 지정된 형식으로 출력하기 위해 해당 파일의 내용을 처리할 것입니다.

<!--
Regardless of whether front matter exists or not, Jekyll will write to the destination
directory (e.g. `_site`) only if `output: true` has been set in the collection's
metadata.
-->
머리말의 존재 여부와 관계 없이, Jekyll 은 컬렉션의 메타데이터에
`output: true` 가 설정되어 있는 경우에만 최종 디렉토리 (예, `_site`) 에
결과물을 생성할 것입니다.

<!--
For example here's how you would add a staff member to the collection set above.
The filename is `./_staff_members/jane.md` with the following content:
-->
아래 예시는 위 컬렉션에 스태프 멤버를 추가하는 방법입니다.
파일명은 `./_staff_members/jane.md` 이며 내용은 다음과 같습니다:

```markdown
---
name: Jane Doe
position: Developer
---
Jane has worked on Jekyll for the past *five years*.
```

<em>
<!--
  Do note that in spite of being considered as a collection internally, the above
  doesn't apply to [posts](/docs/posts/). Posts with a valid filename format will be
  marked for processing even if they do not contain front matter.
-->
  위 예시는 내부적으로 컬렉션으로 분류되지만, [포스트](docs/posts/)에는 적용되지
  않는다는 것을 기억하세요. 올바른 형식의 파일명을 가진 포스트는 머리말이 없는
  경우에도 처리됩니다.
</em>

<div class="note info">
<!--
  <h5>Be sure to name your directories correctly</h5>
-->
  <h5>디렉토리 이름이 올바른지 확인하세요</h5>
  <p>
<!--
The folder must be named identically to the collection you defined in
your <code>_config.yml</code> file, with the addition of the preceding <code>_</code> character.
-->
폴더의 이름은 반드시 <code>_config.yml</code> 파일에 정의한 컬렉션 이름 앞에 <code>_</code>
문자를 붙인 것이어야 합니다.
  </p>
</div>

<!--
## Output
-->
## 출력 {#output}

Now you can iterate over `site.staff_members` on a page and output the content
for each staff member. Similar to posts, the body of the document is accessed
using the `content` variable:

{% raw %}
```liquid
{% for staff_member in site.staff_members %}
  <h2>{{ staff_member.name }} - {{ staff_member.position }}</h2>
  <p>{{ staff_member.content | markdownify }}</p>
{% endfor %}
```
{% endraw %}

<!--
If you'd like Jekyll to create a rendered page for each document in your
collection, you can set the `output` key to `true` in your collection
metadata in `_config.yml`:
-->
컬렉션에 포함된 모든 문서를 렌더링하고 싶다면,
`_config.yml` 파일의 컬렉션 정의부분에 `output` 키를 `true` 로
설정합니다:

```yaml
collections:
  staff_members:
    output: true
```

<!--
You can link to the generated page using the `url` attribute:
-->
생성된 페이지에 대한 링크는 `url` 속성으로 얻을 수 있다:

{% raw %}
```liquid
{% for staff_member in site.staff_members %}
  <h2>
    <a href="{{ staff_member.url }}">
      {{ staff_member.name }} - {{ staff_member.position }}
    </a>
  </h2>
  <p>{{ staff_member.content | markdownify }}</p>
{% endfor %}
```
{% endraw %}

<!--
## Permalinks
-->
## 고유주소 {#permalinks}

<!--
There are special [permalink variables for collections](/docs/permalinks/) to
help you control the output url for the entire collection.
-->
[컬렉션을 위한 고유주소 변수](/docs/permalinks/)는 전체 컬렉션의 url 결과물을 제어할 수 있게 도와줍니다.

<!--
## Custom Sorting of Documents
-->
## 문서 순서 조정

<!--
By default, two documents in a collection are sorted by their `date` attribute when both of them have the `date` key in their front matter. However, if either or both documents do not have the `date` key in their front matter, they are sorted by their respective paths.
-->
디폴트로, 머리말에 `date` 키를 가지고 있는 두 문서가 있고 한 컬렉션에 이 두 문서가 들어있을 때 이 `date` 속성에 따라 정렬이 이루어 집니다. 하지만, 만약 어느 한쪽이나 양쪽 모두 머리말에 `date` 키가 없으면, 정렬은 각각의 경로에 따라 결정됩니다.

<!--
You can control this sorting via the collection's metadata.
-->
컬렉션의 메타 데이터를 통해 정렬방법을 조정할 수 있습니다.

<!--
### Sort By Front Matter Key
-->
### 머리말 키에 따른 정렬

<!--
Documents can be sorted based on a front matter key by setting a `sort_by` metadata to the front matter key string. For example,
to sort a collection of tutorials based on key `lesson`, the configuration would be:
-->
머리말에 메타 데이터 `sort_by` 를 설정해서 머리말 내용에 기반한 문서 정렬이 가능합니다. 예를 들어,
튜토리얼 컬렉션을 `lesson` 키에 따라 정렬하려면 다음과 같이 설정합니다:

```yaml
collections:
  tutorials:
    sort_by: lesson
```

<!--
The documents are arranged in the increasing order of the key's value. If a document does not have the front matter key defined
then that document is placed immediately after sorted documents. When multiple documents do not have the front matter key defined,
those documents are sorted by their dates or paths and then placed immediately after the sorted documents.
-->
문서들은 키 값에 따라 오름차순으로 정렬됩니다. 머리말에 키가 정의되지 않은 문서는
정렬된 문서 뒤에 오게됩니다. 하나 이상의 문서들의 머리말에 키가 정의되어 있지 않으면,
그 문서들끼리 날짜나 경로로 정렬된 후 앞서 정렬된 문서 뒤에 오게됩니다.

<!--
### Manually Ordering Documents
-->
### 문서 수동 정렬

<!--
You can also manually order the documents by setting an `order` metadata with **the filenames listed** in the desired order.
For example, a collection of tutorials would be configured as:
-->
또한 메타 데이터 `order` 에 원하는 순서로 **파일명을 나열해서** 수동으로 문서들을 정렬할 수 있습니다.
예를 들어, 튜토리얼 컬렉션은 다음과 같이 설정할 수 있습니다:

```yaml
collections:
  tutorials:
    order:
      - hello-world.md
      - introduction.md
      - basic-concepts.md
      - advanced-concepts.md
```

<!--
Any documents with filenames that do not match the list entry simply gets placed after the rearranged documents. If a document is
nested under subdirectories, include them in entries as well:
-->
목록에 존재하지 않는 파일명을 가진 문서는 정렬된 문서들 뒤에 위치하게 됩니다. 만약 문서가 하위 디렉토리에
들어있다면, 디렉토리도 목록에 포함시킵니다:

```yaml
collections:
  tutorials:
    order:
      - hello-world.md
      - introduction.md
      - concepts/basics.md
      - concepts/advanced.md
```

<!--
If both metadata keys have been defined properly, `order` list takes precedence.
-->
이 메타 데이터 키 둘 다 올바르게 정의되어 있으면, `order` 목록이 우선됩니다.

<!--
## Liquid Attributes
-->
## Liquid 속성

<!--
### Collections
-->
### 컬렉션

<!--
Collections are also available under `site.collections`, with the metadata
you specified in your `_config.yml` (if present) and the following information:
-->
컬렉션은 `site.collections` 로도 접근할 수 있으며, `_config.yml` 파일에
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
        <p>
<!--
          The name of your collection, e.g. <code>my_collection</code>.
-->
          컬렉션의 이름. 예시, <code>my_collection</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>docs</code></p>
      </td>
      <td>
        <p>
<!--
          An array of <a href="#documents">documents</a>.
-->
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
<!--
          An array of static files in the collection.
-->
          컬렉션 내의 정적 파일 배열.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>relative_directory</code></p>
      </td>
      <td>
        <p>
<!--
          The path to the collection's source directory, relative to the site
          source.
-->
          컬렉션 소스 디렉토리
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
<!--
          The full path to the collections's source directory.
-->
          컬렉션 소스 디렉토리 전체 경로
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
<!--
          Whether the collection's documents will be output as individual
          files.
-->
          컬렉션의 문서들이 독립적인 파일로 출력될 것인지에 대한
          여부.
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
  <h5>고정된 컬렉션</h5>
<!--
  <p>In addition to any collections you create yourself, the
  <code>posts</code> collection is hard-coded into Jekyll. It exists whether
  you have a <code>_posts</code> directory or not. This is something to note
  when iterating through <code>site.collections</code> as you may need to
  filter it out.</p>
-->
  <p>당신이 직접 생성한 컬렉션 외에, Jekyll 에는 <code>posts</code>
  라는 고정된 컬렉션이 있습니다. 이 컬렉션은 <code>_posts</code> 디렉토리와
  관계 없이 항상 존재합니다. 이를 기억해두어야 하는 이유는
  <code>site.collections</code> 값을 순회하는 경우 걸러내야 할 필요가 있을지도
  모르기 때문입니다.</p>
<!--
  <p>You may wish to use filters to find your collection:
  <code>{% raw %}{{ site.collections | where: "label", "myCollection" | first }}{% endraw %}</code></p>
-->
  <p>원하는 컬렉션을 찾기위해 필터를 사용하는 방법입니다:
  <code>{% raw %}{{ site.collections | where: "label", "myCollection" | first }}{% endraw %}</code></p>
</div>

<div class="note info">
<!--
  <h5>Collections and Time</h5>
-->
  <h5>컬렉션과 시간</h5>
<!--
  <p>Except for documents in hard-coded default collection <code>posts</code>, all documents in collections
    you create, are accessible via Liquid irrespective of their assigned date, if any, and therefore renderable.
  </p>
-->
  <p>고정된 기본 컬렉션 <code>posts</code> 의 문서를 제외한, 당신이 생성한 컬렉션의 모든 문서는
    날짜가 지정되어 있는 경우에도 그와 관계없이, Liquid 변수로 접근이 가능합니다. 따라서 모든 문서가 생성됩니다.
  </p>
<!--
  <p>Documents are attempted to be written to disk only if the concerned collection
    metadata has <code>output: true</code>. Additionally, future-dated documents are only written if
    <code>site.future</code> <em>is also true</em>.
  </p>
-->
  <p>메타데이터에 <code>output: true</code> 를 가진 컬렉션의 문서들만 생성됩니다.
  또한, 미래-시간의 문서는 <code>site.future</code> 도 <em>참</em> 인 경우에만
  생성됩니다.
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
In addition to any front matter provided in the document's corresponding
file, each document has the following attributes:
-->
모든 문서는 파일에 지정된 머리말뿐만 아니라, 다음과 같은 속성도 가지고
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
        <p>
<!--
          The (unrendered) content of the document. If no front matter is
          provided, Jekyll will not generate the file in your collection. If
          front matter is used, then this is all the contents of the file
          after the terminating
          `---` of the front matter.
-->
          문서의 (렌더링되지 않은) 컨텐츠.
          머리말이 없다면, Jekyll 은 컬렉션에 어떠한 파일도 생성하지 않는다.
          머리말이 사용되었다면, 이 변수는 머리말의 종료표시인 `---`
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
        <p>
<!--
          The rendered output of the document, based on the
          <code>content</code>.
-->
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
        <p>
<!--
          The full path to the document's source file.
-->
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
<!--
          The path to the document's source file relative to the site source.
-->
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
<!--
          The URL of the rendered collection. The file is only written to the destination when the collection to which it belongs has <code>output: true</code> in the site's configuration.
-->
          렌더링 된 컬렉션의 URL. 사이트 환경설정에 <code>output: true</code> 를 가지고 있는 컬렉션의 파일들만 Site Destination 에 생성된다.
          </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
        <p>
<!--
          The name of the document's collection.
-->
          해당 문서가 포함된 컬렉션의 이름
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p>
<!--
          The date of the document's collection.
-->
          문서가 속한 컬렉션의 날짜
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>
