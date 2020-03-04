---
#title: Markdown Options
title: 마크다운 옵션
permalink: "/docs/configuration/markdown/"
---
<!--
The various Markdown renderers supported by Jekyll sometimes have extra options
available.
-->
Jekyll 은 다양한 마크다운 렌더러를 지원하며, 몇몇은 추가 옵션을 가지고 있기도
합니다.

### Kramdown

<!--
Kramdown is the default Markdown renderer for Jekyll. Below is a list of the
currently supported options:
-->
Kramdown 은 Jekyll 의 기본 마크다운 렌더러입니다. 다음은 현재 지원하는
옵션 목록입니다:

* **auto_id_prefix** - Prefix used for automatically generated header IDs
* **auto_id_stripping** - Strip all formatting from header text for automatic ID generation
* **auto_ids** - Use automatic header ID generation
* **coderay_bold_every** - Defines how often a line number should be made bold
* **coderay_css** - Defines how the highlighted code gets styled
* **coderay_default_lang** - Sets the default language for highlighting code blocks
* **coderay_line_number_start** - The start value for the line numbers
* **coderay_line_numbers** - Defines how and if line numbers should be shown
* **coderay_tab_width** - The tab width used in highlighted code
* **coderay_wrap** - Defines how the highlighted code should be wrapped
* **enable_coderay** - Use coderay for syntax highlighting
* **entity_output** - Defines how entities are output
* **footnote_backlink** - Defines the text that should be used for the footnote backlinks
* **footnote_backlink_inline** - Specifies whether the footnote backlink should always be inline
* **footnote_nr** - The number of the first footnote
* **gfm_quirks** - Enables a set of GFM specific quirks
* **hard_wrap** - Interprets line breaks literally
* **header_offset** - Sets the output offset for headers
* **html_to_native** - Convert HTML elements to native elements
* **line_width** - Defines the line width to be used when outputting a document
* **link_defs** - Pre-defines link definitions
* **math_engine** - Set the math engine
* **math_engine_opts** - Set the math engine options
* **parse_block_html** - Process kramdown syntax in block HTML tags
* **parse_span_html** - Process kramdown syntax in span HTML tags
* **smart_quotes** - Defines the HTML entity names or code points for smart quote output
* **syntax_highlighter** - Set the syntax highlighter
* **syntax_highlighter_opts** - Set the syntax highlighter options
* **toc_levels** - Defines the levels that are used for the table of contents
* **transliterated_header_ids** - Transliterate the header text before generating the ID
* **typographic_symbols** - Defines a mapping from typographical symbol to output characters

<div class="note warning">
<!--
  <h5>There are two unsupported kramdown options</h5>
-->
  <h5>Kramdown 옵션 중 지원하지 않는 두 가지 옵션이 있습니다</h5>
  <p>
<!--
    Please note that both <code>remove_block_html_tags</code> and
    <code>remove_span_html_tags</code> are currently unsupported in Jekyll due
    to the fact that they are not included within the kramdown HTML converter.
-->
    Kramdown HTML 변환기에 <code>remove_block_html_tags</code> 와
    <code>remove_span_html_tags</code> 가 포함되어 있지 않기 때문에, 현재 Jekyll
    에서도 지원하지 않습니다.
  </p>
</div>

<!--
For more details about these options have a look at the [Kramdown configuration documentation](https://kramdown.gettalong.org/options.html).
-->
이 옵션에 관련된 더 자세한 내용은 [Kramdown 환경설정 문서](https://kramdown.gettalong.org/options.html)를 살펴보세요.

### CommonMark

<!--
[CommonMark](https://commonmark.org/) is a rationalized version of Markdown syntax, implemented in C and thus faster than default Kramdown implemented in Ruby. It [slightly differs](https://github.com/commonmark/CommonMark#differences-from-original-markdown) from original Markdown and does not support all the syntax elements implemented in Kramdown, like [Block Inline Attribute Lists](https://kramdown.gettalong.org/syntax.html#block-ials).
-->
[CommonMark](https://commonmark.org/) 는 보다 합리적인 마크다운 문법으로서, C 로 구현되어 루비로 구현된 기본 Kramdown 보다 빠릅니다. 기존 마크다운과는 [약간 다른 부분](https://github.com/commonmark/CommonMark#differences-from-original-markdown)이 있으며 [블록 인라인 속성 목록](https://kramdown.gettalong.org/syntax.html#block-ials)과 같은 Kramdown 에는 구현되어 있는 일부 문법들을 지원하지 않습니다.

<!--
It comes in two flavors: basic CommonMark with [jekyll-commonmark](https://github.com/jekyll/jekyll-commonmark) plugin and [GitHub Flavored Markdown supported by GitHub Pages](https://github.com/github/jekyll-commonmark-ghpages).
-->
두 가지 형태로 제공됩니다: [jekyll-commonmark](https://github.com/jekyll/jekyll-commonmark) 플러그인의 기본 CommonMark 와 [GitHub Pages 에서 지원되는 GitHub Flavored Markdown](https://github.com/github/jekyll-commonmark-ghpages).

### Redcarpet

<!--
Redcarpet can be configured by providing an `extensions` sub-setting, whose
value should be an array of strings. Each string should be the name of one of
the `Redcarpet::Markdown` class's extensions; if present in the array, it will
set the corresponding extension to `true`.
-->
Redcarpet 을 사용하려면 `extensions` 라는 하위-설정에 문자열을 배열 형식으로
지정하면 됩니다. 배열 안에 들어갈 문자열은 `Redcarpet::Markdown` 클래스의
확장기능 이름이며, 배열 안에 지정된 문자열에 해당하는 확장기능의 값이 `true` 로
설정됩니다.

<!--
Jekyll handles two special Redcarpet extensions:
-->
Jekyll 이 처리할 수 있는 두 가지의 특별한 Redcarpet 확장기능이 있습니다:

<!--
- `no_fenced_code_blocks` --- By default, Jekyll sets the `fenced_code_blocks`
extension (for delimiting code blocks with triple tildes or triple backticks)
to `true`, probably because GitHub's eager adoption of them is starting to make
them inescapable. Redcarpet's normal `fenced_code_blocks` extension is inert
when used with Jekyll; instead, you can use this inverted version of the
extension for disabling fenced code.
-->
- `no_fenced_code_blocks` --- Jekyll 에서 `fenced_code_blocks` 확장기능 (틸데나
백틱문자 3 개로 코드 블록을 구분하는 기능) 의 디폴트 값은 `true` 인데,
아마도 오래전부터 GitHub 에서 이 방식으로 채택하고 있어서 점점 필수적으로
받아들여지고 있습니다. Redcarpet 자체적으로는 `fenced_code_blocks` 확장기능이
비활성화 되어 있습니다; 반대로 작동하는 이 버전을 대신 사용해서 코드 테두리를
비활성화 해도 됩니다.

<!--
Note that you can also specify a language for highlighting after the first
delimiter:
-->
또한, 첫 번째 구분자 바로 뒤에 언어를 명시하면 구문강조가 가능하다는 것도
알아두세요:

    ```ruby
    # ...ruby code
    ```

<!--
With both fenced code blocks and highlighter enabled, this will statically
highlight the code; without any syntax highlighter, it will add a
`class="LANGUAGE"` attribute to the `<code>` element, which can be used as a
hint by various JavaScript code highlighting libraries.
-->
코드 블록 테두리와 구문 강조기를 모두 활성화하면, 완전한 코드 구문 강조가
가능합니다; 구문 강조기능을 전혀 사용하지 않으면, `<code>` 요소에
`class="LANGUAGE"` 속성이 추가되어 자바스크립트 기반으로 작성된, 다양한 코드
구문 강조 라이브러리의 작동에 도움이 됩니다.

<!--
- `smart` --- This pseudo-extension turns on SmartyPants, which converts
  straight quotes to curly quotes and runs of hyphens to em (`---`) and en (`--`) dashes.
-->
- `smart` --- 이 의사(pseudo) 확장기능은 SmartyPants 를 활성화하여, 따옴표를
  인쇄용 따옴표로 변환하고 긴 줄표 (`---`) 와 작은 줄표 (`--`) 를 사용할 수 있게 해줍니다.

<!--
All other extensions retain their usual names from Redcarpet, and no renderer
options aside from `smart` can be specified in Jekyll. [A list of available
extensions can be found in the Redcarpet README file.](https://github.com/vmg/redcarpet/blob/v3.2.2/README.markdown#and-its-like-really-simple-to-use)
Make sure you're looking at the README for the right version of
Redcarpet: Jekyll currently uses v3.2.x. The most commonly used
extensions are:
-->
이 외의 다른 확장기능은 Redcarpet 의 확장기능과 동일한 이름을 갖고 있으며,
렌더러의 옵션 중 `smart` 를 제외한 다른 모든 옵션은 사용할 수 없습니다. [사용할 수 있는
확장기능 목록은 Redcarpet 의 README 파일을 확인하세요](https://github.com/vmg/redcarpet/blob/v3.2.2/README.markdown#and-its-like-really-simple-to-use).
올바른 Redcarpet 버전의 README 파일을 읽고있는 것인지 반드시
확인하세요: Jekyll 은 현재 v3.2.x 를 사용하고 있습니다. 자주 사용하는
확장기능은 다음과 같습니다:

- `tables`
- `no_intra_emphasis`
- `autolink`

<!--
### Custom Markdown Processors
-->
### 커스텀 마크다운 처리기 {#custom-markdown-processors}

<!--
If you're interested in creating a custom markdown processor, you're in luck! Create a new class in the `Jekyll::Converters::Markdown` namespace:
-->
커스텀 마크다운 처리기를 만드는 방법에 관심이 있다면, 참 운이 좋으시네요! `Jekyll::Converters::Markdown` 네임스페이스에 새 클래스를 생성하세요:

```ruby
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
```

<!--
Once you've created your class and have it properly set up either as a plugin
in the `_plugins` folder or as a gem, specify it in your `_config.yml`:
-->
클래스를 생성한 후, 루비 젬이나 `_plugins` 폴더에 플러그인으로 설정하는
작업을 올바르게 끝마쳤다면, 해당 클래스를 `_config.yml` 에 명시하세요:

```yaml
markdown: MyCustomProcessor
```
