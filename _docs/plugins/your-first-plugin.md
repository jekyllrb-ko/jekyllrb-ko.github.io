---
#title: Your first plugin
title: 당신의 첫 번째 플러그인
permalink: /docs/plugins/your-first-plugin/
---

<!--
Plugins allow you to extend Jekyll's behavior to fit your needs. There are six
types of plugins in Jekyll.
-->
플러그인을 사용해 자신이 원하는 바에 따라 Jekyll 의 작동방식을 확장할 수 있습니다.
여섯 종류의 Jekyll 플러그인이 있습니다.

<!--
## Generators
-->
## 생성기

<!--
[Generators](/docs/plugins/generators/) create content on your site.
For example:
-->
[생성기](/docs/plugins/generators/)는 사이트의 내용을 생성합니다.
예시:

<!--
* [jekyll-feed](https://github.com/jekyll/jekyll-feed) creates an Atom feed of
blog posts.
* [jekyll-archives](https://github.com/jekyll/jekyll-archives) creates archive
pages for blog categories and tags.
* [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap) creates a sitemap.
-->
* [jekyll-feed](https://github.com/jekyll/jekyll-feed) 는 블로그 포스트의
Atom 피드를 생성합니다.
* [jekyll-archives](https://github.com/jekyll/jekyll-archives) 는 블로그 카테고리와
태그에 대한 아카이브 페이지를 생성합니다.
* [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap) 은 사이트맵을 생성합니다.

<!--
## Converters
-->
## 변환기

<!--
[Converters](/docs/plugins/converters/) change a markup language into another
format. For example:
-->
[변환기](/docs/plugins/converters/)는 마크업 언어를 다른 형식으로 변환합니다.
예시:

<!--
* [jekyll-textile-converter](https://github.com/jekyll/jekyll-textile-converter)
converts textile to HTML.
* [jekyll-coffeescript](https://github.com/jekyll/jekyll-coffeescript) converts
Coffeescript to JavaScript.
* [jekyll-opal](https://github.com/jekyll/jekyll-opal) converts Ruby to
JavaScript.
-->
* [jekyll-textile-converter](https://github.com/jekyll/jekyll-textile-converter)
는 Textile 을 HTML 로 변환합니다.
* [jekyll-coffeescript](https://github.com/jekyll/jekyll-coffeescript) 는
Coffeescript 를 자바스크립트로 변환합니다.
* [jekyll-opal](https://github.com/jekyll/jekyll-opal) 은 루비를
자바스크립트로 변환합니다.

<!--
## Commands
-->
## 명령어

<!--
[Commands](/docs/plugins/commands/) extend the `jekyll` executable with
subcommands. For example:
-->
[명령어](/docs/plugins/commands/)는 `jekyll` 실행 파일의 기능을 하위 명령어
형태로 확장합니다. 예:

<!--
* [jekyll-compose](https://github.com/jekyll/jekyll-compose) adds subcommands
for creating a post, page or draft.
-->
* [jekyll-compose](https://github.com/jekyll/jekyll-compose) 는 포스트나 페이지,
초안을 생성하는 하위 명령어를 추가합니다.

<!--
## Tags
-->
## 태그

<!--
[Tags](/docs/plugins/tags/) create custom Liquid tags. For example:
-->
[태그](/docs/plugins/tags/)는 사용자 Liquid 태그를 생성합니다. 예:

<!--
* [jekyll-youtube](https://github.com/dommmel/jekyll-youtube) embeds a YouTube
video.
* [jekyll-asset-path-plugin](https://github.com/samrayner/jekyll-asset-path-plugin)
outputs a relative URL for assets.
* [jekyll-swfobject](https://github.com/sectore/jekyll-swfobject) embeds a SWF
object.
-->
* [jekyll-youtube](https://github.com/dommmel/jekyll-youtube) 은 유튜브 비디오를
임베드합니다.
* [jekyll-asset-path-plugin](https://github.com/samrayner/jekyll-asset-path-plugin)
은 에셋 파일에 대한 상대 URL 을 출력합니다.
* [jekyll-swfobject](https://github.com/sectore/jekyll-swfobject) 는 SWF 오브젝트를
임베드합니다.

<!--
## Filters
-->
## 필터

<!--
[Filters](/docs/plugins/filters/) create custom Liquid filters. For example:
-->
[필터](/docs/plugins/filters/)는 사용자 Liquid 필터를 생성합니다. 예:

<!--
* [jekyll-time-ago](https://github.com/markets/jekyll-timeago) - The distance
between two dates in words.
* [jekyll-toc](https://github.com/toshimaru/jekyll-toc) - Generates a table of
content.
* [jekyll-email-protect](https://github.com/vwochnik/jekyll-email-protect) -
Obfuscates emails to protect them from spam bots.
-->
* [jekyll-time-ago](https://github.com/markets/jekyll-timeago) - 두 날짜의
차이를 말로 표현.
* [jekyll-toc](https://github.com/toshimaru/jekyll-toc) - 목차를
생성한다.
* [jekyll-email-protect](https://github.com/vwochnik/jekyll-email-protect) -
스팸봇으로부터 이메일을 보호.

<!--
## Hooks
-->
## 훅

<!--
[Hooks](/docs/plugins/hooks/) give fine-grained control to extend the build
process.
-->
[훅](/docs/plugins/hooks/)은 사이트 생성 절차를 세밀하게 통제할 수 있게
해줍니다.

<!--
## Flags
-->
## 플래그

<!--
There are two flags to be aware of when writing a plugin:
-->
플러그인을 만들 때는 다음 두 플래그를 알아두어야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Flag</th>
      <th>Description</th>
-->
      <th>플래그</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>safe</code></p>
      </td>
      <td>
<!--
        <p>
          A boolean flag that informs Jekyll whether this plugin may be safely
          executed in an environment where arbitrary code execution is not
          allowed. This is used by GitHub Pages to determine which core plugins
          may be used, and which are unsafe to run. If your plugin does not
          allow for arbitrary code execution, set this to <code>true</code>.
          GitHub Pages still won’t load your plugin, but if you submit it for
          inclusion in core, it’s best for this to be correct!
        </p>
-->
        <p>
          이 플러그인이 임의의 코드가 실행되는 것이 금지된 환경에서도 안전하게
          실행될 수 있다는 것을 알려주는 이진값 플래그이다. GitHub Pages 는
          이 플래그를 사용해서 실행해도 안전한 Core 플러그인을 골라낸다.
          플러그인이 임의의 코드 실행이 없는 환경에서 사용되어야 한다면, 이
          플래그를 <code>true</code> 로 설정한다. GitHub Pages 는 그래도
          당신의 플러그인을 사용하지 않을 것이지만, Jekyll 프로젝트에
          포함시키려는 경우에는 이게 최선이 방법이다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>priority</code></p>
      </td>
      <td>
<!--
        <p>
          This flag determines what order the plugin is loaded in. Valid values
          are: <code>:lowest</code>, <code>:low</code>, <code>:normal</code>,
          <code>:high</code>, and <code>:highest</code>. Highest priority
          matches are applied first, lowest priority are applied last.
        </p>
-->
        <p>
          플러그인을 읽어들이는 순서를 결정하는 플래그이다. 사용할 수 있는
          값은 <code>:lowest</code> 와 <code>:low</code>, <code>:normal</code>,
          <code>:high</code>, <code>:highest</code> 이다. 우선순위가 높은
          플러그인이 먼저 적용되고, 우선순위가 낮은 플러그인이 나중에 적용된다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
To use one of the example plugins above as an illustration, here is how you’d
specify these two flags:
-->
앞서 설명한 플러그인 예제를 사용하려면, 다음과 같이 플래그를 설정해야
합니다:

```ruby
module Jekyll
  class UpcaseConverter < Converter
    safe true
    priority :low
    ...
  end
end
```

## Best Practices

<!--
The guides help you with the specifics of creating plugins. We also have some
recommended best practices to help structure your plugin.
-->
이 설명서는 플러그인 작성 방법에 대한 설명을 담고 있습니다. 그리고 플러그인의
구조를 관리하는데에 도움이 될 만한 모범 사례도 담고 있습니다.

<!--
We recommend using a [gem](/docs/ruby-101/#gems) for your plugin. This will
help you manage dependencies, keep separation from your site source code and
allow you to share functionality across multiple projects. For tips on creating
a gem take a look a the
[Ruby gems guide](https://guides.rubygems.org/make-your-own-gem/) or look
through the source code of an existing plugin such as
[jekyll-feed](https://github.com/jekyll/jekyll-feed).
-->
플러그인에 [젬](/docs/ruby-101/#gems)을 사용할 것을 권장합니다. 젬은
종속성 관리와 사이트 코드로부터의 분리에 도움이 되며, 다른 프로젝트들에도
기능을 공유할 수 있게 해줍니다.
젬 작성에 관한 팁은
[루비 젬 설명서](https://guides.rubygems.org/make-your-own-gem/) 또는
[jekyll-feed](https://github.com/jekyll/jekyll-feed) 와 같은
기존 플러그인의 소스코드를 참고하세요.
