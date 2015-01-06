---
layout: docs
title: 플러그인
prev_section: pagination
next_section: extras
permalink: /docs/plugins/
---

Jekyll 의 플러그인 시스템은 훅을 제공하기 때문에, 자신의 사이트에 꼭 맞는
컨텐츠를 생성할 수 있습니다. 따라서, Jekyll 의 소스코드를 직접 수정하지 않고도
자신의 코드가 실행되게 할 수 있습니다.

<div class="note info">
  <h5>GitHub Pages 와 플러그인</h5>
  <p>
    <a href="http://pages.github.com/">GitHub Pages</a> 는 Jekyll 을 사용합니다.
    하지만 모든 Pages 사이트는 보안상의 이유로 인하여, <code>--safe</code>
    옵션으로 사용자 플러그인이 비활성화된 상태에서 생성됩니다. 이 말은
    안타깝게도, GitHub Pages 에서는 당신의 플러그인을 사용할 수 없다는
    뜻입니다.<br><br>그래도 GitHub Pages 와 사용자 플러그인을 함께 사용하는
    방법이 있습니다. GitHub 에 소스를 직접 올리는 대신, 먼저 로컬상에서 변환한
    뒤에 생성된 파일을 올리면 됩니다.
  </p>
</div>

## 플러그인 설치하기

플러그인을 설치하는 방법은 세 가지가 있습니다:

1. Site Source 루트에 `_plugins` 디렉토리를 만드세요. 여기에 자신의 플러그인을
    넣습니다. Jekyll 은 사이트를 생성하기 직전에 이 디렉토리의 모든 `*.rb` 파일을
    읽어들입니다.
2. `_config.yml` 파일에 `gems` 라는 키로 배열을 추가하고 사용하려는 플러그인들의
    gem 이름을 나열하세요. 예를 들면 다음과 같습니다:

        gems: [jekyll-test-plugin, jekyll-jsonify, jekyll-assets]
        # This will require each of these gems automatically.
3. `Gemfile` 의 Bundler 그룹에 관련 플러그인을 추가합니다. 예를 들면 다음과
    같습니다:

        group :jekyll_plugins do
          gem "my-jekyll-plugin"
        end

<div class="note info">
  <h5>
    <code>_plugins</code> 와 <code>gems</code> 는
    동시에 사용할 수 있습니다
  </h5>
  <p>
    원한다면 앞서 언급한 두 가지 플러그인 옵션을 동시에 사용할 수 있습니다. 한
    쪽을 사용한다고 해서 다른 쪽을 사용하는데에 제약이 생기지 않습니다.
  </p>
</div>

일반적으로, 플러그인은 세 가지 카테고리 중 하나에 속하게 됩니다:

1. 생성기
2. 변환기
3. 태그

## 생성기

Jekyll 이 당신의 규칙에 따라 부가적인 컨텐츠를 생성하게 하려면, 생성기를 만들면
됩니다.

생성기는 `Jekyll::Generator` 의 하위 클래스로서,
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb)
인스턴스를 전달받는 `generate` 메소드 가지고 있습니다. `generate`
메소드의 리턴값은 무시됩니다.

Jekyll 이 컨텐츠 목록을 파악하고 난 뒤, 사이트가 생성되기 직전에 생성기가
실행됩니다.
YAML 머리말을 가진 페이지들은
[`Jekyll::Page`]({{ site.repository }}/blob/master/lib/jekyll/page.rb)
인스턴스로 저장되어 `site.pages` 로 사용할 수 있습니다. 정적 파일들은
[`Jekyll::StaticFile`]({{ site.repository }}/blob/master/lib/jekyll/static_file.rb)
인스턴스가 되어 `site.static_files` 로 사용할 수 있습니다.
더 자세한 내용은 [변수 문서 페이지](/docs/variables/)와
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb) 를
살펴보세요.

예를 들어, 생성기는 빌드 시점에 계산된 값을 템플릿 변수에 주입할 수 있습니다.
다음 예제 생성기는 `reading.html` 템플릿의 두 변수 `ongoing` 과 `done` 에 값을
채워 넣습니다:

{% highlight ruby %}
module Reading
  class Generator < Jekyll::Generator
    def generate(site)
      ongoing, done = Book.all.partition(&:ongoing?)

      reading = site.pages.detect {|page| page.name == 'reading.html'}
      reading.data['ongoing'] = ongoing
      reading.data['done'] = done
    end
  end
end
{% endhighlight %}

다음은 좀 더 복잡한 생성기로서, 새 페이지를 생성합니다:

{% highlight ruby %}
module Jekyll

  class CategoryPage < Page
    def initialize(site, base, dir, category)
      @site = site
      @base = base
      @dir = dir
      @name = 'index.html'

      self.process(@name)
      self.read_yaml(File.join(base, '_layouts'), 'category_index.html')
      self.data['category'] = category

      category_title_prefix = site.config['category_title_prefix'] || 'Category: '
      self.data['title'] = "#{category_title_prefix}#{category}"
    end
  end

  class CategoryPageGenerator < Generator
    safe true

    def generate(site)
      if site.layouts.key? 'category_index'
        dir = site.config['category_dir'] || 'categories'
        site.categories.each_key do |category|
          site.pages << CategoryPage.new(site, site.source, File.join(dir, category), category)
        end
      end
    end
  end

end
{% endhighlight %}

이 생성기는 `categories` 안에 각 카테고리 별로 파일을 생성하고,
`category_index.html` 레이아웃을 사용하여 각 카테고리 별 포스트 목록을
만듭니다.

생성기가 필수로 구현해야 할 메소드는 딱 하나입니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>generate</code></p>
      </td>
      <td>
        <p>컨텐츠를 생성합니다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 변환기

다른 마크업 언어를 사용하고 싶다면, 해당 언어를 처리할 수 있는 변환기를 직접
구현하면 됩니다. 기본으로 포함된 Markdown 과 Textile 지원도 이 메소드 사용해서
구현한 것입니다.

<div class="note info">
  <h5>YAML 머리말을 잊지 마세요</h5>
  <p>
    Jekyll 은 오직 YAML 머리말로 시작하는 파일만 변환합니다. 변환기 플러그인을
    추가해서 사용할때도 마찬가지 입니다.
  </p>
</div>

아래 예제는 `.upcase` 로 끝나는 모든 포스트를 읽어서 `UpcaseConverter` 로
처리하는 변환기입니다:

{% highlight ruby %}
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
{% endhighlight %}

변환기는 최소한 아래 3 가지 메소드를 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>matches</code></p>
      </td>
      <td><p>
        주어진 확장자가 이 변환기가 처리할 수 있는 확장자 목록에 포함되어
        있는가? 전달인자가 하나 필요합니다: 파일의 확장자 (점 포함). 포함되어
        있다면 <code>true</code> 를, 그렇지 않다면 <code>false</code> 를
        반환해야 합니다.
      </p></td>
    </tr>
    <tr>
      <td>
        <p><code>output_ext</code></p>
      </td>
      <td><p>
        출력할 파일의 확장자 (점 포함). 일반적으로 <code>".html"</code> 가 될
        것입니다.
      </p></td>
    </tr>
    <tr>
      <td>
        <p><code>convert</code></p>
      </td>
      <td><p>
        컨텐츠를 변환하는 로직. 전달인자가 하나 필요합니다: 변환되지 않은 파일
        내용 (YAML 머리말 제외). 반드시 문자열을 반환해야 합니다.
      </p></td>
    </tr>
  </tbody>
</table>
</div>

위 예제에서는, `UpcaseConverter#matches` 는 확장자가 `.upcase` 인지 확인하고,
만약 그렇다면 내용을 변환하기 위해 `UpcaseConverter#convert` 를 호출합니다.
이 예제에서 변환기는 단순히 전체 내용을 대문자로 변환합니다.
마지막으로, 변환된 내용을 페이지로 저장할 때 `.html` 확장자를 사용합니다.


## 명령어

버전 2.5.0 부터, Jekyll 은 `jekyll` 실행파일에 하위명령어를 추가로 제공하는
플러그인들로 확장될 수 있습니다. `Gemfile` 의 `:jekyll_plugins` 라는 그룹에 관련
플러그인을 추가하면 됩니다:

{% highlight ruby %}
group :jekyll_plugins do
  gem "my_fancy_jekyll_plugin"
end
{% endhighlight %}

각 `명령어` 는 반드시 `Jekyll::Command` 클래스의 하위 클래스이어야 하고
`init_with_program` 이라는 하나의 클래스 메소드를 가져야 합니다. 예를 들면 다음과 같습니다:

{% highlight ruby %}
class MyNewCommand < Jekyll::Command
  class << self
    def init_with_program(prog)
      prog.command(:new) do |c|
        c.syntax "new [options]"
        c.description 'Create a new Jekyll site.'

        c.option 'dest', '-d DEST, 'Where the site should go.'

        c.action do |args, options|
          Jekyll::Site.new_site_at(options['dest'])
        end
      end
    end
  end
end
{% endhighlight %}

명령어는 반드시 이 클래스 메소드를 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>init_with_program</code></p>
      </td>
      <td><p>
        이 메소드의 파라메터는 단 하나,
        <code><a href="http://github.com/jekyll/mercenary#readme">Mercenary::Program</a></code>
        인스턴스인데 이는 바로 Jekyll 프로그램 그 자체입니다. 프로그램에 따라,
        명령어는 위 문법을 사용해서 생성될 것입니다. 더 자세한 내용은,
        GitHub.com 의 Mercenary 저장소를 방문하세요.
      </p></td>
    </tr>
  </tbody>
</table>
</div>

## 태그

사이트에 자신의 Liquid 태그를 사용하고 싶다면,
태그 시스템의 훅을 사용하면 됩니다.
Jekyll 에 내장된 `highlight` 와 `include` 가 바로 그 예입니다.
다음 예제는 페이지가 생성된 시간을 출력해주는 Liquid 태그입니다:

{% highlight ruby %}
module Jekyll
  class RenderTimeTag < Liquid::Tag

    def initialize(tag_name, text, tokens)
      super
      @text = text
    end

    def render(context)
      "#{@text} #{Time.now}"
    end
  end
end

Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTag)
{% endhighlight %}

Liquid 태그는 최소한 다음 메소드는 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>render</code></p>
      </td>
      <td>
        <p>태그 컨텐츠를 출력합니다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

그리고 다음과 같이 Liquid 템플릿 엔진에 태그를 등록해야
합니다:

{% highlight ruby %}
Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTag)
{% endhighlight %}

이렇게 하면, 페이지의 어느 곳에서나 다음과 같이 태그를 사용할 수
있습니다:

{% highlight ruby %}
{% raw %}
<p>{% render_time page rendered at: %}</p>
{% endraw %}
{% endhighlight %}

그러면 다음과 같은 결과를 얻을 수 있습니다:

{% highlight html %}
<p>page rendered at: Tue June 22 23:38:47 –0500 2010</p>
{% endhighlight %}

### Liquid 필터

Liquid 템플릿 시스템에 필터를 추가하는 것은 위에 설명한 태그 추가 방법과 상당히
유사합니다. 필터는 단지 자신의 메소드를 Liquid 로 보내는 모듈일 뿐입니다. 모든
메소드에는 최소한 하나의 매개변수가 있어야 하며, 이것은 바로 필터의 입력입니다.
반환 값이 필터의 출력이 됩니다.

{% highlight ruby %}
module Jekyll
  module AssetFilter
    def asset_url(input)
      "http://www.example.com/#{input}?#{Time.now.to_i}"
    end
  end
end

Liquid::Template.register_filter(Jekyll::AssetFilter)
{% endhighlight %}

<div class="note">
  <h5>ProTip™: Liquid 를 사용해서 site 객체에 접근할 수 있습니다</h5>
  <p>
    Jekyll 은 <code>context.registers[:site]</code> 와 같이 Liquid 의
    <code>context.registers</code> 기능을 통해서 <code>site</code> 객체에 접근할
    수 있게 해줍니다. 예를 들어, <code>context.registers[:site].config</code>
    라고 입력하여 전역 환경설정 파일 <code>_config.yml</code> 에 접근할 수 있습니다.
  </p>
</div>

### 플래그

플러그인을 만들 때는 다음 두 플래그를 알아두어야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
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
        <p>
          이 플러그인이 임의의 코드가 실행되는 것이 금지된 환경에서도 안전하게
          실행될 수 있다는 것을 알려주는 boolean 플래그입니다. GitHub Pages 는
          실행해도 안전한 Core 플러그인을 골라내기 위해 이 플래그를 사용합니다.
          플러그인이 임의의 코드 실행이 없는 환경에서 사용되어야 한다면, 이
          플래그를 <code>true</code> 로 설정하세요. GitHub Pages 는 여전히
          당신의 플러그인을 사용하지 않을 것입니다. 하지만, Jekyll 프로젝트에
          포함시키려는 경우에는 이게 제일 좋은 방법입니다!
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>priority</code></p>
      </td>
      <td>
        <p>
          플러그인을 읽어들이는 순서를 결정하는 플래그입니다. 사용할 수 있는
          값은 <code>:lowest</code> 와 <code>:low</code>, <code>:normal</code>,
          <code>:high</code>, <code>:highest</code> 입니다. 우선순위가 높은
          플러그인이 먼저 적용되고, 우선순위가 낮은 플러그인이 나중에 적용됩니다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

앞서 설명한 플러그인 예제를 사용하려면, 다음과 같이 플래그를 설정해야
합니다:

{% highlight ruby %}
module Jekyll
  class UpcaseConverter < Converter
    safe true
    priority :low
    ...
  end
end
{% endhighlight %}

## 사용가능한 플러그인

유용한 플러그인들을 모아두었습니다:

#### 생성기

- [ArchiveGenerator by Ilkka Laukkanen](https://gist.github.com/707909): Uses [this archive page](https://gist.github.com/707020) to generate archives.
- [LESS.js Generator by Andy Fowler](https://gist.github.com/642739): Renders LESS.js files during generation.
- [Version Reporter by Blake Smith](https://gist.github.com/449491): Creates a version.html file containing the Jekyll version.
- [Sitemap.xml Generator by Michael Levin](https://github.com/kinnetica/jekyll-plugins): Generates a sitemap.xml file by traversing all of the available posts and pages.
- [Full-text search by Pascal Widdershoven](https://github.com/PascalW/jekyll_indextank): Adds full-text search to your Jekyll site with a plugin and a bit of JavaScript.
- [AliasGenerator by Thomas Mango](https://github.com/tsmango/jekyll_alias_generator): Generates redirect pages for posts when an alias is specified in the YAML Front Matter.
- [Pageless Redirect Generator by Nick Quinlan](https://github.com/nquinlan/jekyll-pageless-redirects): Generates redirects based on files in the Jekyll root, with support for htaccess style redirects.
- [RssGenerator by Assaf Gelber](https://github.com/agelber/jekyll-rss): Automatically creates an RSS 2.0 feed from your posts.
- [Monthly archive generator by Shigeya Suzuki](https://github.com/shigeya/jekyll-monthly-archive-plugin): Generator and template which renders monthly archive like MovableType style, based on the work by Ilkka Laukkanen and others above.
- [Category archive generator by Shigeya Suzuki](https://github.com/shigeya/jekyll-category-archive-plugin): Generator and template which renders category archive like MovableType style, based on Monthly archive generator.
- [Emoji for Jekyll](https://github.com/yihangho/emoji-for-jekyll): Seamlessly enable emoji for all posts and pages.
- [Compass integration for Jekyll](https://github.com/mscharley/jekyll-compass): Easily integrate Compass and Sass with your Jekyll website.
- [Pages Directory by Ben Baker-Smith](https://github.com/bbakersmith/jekyll-pages-directory): Defines a `_pages` directory for page files which routes its output relative to the project root.
- [Page Collections by Jeff Kolesky](https://github.com/jeffkole/jekyll-page-collections): Generates collections of pages with functionality that resembles posts.
- [Windows 8.1 Live Tile Generation by Matt Sheehan](https://github.com/sheehamj13/jekyll-live-tiles): Generates Internet Explorer 11 config.xml file and Tile Templates for pinning your site to Windows 8.1.
- [Jekyll::AutolinkEmail by Ivan Tse](https://github.com/ivantsepp/jekyll-autolink_email): Autolink your emails.
- [Jekyll::GitMetadata by Ivan Tse](https://github.com/ivantsepp/jekyll-git_metadata): Expose Git metadata for your templates.
- [Jekyll Http Basic Auth Plugin](https://gist.github.com/snrbrnjna/422a4b7e017192c284b3): Plugin to manage http basic auth for jekyll generated pages and directories.

#### 변환기

- [Slim plugin](https://github.com/slim-template/jekyll-slim): Slim converter and includes for Jekyll with support for Liquid tags.
- [Jade plugin by John Papandriopoulos](https://github.com/snappylabs/jade-jekyll-plugin): Jade converter for Jekyll.
- [HAML plugin by Sam Z](https://gist.github.com/517556): HAML converter for Jekyll.
- [HAML-Sass Converter by Adam Pearson](https://gist.github.com/481456): Simple HAML-Sass converter for Jekyll. [Fork](https://gist.github.com/528642) by Sam X.
- [Sass SCSS Converter by Mark Wolfe](https://gist.github.com/960150): Sass converter which uses the new CSS compatible syntax, based Sam X’s fork above.
- [LESS Converter by Jason Graham](https://gist.github.com/639920): Convert LESS files to CSS.
- [LESS Converter by Josh Brown](https://gist.github.com/760265): Simple LESS converter.
- [Upcase Converter by Blake Smith](https://gist.github.com/449463): An example Jekyll converter.
- [CoffeeScript Converter by phaer](https://gist.github.com/959938): A [CoffeeScript](http://coffeescript.org) to Javascript converter.
- [Markdown References by Olov Lassus](https://github.com/olov/jekyll-references): Keep all your markdown reference-style link definitions in one \_references.md file.
- [Stylus Converter](https://gist.github.com/988201): Convert .styl to .css.
- [ReStructuredText Converter](https://github.com/xdissent/jekyll-rst): Converts ReST documents to HTML with Pygments syntax highlighting.
- [Jekyll-pandoc-plugin](https://github.com/dsanson/jekyll-pandoc-plugin): Use pandoc for rendering markdown.
- [Jekyll-pandoc-multiple-formats](https://github.com/fauno/jekyll-pandoc-multiple-formats) by [edsl](https://github.com/edsl): Use pandoc to generate your site in multiple formats. Supports pandoc’s markdown extensions.
- [Transform Layouts](https://gist.github.com/1472645): Allows HAML layouts (you need a HAML Converter plugin for this to work).
- [Org-mode Converter](https://gist.github.com/abhiyerra/7377603): Org-mode converter for Jekyll.
- [Customized Kramdown Converter](https://github.com/mvdbos/kramdown-with-pygments): Enable Pygments syntax highlighting for Kramdown-parsed fenced code blocks.
- [Bigfootnotes Plugin](https://github.com/TheFox/jekyll-bigfootnotes): Enables big footnotes for Kramdown.

#### 필터

- [Truncate HTML](https://github.com/MattHall/truncatehtml) by [Matt Hall](http://codebeef.com): A Jekyll filter that truncates HTML while preserving markup structure.
- [Domain Name Filter by Lawrence Woodman](https://github.com/LawrenceWoodman/domain_name-liquid_filter): Filters the input text so that just the domain name is left.
- [Summarize Filter by Mathieu Arnold](https://gist.github.com/731597): Remove markup after a `<div id="extended">` tag.
- [i18n_filter](https://github.com/gacha/gacha.id.lv/blob/master/_plugins/i18n_filter.rb): Liquid filter to use I18n localization.
- [Smilify](https://github.com/SaswatPadhi/jekyll_smilify) by [SaswatPadhi](https://github.com/SaswatPadhi): Convert text emoticons in your content to themeable smiley pics.
- [Read in X Minutes](https://gist.github.com/zachleat/5792681) by [zachleat](https://github.com/zachleat): Estimates the reading time of a string (for blog post content).
- [Jekyll-timeago](https://github.com/markets/jekyll-timeago): Converts a time value to the time ago in words.
- [pluralize](https://github.com/bdesham/pluralize): Easily combine a number and a word into a gramatically-correct amount like “1 minute” or “2 minute**s**”.
- [reading_time](https://github.com/bdesham/reading_time): Count words and estimate reading time for a piece of text, ignoring HTML elements that are unlikely to contain running text.
- [Table of Content Generator](https://github.com/dafi/jekyll-toc-generator): Generate the HTML code containing a table of content (TOC), the TOC can be customized in many way, for example you can decide which pages can be without TOC.
- [jekyll-humanize](https://github.com/23maverick23/jekyll-humanize): This is a port of the Django app humanize which adds a "human touch" to data. Each method represents a Fluid type filter that can be used in your Jekyll site templates. Given that Jekyll produces static sites, some of the original methods do not make logical sense to port (e.g. naturaltime).
- [Jekyll-Ordinal](https://github.com/PatrickC8t/Jekyll-Ordinal): Jekyll liquid filter to output a date ordinal such as "st", "nd", "rd", or "th".
- [Deprecated articles keeper](https://github.com/kzykbys/JekyllPlugins) by [Kazuya Kobayashi](http://blog.kazuya.co/): A simple Jekyll filter which monitor how old an article is.
- [Jekyll-jalali](https://github.com/mehdisadeghi/jekyll-jalali) by [Mehdi Sadeghi](http://mehdix.ir): A simple Gregorian to Jalali date converter filter.
- [Jekyll Thumbnail Filter](https://github.com/matallo/jekyll-thumbnail-filter): Related posts thumbnail filter.

#### 태그

- [Asset Path Tag](https://github.com/samrayner/jekyll-asset-path-plugin) by [Sam Rayner](http://www.samrayner.com/): Allows organisation of assets into subdirectories by outputting a path for a given file relative to the current post or page.
- [Delicious Plugin by Christian Hellsten](https://github.com/christianhellsten/jekyll-plugins): Fetches and renders bookmarks from delicious.com.
- [Ultraviolet Plugin by Steve Alex](https://gist.github.com/480380): Jekyll tag for the [Ultraviolet](https://github.com/grosser/ultraviolet) code highligher.
- [Tag Cloud Plugin by Ilkka Laukkanen](https://gist.github.com/710577): Generate a tag cloud that links to tag pages.
- [GIT Tag by Alexandre Girard](https://gist.github.com/730347): Add Git activity inside a list.
- [MathJax Liquid Tags by Jessy Cowan-Sharp](https://gist.github.com/834610): Simple liquid tags for Jekyll that convert inline math and block equations to the appropriate MathJax script tags.
- [Non-JS Gist Tag by Brandon Tilley](https://gist.github.com/1027674) A Liquid tag that embeds Gists and shows code for non-JavaScript enabled browsers and readers.
- [Render Time Tag by Blake Smith](https://gist.github.com/449509): Displays the time a Jekyll page was generated.
- [Status.net/OStatus Tag by phaer](https://gist.github.com/912466): Displays the notices in a given status.net/ostatus feed.
- [Embed.ly client by Robert Böhnke](https://github.com/robb/jekyll-embedly-client): Autogenerate embeds from URLs using oEmbed.
- [Logarithmic Tag Cloud](https://gist.github.com/2290195): Flexible. Logarithmic distribution. Documentation inline.
- [oEmbed Tag by Tammo van Lessen](https://gist.github.com/1455726): Enables easy content embedding (e.g. from YouTube, Flickr, Slideshare) via oEmbed.
- [FlickrSetTag by Thomas Mango](https://github.com/tsmango/jekyll_flickr_set_tag): Generates image galleries from Flickr sets.
- [Tweet Tag by Scott W. Bradley](https://github.com/scottwb/jekyll-tweet-tag): Liquid tag for [Embedded Tweets](https://dev.twitter.com/docs/embedded-tweets) using Twitter’s shortcodes.
- [Jekyll Twitter Plugin](https://github.com/rob-murray/jekyll-twitter-plugin): A Liquid tag plugin that renders Tweets from Twitter API. Currently supports the [oEmbed](https://dev.twitter.com/rest/reference/get/statuses/oembed) API.
- [Jekyll-contentblocks](https://github.com/rustygeldmacher/jekyll-contentblocks): Lets you use Rails-like content_for tags in your templates, for passing content from your posts up to your layouts.
- [Generate YouTube Embed](https://gist.github.com/1805814) by [joelverhagen](https://github.com/joelverhagen): Jekyll plugin which allows you to embed a YouTube video in your page with the YouTube ID. Optionally specify width and height dimensions. Like “oEmbed Tag” but just for YouTube.
- [Jekyll-beastiepress](https://github.com/okeeblow/jekyll-beastiepress): FreeBSD utility tags for Jekyll sites.
- [Jsonball](https://gist.github.com/1895282): Reads json files and produces maps for use in Jekyll files.
- [Bibjekyll](https://github.com/pablooliveira/bibjekyll): Render BibTeX-formatted bibliographies/citations included in posts and pages using bibtex2html.
- [Jekyll-citation](https://github.com/archome/jekyll-citation): Render BibTeX-formatted bibliographies/citations included in posts and pages (pure Ruby).
- [Jekyll Dribbble Set Tag](https://github.com/ericdfields/Jekyll-Dribbble-Set-Tag): Builds Dribbble image galleries from any user.
- [Debbugs](https://gist.github.com/2218470): Allows posting links to Debian BTS easily.
- [Refheap_tag](https://github.com/aburdette/refheap_tag): Liquid tag that allows embedding pastes from [refheap](https://refheap.com).
- [Jekyll-devonly_tag](https://gist.github.com/2403522): A block tag for including markup only during development.
- [JekyllGalleryTag](https://github.com/redwallhp/JekyllGalleryTag) by [redwallhp](https://github.com/redwallhp): Generates thumbnails from a directory of images and displays them in a grid.
- [Youku and Tudou Embed](https://gist.github.com/Yexiaoxing/5891929): Liquid plugin for embedding Youku and Tudou videos.
- [Jekyll-swfobject](https://github.com/sectore/jekyll-swfobject): Liquid plugin for embedding Adobe Flash files (.swf) using [SWFObject](http://code.google.com/p/swfobject/).
- [Jekyll Picture Tag](https://github.com/robwierzbowski/jekyll-picture-tag): Easy responsive images for Jekyll. Based on the proposed [`<picture>`](http://picture.responsiveimages.org/) element, polyfilled with Scott Jehl’s [Picturefill](https://github.com/scottjehl/picturefill).
- [Jekyll Image Tag](https://github.com/robwierzbowski/jekyll-image-tag): Better images for Jekyll. Save image presets, generate resized images, and add classes, alt text, and other attributes.
- [Ditaa Tag](https://github.com/matze/jekyll-ditaa) by [matze](https://github.com/matze): Renders ASCII diagram art into PNG images and inserts a figure tag.
- [Jekyll Suggested Tweet](https://github.com/davidensinger/jekyll-suggested-tweet) by [David Ensinger](https://github.com/davidensinger/): A Liquid tag for Jekyll that allows for the embedding of suggested tweets via Twitter’s Web Intents API.
- [Jekyll Date Chart](https://github.com/GSI/jekyll_date_chart) by [GSI](https://github.com/GSI): Block that renders date line charts based on textile-formatted tables.
- [Jekyll Image Encode](https://github.com/GSI/jekyll_image_encode) by [GSI](https://github.com/GSI): Tag that renders base64 codes of images fetched from the web.
- [Jekyll Quick Man](https://github.com/GSI/jekyll_quick_man) by [GSI](https://github.com/GSI): Tag that renders pretty links to man page sources on the internet.
- [jekyll-font-awesome](https://gist.github.com/23maverick23/8532525): Quickly and easily add Font Awesome icons to your posts.
- [Lychee Gallery Tag](https://gist.github.com/tobru/9171700) by [tobru](https://github.com/tobru): Include [Lychee](http://lychee.electerious.com/) albums into a post. For an introduction, see [Jekyll meets Lychee - A Liquid Tag plugin](https://tobrunet.ch/articles/jekyll-meets-lychee-a-liquid-tag-plugin/)
- [Image Set/Gallery Tag](https://github.com/callmeed/jekyll-image-set) by [callmeed](https://github.com/callmeed): Renders HTML for an image gallery from a folder in your Jekyll site. Just pass it a folder name and class/tag options.
- [jekyll_figure](https://github.com/lmullen/jekyll_figure): Generate figures and captions with links to the figure in a variety of formats
- [Jekyll Github Sample Tag](https://github.com/bwillis/jekyll-github-sample): A liquid tag to include a sample of a github repo file in your Jekyll site.
- [Jekyll Project Version Tag](https://github.com/rob-murray/jekyll-version-plugin): A Liquid tag plugin that renders a version identifier for your Jekyll site sourced from the git repository containing your code.
- [Piwigo Gallery](https://github.com/AlessandroLorenzi/piwigo_gallery) by [Alessandro Lorenzi](http://www.alorenzi.eu/): Jekyll plugin to generate thumbnails from a Piwigo gallery and display them with a Liquid tag
- [mathml.rb](https://github.com/tmthrgd/jekyll-plugins) by [Tom Thorogood](http://tomthorogood.co.uk/): A plugin to convert TeX mathematics into MathML for display.
- [webmention_io.rb](https://github.com/aarongustafson/jekyll-webmention_io) by [Aaron Gustafson](http://aaron-gustafson.com/): A plugin to enable [webmention](http://indiewebcamp.com/webmention) integration using [Webmention.io](http://webmention.io). Includes an optional JavaScript for updating webmentions automatically between publishes and, if available, in realtime using WebSockets.
- [Jekyll 500px Embed](https://github.com/lkorth/jekyll-500px-embed) by [Luke Korth](https://lukekorth.com/). A Liquid tag plugin that embeds [500px](https://500px.com/) photos.
- [inline\_highlight](https://github.com/bdesham/inline_highlight): A tag for inline syntax highlighting.
- [jekyll-mermaid](https://github.com/jasonbellamy/jekyll-mermaid): Simplify the creation of mermaid diagrams and flowcharts in your posts and pages.

#### 콜렉션

- [Jekyll Plugins by Recursive Design](http://recursive-design.com/projects/jekyll-plugins/): Plugins to generate Project pages from GitHub readmes, a Category page, and a Sitemap generator.
- [Company website and blog plugins](https://github.com/flatterline/jekyll-plugins) by Flatterline, a [Ruby on Rails development company](http://flatterline.com/): Portfolio/project page generator, team/individual page generator, an author bio liquid tag for use on posts, and a few other smaller plugins.
- [Jekyll plugins by Aucor](https://github.com/aucor/jekyll-plugins): Plugins for trimming unwanted newlines/whitespace and sorting pages by weight attribute.

#### 기타

- [ditaa-ditaa](https://github.com/tmthrgd/ditaa-ditaa) by [Tom Thorogood](http://tomthorogood.co.uk/): a drastic revision of jekyll-ditaa that renders diagrams drawn using ASCII art into PNG images.
- [Pygments Cache Path by Raimonds Simanovskis](https://github.com/rsim/blog.rayapps.com/blob/master/_plugins/pygments_cache_patch.rb): Plugin to cache syntax-highlighted code from Pygments.
- [Draft/Publish Plugin by Michael Ivey](https://gist.github.com/49630): Save posts as drafts.
- [Growl Notification Generator by Tate Johnson](https://gist.github.com/490101): Send Jekyll notifications to Growl.
- [Growl Notification Hook by Tate Johnson](https://gist.github.com/525267): Better alternative to the above, but requires his “hook” fork.
- [Related Posts by Lawrence Woodman](https://github.com/LawrenceWoodman/related_posts-jekyll_plugin): Overrides `site.related_posts` to use categories to assess relationship.
- [Tiered Archives by Eli Naeher](https://gist.github.com/88cda643aa7e3b0ca1e5): Create tiered template variable that allows you to group archives by year and month.
- [Jekyll-localization](https://github.com/blackwinter/jekyll-localization): Jekyll plugin that adds localization features to the rendering engine.
- [Jekyll-rendering](https://github.com/blackwinter/jekyll-rendering): Jekyll plugin to provide alternative rendering engines.
- [Jekyll-pagination](https://github.com/blackwinter/jekyll-pagination): Jekyll plugin to extend the pagination generator.
- [Jekyll-tagging](https://github.com/pattex/jekyll-tagging): Jekyll plugin to automatically generate a tag cloud and tag pages.
- [Jekyll-scholar](https://github.com/inukshuk/jekyll-scholar): Jekyll extensions for the blogging scholar.
- [Jekyll-asset_bundler](https://github.com/moshen/jekyll-asset_bundler): Bundles and minifies JavaScript and CSS.
- [Jekyll-assets](http://ixti.net/jekyll-assets/) by [ixti](https://github.com/ixti): Rails-alike assets pipeline (write assets in CoffeeScript, Sass, LESS etc; specify dependencies for automatic bundling using simple declarative comments in assets; minify and compress; use JST templates; cache bust; and many-many more).
- [JAPR](https://github.com/kitsched/japr): Jekyll Asset Pipeline Reborn - Powerful asset pipeline for Jekyll that collects, converts and compresses JavaScript and CSS assets.
- [File compressor](https://gist.github.com/2758691) by [mytharcher](https://github.com/mytharcher): Compress HTML and JavaScript files on site build.
- [Jekyll-minibundle](https://github.com/tkareine/jekyll-minibundle): Asset bundling and cache busting using external minification tool of your choice. No gem dependencies.
- [Singlepage-jekyll](https://github.com/JCB-K/singlepage-jekyll) by [JCB-K](https://github.com/JCB-K): Turns Jekyll into a dynamic one-page website.
- [generator-jekyllrb](https://github.com/robwierzbowski/generator-jekyllrb): A generator that wraps Jekyll in [Yeoman](http://yeoman.io/), a tool collection and workflow for builing modern web apps.
- [grunt-jekyll](https://github.com/dannygarcia/grunt-jekyll): A straightforward [Grunt](http://gruntjs.com/) plugin for Jekyll.
- [jekyll-postfiles](https://github.com/indirect/jekyll-postfiles): Add `_postfiles` directory and {% raw %}`{{ postfile }}`{% endraw %} tag so the files a post refers to will always be right there inside your repo.
- [A layout that compresses HTML](https://github.com/penibelst/jekyll-compress-html) by [Anatol Broder](http://penibelst.de/): Github Pages compatible, configurable way to compress HTML files on site build.
- [Jekyll CO₂](https://github.com/wdenton/jekyll-co2): Generates HTML showing the monthly change in atmospheric CO₂ at the Mauna Loa observatory in Hawaii.
- [remote-include](http://www.northfieldx.co.uk/remote-include/): Includes files using remote URLs

#### 편집기

- [sublime-jekyll](https://github.com/23maverick23/sublime-jekyll): A Sublime Text package for Jekyll static sites. This package should help creating Jekyll sites and posts easier by providing access to key template tags and filters, as well as common completions and a current date/datetime command (for dating posts). You can install this package manually via GitHub, or via [Package Control](https://sublime.wbond.net/packages/Jekyll).
- [vim-jekyll](https://github.com/parkr/vim-jekyll): A vim plugin to generate
  new posts and run `jekyll build` all without leaving vim.
- [markdown-writer](https://atom.io/packages/markdown-writer): An Atom package for Jekyll. It can create new posts/drafts, manage tags/categories, insert link/images and add many useful key mappings.

<div class="note info">
  <h5>Jekyll 플러그인을 수배합니다</h5>
  <p>
    자신의 플러그인을 이 목록에 포함시키고 싶다면,
    <a href="../contributing/">기여하기 페이지를
    읽어보세요</a>.
  </p>
</div>
