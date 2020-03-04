---
#title: Converters
title: 변환기
permalink: /docs/plugins/converters/
---

<!--
If you have a new markup language you’d like to use with your site, you can
include it by implementing your own converter. Both the Markdown and
[Textile](https://github.com/jekyll/jekyll-textile-converter) markup
languages are implemented using this method.
-->
당신의 사이트에 사용하고자 하는 다른 마크업 언어가 있다면, 해당 언어를 처리할 수
있는 변환기를 직접 구현하면 됩니다. 마크업 언어 마크다운과
[Textile](https://github.com/jekyll/jekyll-textile-converter) 도 이
메소드를 사용해서 구현한 것입니다.

<div class="note info">
<!--
  <h5>Remember your Front Matter</h5>
  <p>
    Jekyll will only convert files that have a YAML header at the top, even for
    converters you add using a plugin.
  </p>
-->
  <h5>머리말을 잊지 마세요</h5>
  <p>
    Jekyll 은 오직 YAML 헤더로 시작하는 파일만 변환합니다. 변환기 플러그인을
    추가해서 사용할때도 마찬가지 입니다.
  </p>
</div>

<!--
Below is a converter that will take all posts ending in `.upcase` and process
them using the `UpcaseConverter`:
-->
아래 예제는 `.upcase` 로 끝나는 모든 포스트를 읽어서 `UpcaseConverter` 로
처리하는 변환기입니다:

```ruby
module Jekyll
  class UpcaseConverter < Converter
    safe true
    priority :low

    def matches(ext)
      ext =~ /^\.upcase$/i
    end

    def output_ext(ext)
      ".html"
    end

    def convert(content)
      content.upcase
    end
  end
end
```

<!--
Converters should implement at a minimum 3 methods:
-->
변환기는 최소한 아래 3 가지 메소드를 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Method</th>
      <th>Description</th>
-->
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>matches</code></p>
      </td>
<!--
      <td><p>
        Does the given extension match this converter’s list of acceptable
        extensions? Takes one argument: the file’s extension (including the
        dot). Must return <code>true</code> if it matches, <code>false</code>
        otherwise.
      </p></td>
-->
      <td><p>
        주어진 확장자가 이 변환기가 처리할 수 있는 확장자 목록에 포함되어
        있는가? 파라메터가 하나 필요합니다: 파일의 확장자 (점 포함). 포함되어
        있다면 <code>true</code> 를, 그렇지 않다면 <code>false</code> 를
        반환해야 합니다.
      </p></td>
    </tr>
    <tr>
      <td>
        <p><code>output_ext</code></p>
      </td>
<!--
      <td><p>
        The extension to be given to the output file (including the dot).
        Usually this will be <code>".html"</code>.
      </p></td>
-->
      <td><p>
        출력할 파일의 확장자 (점 포함). 일반적으로 <code>".html"</code> 가 될
        것입니다.
      </p></td>
    </tr>
    <tr>
      <td>
        <p><code>convert</code></p>
      </td>
<!--
      <td><p>
        Logic to do the content conversion. Takes one argument: the raw content
        of the file (without front matter). Must return a String.
      </p></td>
-->
      <td><p>
        컨텐츠를 변환하는 로직. 파라메터가 하나 필요합니다: 변환되지 않은 파일
        내용 (머리말 제외). 반드시 문자열을 반환해야 합니다.
      </p></td>
    </tr>
  </tbody>
</table>
</div>

<!--
In our example, `UpcaseConverter#matches` checks if our filename extension is
`.upcase`, and will render using the converter if it is. It will call
`UpcaseConverter#convert` to process the content. In our simple converter we’re
simply uppercasing the entire content string. Finally, when it saves the page,
it will do so with a `.html` extension.
-->
위 예제에서, `UpcaseConverter#matches` 는 확장자가 `.upcase` 인지 확인하고,
만약 그렇다면 변환기를 사용해 렌더링을 수행합니다. 변환기는 내용을 처리하기 위해
`UpcaseConverter#convert` 를 호출합니다. 이 예제의 변환기는 단순히 전체 내용을
대문자로 변환합니다. 마지막으로, 변환된 내용을 페이지로 저장할 때
`.html` 확장자를 사용합니다.
