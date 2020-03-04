---
#title: Liquid Filters
title: Liquid 필터
permalink: "/docs/liquid/filters/"
shopify_filter_url: https://shopify.github.io/liquid/filters/
shopify_filters:
- abs
- append
- at_least
- at_most
- capitalize
- ceil
- compact
- concat
- date
- default
- divided_by
- downcase
- escape
- escape_once
- first
- floor
- join
- last
- lstrip
- map
- minus
- modulo
- newline_to_br
- plus
- prepend
- remove
- remove_first
- replace
- replace_first
- reverse
- round
- rstrip
- size
- slice
- sort
- sort_natural
- split
- strip
- strip_html
- strip_newlines
- times
- truncate
- truncatewords
- uniq
- upcase
- url_decode
- url_encode
---

<!--
All of the standard Liquid [filters](#standard-liquid-filters) are supported (see below).
-->
표준 Liquid [필터](https://shopify.github.io/liquid/filters/abs/)를 모두 지원합니다 (아래 참조).

<!--
To make common tasks easier, Jekyll even adds a few handy filters of its own,
all of which you can find on this page. You can also create your own filters
using [plugins](/docs/plugins/).
-->
자주 수행하는 작업들을 더 쉽게하기 위해, Jekyll 만을 위한 몇 가지 유용한 필터가
추가되어 있으며, 모두 이 페이지에 설명되어 있습니다. 게다가
[플러그인](/docs/plugins/)을 사용하면 자신만의 필터도 만들 수 있습니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Description</th>
      <th><span class="filter">Filter</span> and <span class="output">Output</span></th>
-->
      <th>설명</th>
      <th><span class="filter">필터</span>와 <span class="output">출력</span></th>
    </tr>
  </thead>
  <tbody>
    {% for filter in site.data.jekyll_filters %}
      <tr>
        <td>
          <p class="name"><strong>{{ filter.name }}</strong></p>
          <p>
            {{- filter.description -}}
            {%- if filter.version_badge %}
              <span class="version-badge" title="This filter is available from version {{ filter.version_badge }}">
                {{- filter.version_badge -}}
              </span>
            {% endif -%}
          </p>
        </td>
        <td class="align-center">
          {%- for example in filter.examples %}
            <p><code class="filter">{{ example.input }}</code></p>
            {% if example.output %}<p><code class="output">{{ example.output }}</code></p>{% endif %}
          {% endfor -%}
        </td>
      </tr>
    {% endfor %}
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
- `latin`: like `default`, except Latin characters are first transliterated (e.g. `àèïòü` to `aeiou`) {%- include docs_version_badge.html version="3.7.0" -%}.
-->
- `none`: 필터링 안함
- `raw`: 공백문자
- `default`: 알파벳, 숫자가 아닌 문자 또는 공백문자
- `pretty`: 알파벳, 숫자가 아닌 문자 (`._~!$&'()+,;=@` 제외) 또는 공백문자
- `ascii`: 알파벳, 숫자, ASCII 가 아닌 문자 또는 공백문자
- `latin`: `default` 와 동일하나, 라틴 문자를 우선적으로 변환한다 (예, `àèïòü` 를 `aeiou` 로) {%- include docs_version_badge.html version="3.7.0" -%}.

<!--
### Detecting `nil` values with `where` filter {%- include docs_version_badge.html version="4.0" -%}
-->
### `where` 필터로 `nil` 값 찾기 {%- include docs_version_badge.html version="4.0" -%}

<!--
You can use the `where` filter to detect documents and pages with properties that are `nil` or `""`. For example,
-->
프로퍼티가 `nil` 이나 `""` 인 문서나 페이지를 찾기 위해 `where` 필터를 사용할 수 있습니다. 예를 들어,

<!--
```liquid
// Using `nil` to select posts that either do not have `my_prop` defined or `my_prop` has been set to `nil` explicitly.
{% raw %}{% assign filtered_posts = site.posts | where: 'my_prop', nil %}{% endraw %}
```
-->
```liquid
// `nil` 을 사용해서 `my_prop` 이 정의되어 있지 않거나 명시적으로 `nil` 이 설정되어 있는 포스트를 찾기
{% raw %}{% assign filtered_posts = site.posts | where: 'my_prop', nil %}{% endraw %}
```


<!--
```liquid
// Using Liquid's special literal `empty` or `blank` to select posts that have `my_prop` set to an empty value.
{% raw %}{% assign filtered_posts = site.posts | where: 'my_prop', empty %}{% endraw %}
```
-->
```liquid
// Liquid 의 특수 리터럴 `empty` 또는 `blank` 를 사용해서 변수 `my_prop` 의 값이 비어있는 포스트를 찾기
{% raw %}{% assign filtered_posts = site.posts | where: 'my_prop', empty %}{% endraw %}
```

<!--
### Binary operators in `where_exp` filter {%- include docs_version_badge.html version="4.0" -%}
-->
### 이항 연산자와 `where_exp` 필터 {%- include docs_version_badge.html version="4.0" -%}

<!--
You can use Liquid binary operators `or` and `and` in the expression passed to the `where_exp` filter to employ multiple
conditionals in the operation.
-->
Liquid 의 이항 연산자 `or` 와 `and` 를 사용한 표현식을 `where_exp` 필터에 전달하여
조건문을 여러 개 사용할 수 있습니다.

<!--
For example, to get a list of documents on English horror flicks, one could use the following snippet:
-->
예를 들어, 영어권의 공포영화에 대한 목록을 얻으려면, 다음 코드를 사용할 수 있을 것입니다:

```liquid
{% raw %}{{ site.movies | where_exp: "item", "item.genre == 'horror' and item.language == 'English'" }}{% endraw %}
```

<!--
Or to get a list of comic-book based movies, one may use the following:
-->
또, 만화를 기반으로한 영화의 목록을 얻으려 할 때, 다음과 같이 사용할 수도 있습니다:

```liquid
{% raw %}{{ site.movies | where_exp: "item", "item.sub_genre == 'MCU' or item.sub_genre == 'DCEU'" }}{% endraw %}
```

<!--
### Standard Liquid Filters
-->
### 기본 Liquid 필터

<!--
For your convenience, here is the list of all [Liquid filters]({{ page.shopify_filter_url }}) with links to examples in the official Liquid documentation.
-->
편의를 돕기 위해, 여기 [Liquid 필터]({{ page.shopify_filter_url }}) 전체 목록에 공식 Liquid 문서의 예제를 링크해두었습니다.

{% for filter in page.shopify_filters %}
- [{{ filter }}]({{ filter | prepend: page.shopify_filter_url | append: '/' }})
{% endfor %}
