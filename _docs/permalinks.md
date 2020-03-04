---
#title: Permalinks
title: 고유주소
permalink: /docs/permalinks/
---

<!--
Permalinks are the output path for your pages, posts, or collections. They
allow you to structure the directories of your source code different from the
directories in your output.
-->
고유주소는 페이지나 포스트, 컬렉션의 결과물 경로입니다. 이는
소스코드의 디렉토리 구조를 결과물 디렉토리와 다르게 구성할 수
있도록 해줍니다.

<!--
## Front Matter
-->
## 머리말 {#frontmatter}

<!--
The simplest way to set a permalink is using front matter. You set the
`permalink` variable in front matter to the output path you'd like.
-->
고유주소를 설정하는 가장 간단한 방법은 머리말을 사용하는 것입니다. 머리말에
`permalink` 변수를 설정해 원하는 결과물 경로를 지정합니다.

<!--
For example, you might have a page on your site located at
`/my_pages/about-me.html` and you want the output url to be `/about/`. In
front matter of the page you would set:
-->
예를 들어, 페이지 소스 코드의 경로가
`/my_pages/about-me.html` 이고 url 을 `/about/` 으로 만드려고 합니다. 페이지의
머리말에 다음과 같이 설정합니다:

```
---
permalink: /about/
---
```

<!--
## Global
-->
## 글로벌 {#global}

<!--
Setting a permalink in front matter for every page on your site is no fun.
Luckily, Jekyll lets you set the permalink structure globally in your `_config.yml`.
-->
소스 코드의 모든 페이지에 머리말로 고유주소를 설정하는 것은 즐겁지 않습니다.
다행하게도, Jekyll 은 `_config.yml` 에 글로벌 고유주소 구조를 설정할 수 있게 해줍니다.

<!--
To set a global permalink, you use the `permalink` variable in `_config.yml`.
You can use placeholders to your desired output. For example:
-->
글로벌 고유주소를 설정하려면, `_config.yml` 에 `permalink` 변수를 사용합니다.
Placeholder 를 사용할 수 있습니다. 예를 들면:

```yaml
permalink: /:categories/:year/:month/:day/:title:output_ext
```

<!--
Note that pages and collections (excluding `posts` and `drafts`) don't have time
and categories (for pages, the above `:title` is equivalent to `:basename`), these
aspects of the permalink style are ignored for the output.
-->
페이지와 컬렉션 (`posts` 와 `drafts` 제외) 은 시간과 카테고리 정보가 없어서
(페이지에서, 위 `:title` 에 상응하는 것은 `:basename` 이다), 이러한 내용들은
결과물에서 무시됩니다.

<!--
For example, a permalink style of
`/:categories/:year/:month/:day/:title:output_ext` for the `posts` collection becomes
`/:title.html` for pages and collections (excluding `posts` and `drafts`).
-->
예를 들어, `posts` 컬렉션의 고유주소 스타일이
`/:categories/:year/:month/:day/:title:output_ext` 일 때, 페이지와 컬렉션 (`posts` 와 `drafts` 제외) 에서는
`/:title.html` 이 됩니다.

### Placeholders

<!--
Here's the full list of placeholders available:
-->
다음은 사용할 수 있는 Placeholder 의 전체 목록입니다:


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
        <p><code>year</code></p>
      </td>
      <td>
        <p>
<!--
          Year from the post’s filename with four digits.
          May be overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 연도 전체 네 자리.
          머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_year</code></p>
      </td>
      <td>
        <p>
<!--
          Year from the post’s filename without the century. (00..99)
          May be overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 연도 끝 두 자리. (00..99)
          머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>month</code></p>
      </td>
      <td>
        <p>
<!--
          Month from the post’s filename. (01..12)
          May be overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 월. (01..12)
          머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_month</code></p>
      </td>
      <td>
        <p>
<!--
          Month without leading zeros from the post’s filename. May be
          overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 월. 자리수 채우기 없음. 머리말의
          <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_month</code></p>
      </td>
      <td>
<!--
        <p>Three-letter month abbreviation, e.g. “Jan”.</p>
-->
        <p>세 자리 월 축약형. 예시, “Jan”.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>long_month</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
<!--
        <p>Full month name, e.g. “January”.</p>
-->
        <p>전체 월. 예시, “January”.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>day</code></p>
      </td>
      <td>
        <p>
<!--
          Day of the month from the post’s filename. (01..31)
          May be overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 일. (01..31)
          머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_day</code></p>
      </td>
      <td>
        <p>
<!--
          Day of the month without leading zeros from the post’s filename.
          May be overridden via the document’s <code>date</code> front matter.
-->
          포스트 파일명 날짜의 일. 자리수 채우기 없음.
          머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>y_day</code></p>
      </td>
      <td>
<!--
        <p>Ordinal day of the year from the post’s filename, with leading zeros. (001..366)</p>
-->
        <p>포스트 파일명 날짜의 서수일. 자리수 채우기 포함. (001..366)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>w_year</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
        <p>Week year which may differ from the month year for up to three days at the start of January and end of December</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>week</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
        <p>Week number of the current year, starting with the first week having a majority of its days in January. (01..53)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>w_day</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
<!--
        <p>Day of the week, starting with Monday. (1..7)</p>
-->
        <p>숫자로 표현된 요일. 월요일부터 시작. (1..7)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_day</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
<!--
        <p>Three-letter weekday abbreviation, e.g. “Sun”.</p>
-->
        <p>세 자리 요일 축약형. 예시, “Sun”.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>long_day</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
<!--
        <p>Weekday name, e.g. “Sunday”.</p>
-->
        <p>요일명. 예시, “Sunday”.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>hour</code></p>
      </td>
      <td>
        <p>
<!--
          Hour of the day, 24-hour clock, zero-padded from the post’s
          <code>date</code> front matter. (00..23)
-->
          포스트 머리말 <code>date</code> 의 24 시간제, 두 자리 형식
          시간값. (00..23)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>minute</code></p>
      </td>
      <td>
        <p>
<!--
          Minute of the hour from the post’s <code>date</code> front matter. (00..59)
-->
          포스트 머리말 <code>date</code> 의 분값. (00..59)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>second</code></p>
      </td>
      <td>
        <p>
<!--
          Second of the minute from the post’s <code>date</code> front matter. (00..59)
-->
          포스트 머리말 <code>date</code> 의 초값. (00..59)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>
<!--
            Title from the document’s filename. May be overridden via
            the document’s <code>slug</code> front matter.
-->
            파일명에 명시된 문서의 제목. 머리말의
            <code>slug</code> 를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>slug</code></p>
      </td>
      <td>
        <p>
<!--
            Slugified title from the document’s filename (any character
            except numbers and letters is replaced as hyphen). May be
            overridden via the document’s <code>slug</code> front matter.
-->
            파일명에 명시된 문서 제목의 슬러그화 결과 (숫자와 글자가 아닌
            모든 문자를 하이픈으로 변경함). 머리말의 <code>slug</code> 로
            값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>
<!--
          The specified categories for this post. If a post has multiple
          categories, Jekyll will create a hierarchy (e.g. <code>/category1/category2</code>).
          Also Jekyll automatically parses out double slashes in the URLs,
          so if no categories are present, it will ignore this.
-->
          해당 포스트에 지정된 카테고리들. 만약 포스트가 여러 카테고리에
          속해있다면, 계층 구조로 URL 이 생성된다 (예시. <code>/category1/category2</code>).
          또한, Jekyll 은 URL 을 분석해서 연속된 슬래시를 자동으로 제거하기
          때문에, 카테고리가 하나도 없으면, Jekyll 은 이 변수를 무시한다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
### Built-in formats
-->
### 기본 제공 형식 {#builtinformats}

<!--
For posts, Jekyll also provides the following built-in styles for convenience:
-->
편의를 위해 Jekyll 은 포스트에 사용할 수 있는 내장된 스타일을 제공합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Permalink Style</th>
      <th>URL Template</th>
-->
      <th>고유주소 스타일</th>
      <th>URL 템플릿</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title:output_ext</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>pretty</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title/</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>ordinal</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:y_day/:title:output_ext</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>weekdate</code></p>
        <small>{% include docs_version_badge.html version="4.0" %}</small>
      </td>
      <td>
        <p><code>/:categories/:year/W:week/:short_day/:title:output_ext</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>none</code></p>
      </td>
      <td>
        <p><code>/:categories/:title:output_ext</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
Rather than typing `permalink: /:categories/:year/:month/:day/:title/`, you can just type `permalink: pretty`.
-->
`permalink: /:categories/:year/:month/:day/:title/` 가 아니라, 그냥 `permalink: pretty` 라고 입력해도 된다.

<div class="note info">
<!--
<h5>Specifying permalinks through the front matter</h5>
-->
<h5>머리말에서 고유주소 사용</h5>
<!--
<p>Built-in permalink styles are not recognized in front matter. As a result, <code>permalink: pretty</code> will not work.</p>
-->
<p>내장된 고유주소 스타일은 머리말에서는 인식되지 않습니다. 따라서, <code>permalink: pretty</code> 는 작동하지 않을 것입니다.</p>
</div>

<!--
### Collections
-->
### 컬렉션

<!--
For collections (including `posts` and `drafts`), you have the option to override
the global permalink in the collection configuration in `_config.yml`:
-->
컬렉션 (`posts` 와 `drafts` 포함) 의 경우, `_config.yml` 에 설정된 컬렉션
환경설정의 글로벌 고유주소를 덮어쓸 수 있는 방법이 있습니다:

```yaml
collections:
  my_collection:
    output: true
    permalink: /:collection/:name
```

<!--
Collections have the following placeholders available:
-->
컬렉션에서 사용할 수 있는 Placeholder 는 다음과 같습니다:

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
        <p>컬렉션의 레이블.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:path</code></p>
      </td>
      <td>
        <p>
<!--
          Path to the document relative to the collection's directory,
          including base filename of the document.
-->
          컬렉션 디렉토리에 따른,
          파일명을 포함한 문서의 경로
        </p>
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
        <p>모든 공백과 비-알파벳 문자를 하이픈으로 교체한
        문서의 파일명.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:title</code></p>
      </td>
      <td>
        <p>
<!--
          The <code>:title</code> template variable will take the
          <code>slug</code> <a href="/docs/front-matter/">front matter</a>
          variable value if any is present in the document; if none is
          defined then <code>:title</code> will be equivalent to
          <code>:name</code>, aka the slug generated from the filename.
-->
          만약 문서의 <a href="/docs/front-matter/">머리말</a>에
          <code>slug</code> 가 있다면, <code>:title</code> 템플릿 변수는
          이 값을 사용한다; 만약 존재하지 않으면
          <code>:title</code> 는 <code>:name</code> 와
          동일하며, 슬러그는 파일명으로부터 생성된다.
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
        <p>결과물 파일의 확장자. (기본적으로 포함되어 있으며 보통 불필요하다.)</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
### Pages
-->
### 페이지

<!--
For pages, you have to use front matter to override the global permalink,
and if you set a permalink via front matter defaults in `_config.yml`,
it will be ignored.
-->
페이지에서는, 글로벌 고유주소를 덮어쓰려면 머리말을 사용해야만 합니다.
그리고 `_config.yml` 에 머리말 기본값이 설정된 상태에서는
무시됩니다.

<!--
Pages have the following placeholders available:
-->
페이지에서 사용할 수 있는 Placeholder 는 다음과 같습니다:

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
        <p><code>:path</code></p>
      </td>
      <td>
        <p>
<!--
          Path to the page relative to the site's source directory, excluding
          base filename of the page.
-->
          사이트 소스 디렉토리에서의 파일명을 제외한 페이지 경로
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:basename</code></p>
      </td>
      <td>
<!--
        <p>The page's base filename</p>
-->
        <p>페이지의 파일명</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:output_ext</code></p>
      </td>
      <td>
        <p>
<!--
          Extension of the output file. (Included by default and usually
          unnecessary.)
-->
          결과물 파일의 확장자. (기본적으로 포함되어 있으며 보통
          불필요하다.)
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>
