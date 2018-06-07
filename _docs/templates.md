---
#title: Templates
title: 템플릿
permalink: /docs/templates/
---

<!--
Jekyll uses the [Liquid](https://shopify.github.io/liquid/) templating language to
process templates. All of the standard Liquid [tags](https://shopify.github.io/liquid/tags/control-flow/) and
[filters](https://shopify.github.io/liquid/filters/abs/) are
supported. To make common tasks easier, Jekyll even adds a few handy filters
and tags of its own, all of which you can find on this page. Jekyll even lets
you come up with your own tags via plugins.
-->
Jekyll 은 템플릿 처리 작업을 위해 [Liquid](https://shopify.github.io/liquid/) 템플릿
언어를 사용합니다. 표준 Liquid [태그](https://shopify.github.io/liquid/tags/control-flow/)와
[필터](https://shopify.github.io/liquid/filters/abs/)를
모두 지원합니다. 빈도가 높은 작업을 더 쉽게하기 위해, Jekyll 에만 추가된 필터와
태그도 있으며 모두 이 페이지에 설명되어 있습니다. 게다가 플러그인을 사용하면 Jekyll 에
자신만의 태그도 만들 수 있습니다.

<!--
## Filters
-->
## 필터 {#filters}

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Description</th>
      <th><span class="filter">Filter</span> and <span class="output">Output</span></th>
-->
      <th>설명</th>
      <th><span class="filter">필터</span>와 <span class="output">결과</span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
<!--
        <p class="name"><strong>Relative URL</strong></p>
        <p>Prepend the <code>baseurl</code> value to the input. Useful if your site is hosted at a subpath rather than the root of the domain.</p>
-->
        <p class="name"><strong>Relative URL</strong></p>
        <p>입력값 앞에 <code>baseurl</code> 값을 추가한다. 사이트가 최상위 경로가 아닌 하위 경로에서 호스팅 될 경우 유용하다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "/assets/style.css" | relative_url }}{% endraw %}</code>
        </p>
        <p>
         <code class="output">/my-baseurl/assets/style.css</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Absolute URL</strong></p>
        <p>Prepend the <code>url</code> and <code>baseurl</code> value to the input.</p>
-->
        <p class="name"><strong>Absolute URL</strong></p>
        <p>입력값 앞에 <code>url</code> 과 <code>baseurl</code> 값을 추가한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "/assets/style.css" | absolute_url }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">http://example.com/my-baseurl/assets/style.css</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to XML Schema</strong></p>
        <p>Convert a Date into XML Schema (ISO 8601) format.</p>
-->
        <p class="name"><strong>Date to XML Schema</strong></p>
        <p>날짜를 XML 스키마 (ISO 8601) 형식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_xmlschema }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">2008-11-07T13:07:54-08:00</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to RFC-822 Format</strong></p>
        <p>Convert a Date into the RFC-822 format used for RSS feeds.</p>
-->
        <p class="name"><strong>Date to RFC-822 Format</strong></p>
        <p>날짜를 RSS 피드에 사용하는 RFC-822 형식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_rfc822 }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">Mon, 07 Nov 2008 13:07:54 -0800</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to String</strong></p>
        <p>Convert a date to short format.</p>
-->
        <p class="name"><strong>Date to String</strong></p>
        <p>날짜를 짧은 형식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">07 Nov 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to String in ordinal US style</strong></p>
        <p>Format a date to ordinal, US, short format.</p>
-->
        <p class="name"><strong>Date to String in ordinal US style</strong></p>
        <p>날짜를 미국형 짧은 서수식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_string: "ordinal", "US" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">Nov 7th, 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to Long String</strong></p>
        <p>Format a date to long format.</p>
-->
        <p class="name"><strong>Date to Long String</strong></p>
        <p>날짜를 긴 형식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_long_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">07 November 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Date to Long String in ordinal UK style</strong></p>
        <p>Format a date to ordinal, UK, long format.</p>
-->
        <p class="name"><strong>Date to Long String in ordinal UK style</strong></p>
        <p>날짜를 영국형 긴 서수식으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_long_string: "ordinal" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">7th November 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Where</strong></p>
        <p>Select all the objects in an array where the key has the given value.</p>
-->
        <p class="name"><strong>Where</strong></p>
        <p>배열 안에서 특정 키와 값을 가진 객체들을 선택한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | where:"graduation_year","2014" }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Where Expression</strong></p>
        <p>Select all the objects in an array where the expression is true.
        {% include docs_version_badge.html version="3.2.0" %}</p>
-->
        <p class="name"><strong>Where Expression</strong></p>
        <p>배열 안에서 표현식이 참인 객체들을 선택한다.
        {% include docs_version_badge.html version="3.2.0" %}</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | where_exp:"item",
"item.graduation_year == 2014" }}{% endraw %}</code>
         <code class="filter">{% raw %}{{ site.members | where_exp:"item",
"item.graduation_year < 2014" }}{% endraw %}</code>
         <code class="filter">{% raw %}{{ site.members | where_exp:"item",
"item.projects contains 'foo'" }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Group By</strong></p>
        <p>Group an array's items by a given property.</p>
-->
        <p class="name"><strong>Group By</strong></p>
        <p>배열 안의 항목들을 특정 속성으로 그룹 짓는다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | group_by:"graduation_year" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">[{"name"=>"2013", "items"=>[...]},
{"name"=>"2014", "items"=>[...]}]</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Group By Expression</strong></p>
        <p>Group an array's items using a Liquid expression.
        {% include docs_version_badge.html version="3.4.0" %}</p>
-->
        <p class="name"><strong>Group By Expression</strong></p>
        <p>배열 안의 항목들을 Liquid 표현식을 사용해 그룹 짓는다.
        {% include docs_version_badge.html version="3.4.0" %}</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | group_by_exp:"item",
"item.graduation_year | truncate: 3, \"\"" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">[{"name"=>"201...", "items"=>[...]},
{"name"=>"200...", "items"=>[...]}]</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>XML Escape</strong></p>
        <p>Escape some text for use in XML.</p>
-->
        <p class="name"><strong>XML Escape</strong></p>
        <p>XML 에 사용되는 몇몇 텍스트를 이스케이프 한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.content | xml_escape }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>CGI Escape</strong></p>
        <p>
          CGI escape a string for use in a URL. Replaces any special characters
          with appropriate <code>%XX</code> replacements. CGI escape normally replaces a space with a plus <code>+</code> sign.
        </p>
-->
        <p class="name"><strong>CGI Escape</strong></p>
        <p>
          URL 에 사용되는 CGI 이스케이프 문자열. 모든 특수문자를 그에 맞는
          <code>%XX</code> 로 변환한다. 일반적으로 CGI 이스케이프에서는 공백이 <code>+</code> 문자로 교체된다.
        </p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "foo, bar; baz?" | cgi_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo%2C+bar%3B+baz%3F</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>URI Escape</strong></p>
        <p>
          Percent encodes any special characters in a URI. URI escape normally replaces a space with <code>%20</code>. <a href="https://en.wikipedia.org/wiki/Percent-encoding#Types_of_URI_characters">Reserved characters</a> will not be escaped.
        </p>
-->
        <p class="name"><strong>URI Escape</strong></p>
        <p>
          URI 에 있는 특수 문자들에 퍼센트 문자 인코딩을 한다. 일반적으로 URI 이스케이프에서는 공백이 <code>%20</code> 로 교체된다. <a href="https://en.wikipedia.org/wiki/Percent-encoding#Types_of_URI_characters">예약 문자들</a>은 이스케이프되지 않는다.
        </p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "http://foo.com/?q=foo, \bar?" | uri_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">http://foo.com/?q=foo,%20%5Cbar?</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Number of Words</strong></p>
        <p>Count the number of words in some text.</p>
-->
        <p class="name"><strong>Number of Words</strong></p>
        <p>텍스트 안의 단어 수.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.content | number_of_words }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">1337</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Array to Sentence</strong></p>
        <p>Convert an array into a sentence. Useful for listing tags. Optional argument for connector.</p>
-->
        <p class="name"><strong>Array to Sentence</strong></p>
        <p>배열을 한 문장으로 변환한다. 태그를 나열할 때 유용하다. 커넥터에는 선택사항이다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.tags | array_to_sentence_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo, bar, and baz</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ page.tags | array_to_sentence_string: 'or' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo, bar, or baz</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Markdownify</strong></p>
        <p>Convert a Markdown-formatted string into HTML.</p>
-->
        <p class="name"><strong>Markdownify</strong></p>
        <p>Markdown 포맷 문자열을 HTML 로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.excerpt | markdownify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Smartify</strong></p>
        <p>Convert "quotes" into &ldquo;smart quotes.&rdquo;</p>
-->
        <p class="name"><strong>Smartify</strong></p>
        <p>"일반 따옴표" 를 &ldquo;세련된 따옴표&rdquo;로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.title | smartify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Converting Sass/SCSS</strong></p>
        <p>Convert a Sass- or SCSS-formatted string into CSS.</p>
-->
        <p class="name"><strong>Converting Sass/SCSS</strong></p>
        <p>Sass 또는 SCSS 형식 문자열을 CSS 로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
          <code class="filter">{% raw %}{{ some_scss | scssify }}{% endraw %}</code>
          <code class="filter">{% raw %}{{ some_sass | sassify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Slugify</strong></p>
        <p>Convert a string into a lowercase URL "slug". See below for options.</p>
-->
        <p class="name"><strong>Slugify</strong></p>
        <p>문자열을 소문자 URL "슬러그"로 변환한다. 자세한 옵션은 아래를 참고하시오.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "The _config.yml file" | slugify }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-config-yml-file</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ "The _config.yml file" | slugify: 'pretty' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-_config.yml-file</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ "The _cönfig.yml file" | slugify: 'ascii' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-c-nfig-yml-file</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ "The cönfig.yml file" | slugify: 'latin' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-config-yml-file</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Data To JSON</strong></p>
        <p>Convert Hash or Array to JSON.</p>
-->
        <p class="name"><strong>Data To JSON</strong></p>
        <p>해시나 배열을 JSON 으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.data.projects | jsonify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Normalize Whitespace</strong></p>
        <p>Replace any occurrence of whitespace with a single space.</p>
-->
        <p class="name"><strong>Normalize Whitespace</strong></p>
        <p>모든 공백문자를 하나의 공백으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "a \n b" | normalize_whitespace }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Sort</strong></p>
        <p>Sort an array. Optional arguments for hashes: 1.&nbsp;property name 2.&nbsp;nils order (<em>first</em> or <em>last</em>).</p>
-->
        <p class="name"><strong>Sort</strong></p>
        <p>배열을 정렬한다. 해시에 사용하는 선택적 전달인자: 1.&nbsp;속성 이름 2.&nbsp;nils 순서 (<em>first</em> 또는 <em>last</em>).</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.tags | sort }}{% endraw %}</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ site.posts | sort: 'author' }}{% endraw %}</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ site.pages | sort: 'title', 'last' }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Sample</strong></p>
        <p>Pick a random value from an array. Optional: pick multiple values.</p>
-->
        <p class="name"><strong>Sample</strong></p>
        <p>배열 안에서 무작위로 선택한 값 하나. 선택사항: 값을 여러 개 선택한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.pages | sample }}{% endraw %}</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ site.pages | sample:2 }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>To Integer</strong></p>
        <p>Convert a string or boolean to integer.</p>
-->
        <p class="name"><strong>To Integer</strong></p>
        <p>문자열 또는 부울 값을 정수형으로 변환한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ some_var | to_integer }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Array Filters</strong></p>
        <p>Push, pop, shift, and unshift elements from an Array.</p>
        <p>These are <strong>NON-DESTRUCTIVE</strong>, i.e. they do not mutate the array, but rather make a copy and mutate that.</p>
-->
        <p class="name"><strong>Array Filters</strong></p>
        <p>배열에 항목을 삽입, 추출, 순환시킨다.</p>
        <p>이 필터는 <strong>비파괴적</strong>이다. 예시, 해당 배열을 직접 변경하지 않고, 복사본을 만든 후 변경한다.</p>
      </td>
      <td class="align-center">
        <p>
          <code class="filter">{% raw %}{{ page.tags | push: 'Spokane' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">['Seattle', 'Tacoma', 'Spokane']</code>
        </p>
        <p>
          <code class="filter">{% raw %}{{ page.tags | pop }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">['Seattle']</code>
        </p>
        <p>
          <code class="filter">{% raw %}{{ page.tags | shift }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">['Tacoma']</code>
        </p>
        <p>
          <code class="filter">{% raw %}{{ page.tags | unshift: "Olympia" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">['Olympia', 'Seattle', 'Tacoma']</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p class="name"><strong>Inspect</strong></p>
        <p>Convert an object into its String representation for debugging.</p>
-->
        <p class="name"><strong>Inspect</strong></p>
        <p>디버깅을 위해 객체를 문자열로 표시한다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ some_var | inspect }}{% endraw %}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
### Options for the `slugify` filter
-->
### `slugify` 필터의 옵션들

<!--
The `slugify` filter accepts an option, each specifying what to filter.
The default is `default`. They are as follows (with what they filter):
-->
`slugify` 필터에는 옵션이 있어서, 무엇을 필터링할 것인지 선택할 수 있습니다.
디폴트값은 `default` 입니다. 옵션값(과 그에 대한 필터링 대상)은 다음과 같습니다:

<!--
- `none`: no characters
- `raw`: spaces
- `default`: spaces and non-alphanumeric characters
- `pretty`: spaces and non-alphanumeric characters except for `._~!$&'()+,;=@`
- `ascii`: spaces, non-alphanumeric, and non-ASCII characters
- `latin`: like `default`, except Latin characters are first transliterated (e.g. `àèïòü` to `aeiou`) {%- include docs_version_badge.html version="3.7.0" -%}
-->
- `none`: 필터링 안함
- `raw`: 공백문자
- `default`: 알파벳, 숫자가 아닌 문자 또는 공백문자
- `pretty`: 알파벳, 숫자가 아닌 문자 (`._~!$&'()+,;=@` 제외) 또는 공백문자
- `ascii`: 알파벳, 숫자, ASCII 가 아닌 문자 또는 공백문자
- `latin`: like `default`, except Latin characters are first transliterated (e.g. `àèïòü` to `aeiou`) {%- include docs_version_badge.html version="3.7.0" -%}

## 태그
<!--
## Tags
-->

<!--
* [Includes](#includes)
* [Code snippet highlighting](#code-snippet-highlighting)
* [Linking to pages, collections and posts (the new and improved way)](#links)
* [Linking to posts (the old way)](#linking-to-posts)
-->
* [조각 파일](#includes)
* [코드 구문 강조](#code-snippet-highlighting)
* [페이지나 콜렉션, 게시물에 연결하기 (개선된 새로운 방식)](#links)
* [게시물에 연결하기 (기존 방식)](#linking-to-posts)

<!--
### Includes
-->
### 조각 파일

<!--
If you have small page snippets that you want to include in multiple places on your site, save the snippets as *include files* and insert them where required, by using the `include` tag:
-->
사이트의 여기저기에 삽입시키고자 하는 작은 페이지 조각들이 있다면, *조각 파일* 로 저장하고 `include` 태그를 사용해 필요한 곳에 삽입하세요:

{% raw %}
```liquid
{% include footer.html %}
```
{% endraw %}

<!--
Jekyll expects all *include files* to be placed in an `_includes` directory at the root of your source directory. In the above example, this will embed the contents of `_includes/footer.html` into the calling file.
-->
*조각 파일* 은 프로젝트 Site Source 디렉토리 안의 `_includes` 디렉토리에 넣어야 합니다. 위 예제의 경우, 이 코드를 포함하고 있는 파일에는 `_includes/footer.html` 의 내용이 삽입됩니다.

<!--
For more advanced information on using includes, see [Includes](../includes).
-->
조각 파일 사용법에 대한 더 자세한 설명에 대해서는, [조각 파일](../includes)을 살펴보세요.

<!--
### Code snippet highlighting
-->
### 코드 구문 강조

<!--
Jekyll has built in support for syntax highlighting of over 60 languages
thanks to [Rouge](http://rouge.jneen.net). Rouge is the default highlighter
in Jekyll 3 and above. To use it in Jekyll 2, set `highlighter` to `rouge`
and ensure the `rouge` gem is installed properly.
-->
[Rouge](http://rouge.jneen.net) 덕분에 Jekyll 은 60 개 이상의 언어에
대한 구문 강조 기능을 내장하고 있습니다.
Jekyll 3 와 그 이상의 버전에서는 Rouge 가 기본 구문 강조기입니다.
Jekyll 2 에서 사용하기 위해서는, `highlighter` 를 `rouge` 로 설정하고
`rouge` gem 이 제대로 설치되어 있는지 확인하세요.

<!--
Alternatively, you can use [Pygments](http://pygments.org) to highlight
your code snippets. To use Pygments, you must have Python installed on your
system, have the `pygments.rb` gem installed and set `highlighter` to
`pygments` in your site's configuration file. Pygments supports [over 100
languages](http://pygments.org/languages/)
-->
다른 방법으로는, [Pygments](http://pygments.org) 를 사용해 코드 조각에
구문 강조를 할 수 있습니다. Pygments 를 사용하기 위해서는, 시스템에
Python 과 `pygments.rb` gem 이 설치되어 있어야 하고, 사이트 환경설정 파일에
`highlighter` 를 `pygments` 로 설정해야 합니다. Pygments 는
[100 개 이상의 언어](http://pygments.org/languages/)를 지원합니다.

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
wiki](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers)
or the [Pygments' Lexers page](http://pygments.org/docs/lexers/).
-->
`highlight` 태그에 전달한 인자 (위 예시에서는 `ruby`) 는 언어 식별자입니다.
각 언어에 해당하는 구문 강조용 식별자를 찾으려면, [Rouge
위키](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers)
또는 [Pygments 의 Lexer 페이지](http://pygments.org/docs/lexers/)에서
“short name” 을 살펴보세요.

<div class="note info">
<!--
  <h5>Jekyll processes all Liquid filters in code blocks</h5>
  <p>If you are using a language that contains curly braces, you
    will likely need to place <code>{&#37; raw &#37;}</code> and
    <code>{&#37; endraw &#37;}</code> tags around your code.</p>
-->
  <h5>Jekyll 은 코드 블록 안에서도 Liquid 필터를 처리합니다</h5>
  <p>만약 당신이 사용하려는 언어에 중괄호가 포함되어 있다면, 당신의
    코드 앞 뒤를 <code>{&#37; raw &#37;}</code> 와
    <code>{&#37; endraw &#37;}</code> 태그로 감싸야 할 것입니다.</p>
</div>

<!--
#### Line numbers
-->
#### 줄 번호

<!--
There is a second argument to `highlight` called `linenos` that is optional.
Including the `linenos` argument will force the highlighted code to include line
numbers. For instance, the following code block would include line numbers next
to each line:
-->
`highlight` 의 두 번째 전달인자인 `linenos` 는 선택사항입니다.
전달인자 `linenos` 를 추가하면 구문 강조된 코드에 줄 번호를
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
#### Stylesheets for syntax highlighting
-->
#### 구문 강조용 스타일시트

<!--
In order for the highlighting to show up, you’ll need to include a highlighting
stylesheet. For an example stylesheet you can look at
[syntax.css](https://github.com/mojombo/tpw/tree/master/css/syntax.css). These
are the same styles as used by GitHub and you are free to use them for your own
site. If you use `linenos`, you might want to include an additional CSS class
definition for the `.lineno` class in `syntax.css` to distinguish the line
numbers from the highlighted code.
-->
강조 부분을 눈에 띄게 만들려면, 구문 강조용 스타일시트를 추가해야 합니다.
참고해볼만한 스타일시트로는
[syntax.css](https://github.com/mojombo/tpw/tree/master/css/syntax.css) 가
있습니다. 이 스타일은 GitHub 에서 사용하는 것과 동일하며 당신의 사이트에도
자유롭게 사용할 수 있습니다. `linenos` 를 사용하는 경우에는, `syntax.css` 에
`.lineno` 라는 CSS 클래스 선언을 추가해서 줄 번호와 구문 강조된 코드를 구분할 수
있습니다.


<!--
## Links
-->
## 링크

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
{{ site.baseurl }}{% link _collection/name-of-document.md %}
{{ site.baseurl }}{% link _posts/2016-07-26-name-of-post.md %}
{{ site.baseurl }}{% link news/index.html %}
{{ site.baseurl }}{% link /assets/files/doc.pdf %}
```
{% endraw %}

<!--
You can also use the `link` tag to create a link in Markdown as follows:
-->
다음과 같이 Markdown 안에서도 `link` 태그를 사용해 링크를 생성할 수 있습니다:

{% raw %}
```liquid
[Link to a document]({{ site.baseurl }}{% link _collection/name-of-document.md %})
[Link to a post]({{ site.baseurl }}{% link _posts/2016-07-26-name-of-post.md %})
[Link to a page]({{ site.baseurl }}{% link news/index.html %})
[Link to a file]({{ site.baseurl }}{% link /assets/files/doc.pdf %})
```
{% endraw %}

<!--
(Including `{% raw %}{{ site.baseurl }}{% endraw %}` is optional &mdash; it depends on whether you want to preface the page URL with the `baseurl` value.)
-->
(`{% raw %}{{ site.baseurl }}{% endraw %}` 을 사용하는 것은 선택사항입니다 &mdash; 페이지의 URL 에 `baseurl` 값을 포함시킬지 말지 당신의 결정에 달려있습니다.)

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
`link` 태그에는 필터를 추가할 수 없다는 것을 알아두세요. 예를 들어, `{% raw %}{% link mypage.html | append: "#section1" %} {% endraw %}` 처럼 Liquid 필터를 사용해 문자열을 추가할 수 없습니다. 페이지의 특정 부분에 링크하기 위해서는, 기본 HTML 링크나 Markdown 링크 방식을 사용해야 합니다.

<!--
The name of the file you want to link can be specified as a variable instead of an actual file name. For example, suppose you defined a variable in your page's front matter like this:
-->
링크하고자 하는 파일의 이름을 지정할 때 실제 파일 이름 대신 변수를 사용할 수 있습니다. 예를 들어, 다음과 같이 페이지의 머리말에 변수를 정의했다고 생각해봅시다:

```yaml
---
title: My page
my_variable: footer_company_a.html
---
```

<!--
You could then reference that variable in your link:
-->
그럼 링크에서 이 변수를 참조할 수 있습니다:

```liquid
{% raw %}{% link {{ page.my_variable }} %}{% endraw %}
```

<!--
In this example, the link would add link to the file `footer_company_a.html`.
-->
이 예제에서는, `footer_company_a.html` 파일에 대한 링크가 추가됩니다.

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
{{ site.baseurl }}{% post_url 2010-07-21-name-of-post %}
```
{% endraw %}

<!--
If you organize your posts in subdirectories, you need to include subdirectory path to the post:
-->
만약 게시물을 하위 디렉토리에 넣고 관리한다면, 하위 디렉토리 경로도 포함시켜야 합니다:

{% raw %}
```liquid
{{ site.baseurl }}{% post_url /subdir/2010-07-21-name-of-post %}
```
{% endraw %}

<!--
There is no need to include the file extension when using the `post_url` tag.
-->
`post_url` 태그를 사용할 때는 파일 확장자를 지정할 필요가 없습니다.

<!--
You can also use this tag to create a link to a post in Markdown as follows:
-->
다음과 같이 Markdown 에서도 이 태그를 사용하여 게시물 링크를 생성할 수 있습니다:

{% raw %}
```liquid
[Name of Link]({{ site.baseurl }}{% post_url 2010-07-21-name-of-post %})
```
{% endraw %}
