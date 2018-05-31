---
#title: Plugins
title: 플러그인
permalink: /docs/plugins/
---

<!--
Jekyll has a plugin system with hooks that allow you to create custom generated
content specific to your site. You can run custom code for your site without
having to modify the Jekyll source itself.
-->
Jekyll 은 Hook 을 제공하는 플러그인 시스템을 갖추고 있어서 자신의 사이트에 꼭
맞는 컨텐츠를 생성할 수 있습니다. 따라서, Jekyll 의 소스코드를 직접 수정하지
않고도 자신의 코드가 실행되게 할 수 있습니다.

<div class="note info">
<!--
  <h5>Plugins on GitHub Pages</h5>
  <p>
    <a href="https://pages.github.com/">GitHub Pages</a> is powered by Jekyll.
    However, all Pages sites are generated using the <code>--safe</code> option
    to disable custom plugins for security reasons. Unfortunately, this means
    your plugins won’t work if you’re deploying to GitHub Pages.<br><br>
    You can still use GitHub Pages to publish your site, but you’ll need to
    convert the site locally and push the generated static files to your GitHub
    repository instead of the Jekyll source files.
  </p>
-->
  <h5>GitHub Pages 와 플러그인</h5>
  <p>
    <a href="https://pages.github.com/">GitHub Pages</a> 는 Jekyll 을 사용합니다.
    하지만 보안상의 이유로 인해, 모든 Pages 사이트는 <code>--safe</code>
    옵션으로 사용자 플러그인이 비활성화된 상태에서 생성됩니다. 이 말은
    안타깝게도, GitHub Pages 에서는 당신의 플러그인을 사용할 수 없다는
    뜻입니다.<br><br>그래도 GitHub Pages 와 사용자 플러그인을 함께 사용하는
    방법이 있습니다. GitHub 에 소스를 직접 올리는 대신, 로컬 시스템에서 변환을
    먼저 한 후 생성된 파일을 올리면 됩니다.
  </p>
</div>

<!--
## Installing a plugin
-->
## 플러그인 설치하기

<!--
You have 3 options for installing plugins:
-->
플러그인을 설치하는 방법은 세 가지가 있습니다:

<!--
1. In your site source root, make a `_plugins` directory. Place your plugins
   here. Any file ending in `*.rb` inside this directory will be loaded before
   Jekyll generates your site.

2. In your `_config.yml` file, add a new array with the key `plugins` (or `gems` for Jekyll < `3.5.0`) and the
   values of the gem names of the plugins you'd like to use. An example:

   ```yaml
   # This will require each of these plugins automatically.
   plugins:
     - jekyll-gist
     - jekyll-coffeescript
     - jekyll-assets
     - another-jekyll-plugin
   ```

   Then install your plugins using `gem install jekyll-gist jekyll-coffeescript jekyll-assets another-jekyll-plugin`

3. Add the relevant plugins to a Bundler group in your `Gemfile`. An
   example:

   ```ruby
    group :jekyll_plugins do
      gem "jekyll-gist"
      gem "jekyll-coffeescript"
      gem "jekyll-assets"
      gem "another-jekyll-plugin"
    end
   ```

   Now you need to install all plugins from your Bundler group by running single command `bundle install`.
-->
1. Site Source 루트에 `_plugins` 디렉토리를 만드세요. 여기에 자신의 플러그인을
넣습니다. Jekyll 은 사이트를 생성하기 직전에 이 디렉토리의 모든 `*.rb` 파일을
읽어들입니다.

2. `_config.yml` 파일에 `plugins` (또는 `3.5.0` 버전 이전의 Jekyll 에서는 `gems`) 라는 키로 배열을 추가하고
   사용하려는 플러그인들의 gem 이름을 나열하세요. 예를 들면 다음과 같습니다:

   ```yaml
   # This will require each of these plugins automatically.
   plugins:
     - jekyll-gist
     - jekyll-coffeescript
     - jekyll-assets
     - another-jekyll-plugin
   ```

    그리고 다음 명령을 실행하여 해당 플러그인들을 설치합니다. `gem install jekyll-gist jekyll-coffeescript jekyll-assets another-jekyll-plugin`

3. 관련 플러그인을 `Gemfile` 의 Bundler 그룹에 추가합니다. 예를 들면 다음과
    같습니다:

   ```ruby
    group :jekyll_plugins do
      gem "jekyll-gist"
      gem "jekyll-coffeescript"
      gem "jekyll-assets"
      gem "another-jekyll-plugin"
    end
   ```

    이제 `bundle install` 명령만 한 번 실행해주면 Bundler 그룹에 있는 모든 플러그인이 설치됩니다.

<div class="note info">
<!--
  <h5>
    <code>_plugins</code>, <code>_config.yml</code> and <code>Gemfile</code>
    can be used simultaneously
  </h5>
  <p>
    You may use any of the aforementioned plugin options simultaneously in the
    same site if you so choose. Use of one does not restrict the use of the
    others.
  </p>
-->
  <h5>
    <code>_plugins</code> 와 <code>_config.yml</code>, <code>Gemfile</code> 은
    동시에 함께 사용할 수 있습니다
  </h5>
  <p>
    원한다면 앞서 언급한 플러그인 옵션들을 한 사이트에 동시에 사용할 수
    있습니다. 어떤 옵션을 사용한다고 해서 다른 옵션을 사용하는데에 제약이 생기는
    것은 아닙니다.
  </p>
</div>

<!--
### The jekyll_plugins group
-->
### jekyll_plugins 그룹

<!--
Jekyll gives this particular group of gems in your `Gemfile` a different
treatment. Any gem included in this group is loaded before Jekyll starts
processing the rest of your source directory.
-->
당신의 `Gemfile` 에 정의된 이 그룹은, 조금 다른 방식으로 처리됩니다.
Jekyll 은 작업을 시작하기 전에 먼저 이 그룹에 속해있는 gem 들을
불러들입니다.

<!--
A gem included here will be activated even if its not explicitly listed under
the `plugins:` key in your site's config file.
-->
심지어 사이트 환경설정 파일의 `plugins:` 키에 정의되어 있지 않더라도, 이
안에 있는 gem 들은 활성화됩니다.

<div class="note warning">
  <p>
<!--
    Gems included in the <code>:jekyll-plugins</code> group are activated
    regardless of the <code>--safe</code> mode setting. Be aware of what
    gems are included under this group!
-->
    그룹 <code>:jekyll-plugins</code> 에 포함되어 있는 gem 들은
    <code>--safe</code> 모드 설정에 관계없이 활성화됩니다. 어떤 gem 들을
    이 그룹에 포함시킬 것인지 주의를 기울이세요!
  </p>
</div>


<!--
In general, plugins you make will fall broadly into one of five categories:
-->
일반적으로, 플러그인은 크게 다섯 가지 카테고리 중 하나에 속하게 됩니다:

<!--
1. [Generators](#generators)
2. [Converters](#converters)
3. [Commands](#commands)
4. [Tags](#tags)
5. [Hooks](#hooks)
-->
1. [생성기](#generators)
2. [변환기](#converters)
3. [명령어](#commands)
4. [태그](#tags)
5. [훅](#hooks)

<!--
See the bottom of the page for a [list of available plugins](#available-plugins).
-->
이 페이지 뒷 부분에 [사용할 수 있는 플러그인 목록](#available-plugins)이 있습니다.

<!--
For further information on how to develop your own plugins, check out the [Liquid documentation](https://github.com/Shopify/liquid/wiki/Liquid-for-Programmers) as well.
-->
자신만의 플러그인을 개발하는 방법에 대한 더 자세한 내용이 필요하면, [Liquid 문서](https://github.com/Shopify/liquid/wiki/Liquid-for-Programmers)도 살펴보시기 바랍니다.

<!--
If you never developed a Jekyll plugin [check this useful wrap-up](https://ayastreb.me/writing-a-jekyll-plugin/) by @ayastreb to get started.
-->
Jekyll 플러그인 개발에 대해 @ayastreb 이 작성한 [요약본](https://ayastreb.me/writing-a-jekyll-plugin/)이 Jekyll 플러그인 개발 경험이 전혀 없는 분들에게 도움이 될 것입니다.

<!--
## Generators
-->
## 생성기

<!--
You can create a generator when you need Jekyll to create additional content
based on your own rules.
-->
생성기를 만들어 Jekyll 로 하여금 당신이 정한 규칙에 따라 부가적인 컨텐츠를
생성하도록 할 수 있습니다.

<!--
A generator is a subclass of `Jekyll::Generator` that defines a `generate`
method, which receives an instance of
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb). The
return value of `generate` is ignored.
-->
생성기는 `Jekyll::Generator` 의 하위 클래스로서,
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb)
인스턴스를 전달받는 `generate` 메소드 가지고 있습니다. `generate` 메소드의
리턴값은 무시됩니다.

<!--
Generators run after Jekyll has made an inventory of the existing content, and
before the site is generated. Pages with YAML Front Matters are stored as
instances of
[`Jekyll::Page`]({{ site.repository }}/blob/master/lib/jekyll/page.rb)
and are available via `site.pages`. Static files become instances of
[`Jekyll::StaticFile`]({{ site.repository }}/blob/master/lib/jekyll/static_file.rb)
and are available via `site.static_files`. See
[the Variables documentation page](/docs/variables/) and
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb)
for more details.
-->
생성기는 Jekyll 이 컨텐츠 목록을 파악하고 난 후, 그리고 사이트가 생성되기 직전에
실행됩니다.
YAML 머리말을 가진 페이지들은
[`Jekyll::Page`]({{ site.repository }}/blob/master/lib/jekyll/page.rb)
인스턴스로 저장되어 `site.pages` 로 사용할 수 있습니다. 정적 파일들은
[`Jekyll::StaticFile`]({{ site.repository }}/blob/master/lib/jekyll/static_file.rb)
인스턴스가 되어 `site.static_files` 로 사용할 수 있습니다.
더 자세한 내용은 [변수 문서 페이지](/docs/variables/)와
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb) 를
살펴보세요.

<!--
For instance, a generator can inject values computed at build time for template
variables. In the following example the template `reading.html` has two
variables `ongoing` and `done` that we fill in the generator:
-->
예를 들어, 생성기는 빌드 시점에 계산된 값을 템플릿 변수에 주입할 수 있습니다.
다음 예제 생성기는 `reading.html` 템플릿의 두 변수 `ongoing` 과 `done` 에 값을
채워 넣습니다:

```ruby
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
```

<!--
This is a more complex generator that generates new pages:
-->
다음은 좀 더 복잡한 생성기로서, 새 페이지를 생성합니다:

```ruby
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
```

<!--
In this example, our generator will create a series of files under the
`categories` directory for each category, listing the posts in each category
using the `category_index.html` layout.
-->
이 생성기는 `categories` 안에 각 카테고리 별로 파일을 생성하고,
`category_index.html` 레이아웃을 사용하여 각 카테고리 별 포스트 목록을
만듭니다.

<!--
Generators are only required to implement one method:
-->
생성기가 필수로 구현해야 할 메소드는 딱 하나입니다:

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
        <p><code>generate</code></p>
      </td>
      <td>
<!--
        <p>Generates content as a side-effect.</p>
-->
        <p>컨텐츠를 생성합니다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Converters
-->
## 변환기

<!--
If you have a new markup language you’d like to use with your site, you can
include it by implementing your own converter. Both the Markdown and
[Textile](https://github.com/jekyll/jekyll-textile-converter) markup
languages are implemented using this method.
-->
당신의 사이트에 사용하고자 하는 다른 마크업 언어가 있다면, 해당 언어를 처리할 수
있는 변환기를 직접 구현하면 됩니다. 마크업 언어 Markdown 과
[Textile](https://github.com/jekyll/jekyll-textile-converter) 도 이
메소드를 사용해서 구현한 것입니다.

<div class="note info">
<!--
  <h5>Remember your YAML Front Matter</h5>
  <p>
    Jekyll will only convert files that have a YAML header at the top, even for
    converters you add using a plugin.
  </p>
-->
  <h5>YAML 머리말을 잊지 마세요</h5>
  <p>
    Jekyll 은 오직 YAML 머리말로 시작하는 파일만 변환합니다. 변환기 플러그인을
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
        있는가? 전달인자가 하나 필요합니다: 파일의 확장자 (점 포함). 포함되어
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
        of the file (without YAML Front Matter). Must return a String.
      </p></td>
-->
      <td><p>
        컨텐츠를 변환하는 로직. 전달인자가 하나 필요합니다: 변환되지 않은 파일
        내용 (YAML 머리말 제외). 반드시 문자열을 반환해야 합니다.
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
위 예제에서는, `UpcaseConverter#matches` 는 확장자가 `.upcase` 인지 확인하고,
만약 그렇다면 내용을 변환하기 위해 `UpcaseConverter#convert` 를 호출합니다.
이 예제에서 변환기는 단순히 전체 내용을 대문자로 변환합니다.
마지막으로, 변환된 내용을 페이지로 저장할 때 `.html` 확장자를 사용합니다.


<!--
## Commands
-->
## 명령어

<!--
As of version 2.5.0, Jekyll can be extended with plugins which provide
subcommands for the `jekyll` executable. This is possible by including the
relevant plugins in a `Gemfile` group called `:jekyll_plugins`:
-->
버전 2.5.0 부터, Jekyll 은 `jekyll` 실행파일에 하위명령어를 추가로 제공하는
플러그인들로 확장될 수 있습니다. `Gemfile` 의 `:jekyll_plugins` 라는 그룹에 관련
플러그인을 추가하면 됩니다:

```ruby
group :jekyll_plugins do
  gem "my_fancy_jekyll_plugin"
end
```

<!--
Each `Command` must be a subclass of the `Jekyll::Command` class and must
contain one class method: `init_with_program`. An example:
-->
각 `명령어` 는 반드시 `Jekyll::Command` 클래스의 하위 클래스이어야 하고
`init_with_program` 이라는 하나의 클래스 메소드를 가져야 합니다. 예를 들면 다음과 같습니다:

```ruby
class MyNewCommand < Jekyll::Command
  class << self
    def init_with_program(prog)
      prog.command(:new) do |c|
        c.syntax "new [options]"
        c.description 'Create a new Jekyll site.'

        c.option 'dest', '-d DEST', 'Where the site should go.'

        c.action do |args, options|
          Jekyll::Site.new_site_at(options['dest'])
        end
      end
    end
  end
end
```

<!--
Commands should implement this single class method:
-->
명령어는 반드시 이 클래스 메소드를 구현해야 합니다:

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
        <p><code>init_with_program</code></p>
      </td>
<!--
      <td><p>
        This method accepts one parameter, the
        <code><a href="https://github.com/jekyll/mercenary#readme">Mercenary::Program</a></code>
        instance, which is the Jekyll program itself. Upon the program,
        commands may be created using the above syntax. For more details,
        visit the Mercenary repository on GitHub.com.
      </p></td>
-->
      <td><p>
        이 메소드의 파라메터는 단 하나,
        <code><a href="https://github.com/jekyll/mercenary#readme">Mercenary::Program</a></code>
        인스턴스인데 이는 바로 Jekyll 프로그램 그 자체입니다. 프로그램에 따라,
        명령어는 위 문법을 사용해서 생성될 것입니다. 더 자세한 내용은,
        GitHub.com 의 Mercenary 저장소를 방문하세요.
      </p></td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Tags
-->
## 태그

<!--
If you’d like to include custom liquid tags in your site, you can do so by
hooking into the tagging system. Built-in examples added by Jekyll include the
`highlight` and `include` tags. Below is an example of a custom liquid tag that
will output the time the page was rendered:
-->
사이트에 자신의 Liquid 태그를 사용하고 싶다면,
태그 시스템의 Hook 을 사용하면 됩니다.
Jekyll 에 내장된 `highlight` 와 `include` 가 바로 그 예입니다.
다음 예제는 페이지가 생성된 시간을 출력해주는 Liquid 태그입니다:

```ruby
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
```

<!--
At a minimum, liquid tags must implement:
-->
Liquid 태그는 최소한 다음 메소드는 구현해야 합니다:

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
        <p><code>render</code></p>
      </td>
      <td>
<!--
        <p>Outputs the content of the tag.</p>
-->
        <p>태그 컨텐츠를 출력합니다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
You must also register the custom tag with the Liquid template engine as
follows:
-->
그리고 다음과 같이 Liquid 템플릿 엔진에 태그를 등록해야
합니다:

```ruby
Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTag)
```

<!--
In the example above, we can place the following tag anywhere in one of our
pages:
-->
이렇게 하면, 페이지의 어느 곳에서나 다음과 같이 태그를 사용할 수
있습니다:

{% raw %}
```ruby
<p>{% render_time page rendered at: %}</p>
```
{% endraw %}

<!--
And we would get something like this on the page:
-->
그러면 다음과 같은 결과를 얻을 수 있습니다:

```html
<p>page rendered at: Tue June 22 23:38:47 –0500 2010</p>
```

<!--
### Liquid filters
-->
### Liquid 필터

<!--
You can add your own filters to the Liquid template system much like you can
add tags above. Filters are simply modules that export their methods to liquid.
All methods will have to take at least one parameter which represents the input
of the filter. The return value will be the output of the filter.
-->
Liquid 템플릿 시스템에 필터를 추가하는 것은 위에 설명한 태그 추가 방법과 상당히
유사합니다. 필터는 단지 자신의 메소드를 Liquid 로 보내는 모듈일 뿐입니다. 모든
메소드에는 최소한 하나의 매개변수가 있어야 하며, 이것은 바로 필터의 입력입니다.
반환 값이 필터의 출력이 됩니다.

```ruby
module Jekyll
  module AssetFilter
    def asset_url(input)
      "http://www.example.com/#{input}?#{Time.now.to_i}"
    end
  end
end

Liquid::Template.register_filter(Jekyll::AssetFilter)
```

<div class="note">
<!--
  <h5>ProTip™: Access the site object using Liquid</h5>
  <p>
    Jekyll lets you access the <code>site</code> object through the
    <code>context.registers</code> feature of Liquid at <code>context.registers[:site]</code>. For example, you can
    access the global configuration file <code>_config.yml</code> using
    <code>context.registers[:site].config</code>.
  </p>
-->
  <h5>ProTip™: Liquid 를 사용해서 site 객체에 접근할 수 있습니다</h5>
  <p>
    Jekyll 은 <code>context.registers[:site]</code> 와 같이 Liquid 의
    <code>context.registers</code> 기능을 통해서 <code>site</code> 객체에 접근할
    수 있게 해줍니다. 예를 들어, <code>context.registers[:site].config</code>
    라고 입력하여 전역 환경설정 파일 <code>_config.yml</code> 에 접근할 수 있습니다.
  </p>
</div>

<!--
### Flags
-->
### 플래그

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
          실행될 수 있다는 것을 알려주는 boolean 플래그이다. GitHub Pages 는
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

<!--
## Hooks
-->
## Hook

<!--
Using hooks, your plugin can exercise fine-grained control over various aspects
of the build process. If your plugin defines any hooks, Jekyll will call them
at pre-defined points.
-->
Hook 을 사용하면, 당신의 플러그인이 사이트 빌드에 다방면으로 정교한 작업을
수행할 수 있습니다. 당신의 플러그인에 Hook 이 포함되어 있으면, Jekyll 은 정해진
시점에 해당 Hook 을 호출합니다.

<!--
Hooks are registered to a container and an event name. To register one, you
call Jekyll::Hooks.register, and pass the container, event name, and code to
call whenever the hook is triggered. For example, if you want to execute some
custom functionality every time Jekyll renders a post, you could register a
hook like this:
-->
Hook 은 이벤트 이름과 컨테이너에 등록됩니다. 등록하는 방법은,
Jekyll::Hooks.register 를 호출하고 컨테이너, 이벤트 이름과 Hook 이 실행될 때
호출할 코드를 연결하는 것입니다. 예를 들어, Jekyll 이 포스트를 생성할 때마다
특정 코드를 실행하도록 하려면, 다음과 같이 Hook 을 등록하면 됩니다:

```ruby
Jekyll::Hooks.register :posts, :post_render do |post|
  # code to call after Jekyll renders a post
end
```

<!--
Jekyll provides hooks for <code>:site</code>, <code>:pages</code>,
<code>:posts</code>, and <code>:documents</code>. In all cases, Jekyll calls your
hooks with the container object as the first callback parameter. But in the
case of <code>:pre_render</code>, your hook will also receive a payload hash as
a second parameter which allows you full control over the variables that are
available while rendering.
-->
Jekyll 은 <code>:site</code>, <code>:pages</code>, <code>:posts</code> 와
<code>:documents</code> 에 관련된 Hook 을 제공합니다. 어떤 상황에서든, Jekyll 은
Hook 을 호출하며 첫 번째 매개변수로 컨테이너 객체를 넘겨줍니다. 하지만
<code>:pre_render</code> 의 경우에는 두 번째 매개변수로 페이로드 해시도
제공하는데, 이로 인해 렌더링 중 사용할 수 있는 변수들에 대해 완벽한 관리 권한을
얻을 수 있습니다.

<!--
The complete list of available hooks is below:
-->
사용 가능한 Hook 들의 전체 목록은 다음과 같습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Container</th>
      <th>Event</th>
      <th>Called</th>
-->
      <th>컨테이너</th>
      <th>이벤트</th>
      <th>호출 시점</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:after_init</code></p>
      </td>
      <td>
<!--
        <p>Just after the site initializes, but before setup & render. Good
        for modifying the configuration of the site.</p>
-->
        <p>사이트 초기화 직후, 환경설정과 렌더링 작업 전. 사이트 환경설정을
        조정하기에 적절한 시점이다.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:after_reset</code></p>
      </td>
      <td>
<!--
        <p>Just after site reset</p>
-->
        <p>사이트가 초기화된 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_read</code></p>
      </td>
      <td>
<!--
        <p>After site data has been read and loaded from disk</p>
-->
        <p>디스크로부터 사이트 데이터를 읽어들인 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering the whole site</p>
-->
        <p>전체 사이트를 렌더링하기 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering the whole site, but before writing any files</p>
-->
        <p>전체 사이트를 렌더링한 직후 (파일 생성 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing the whole site to disk</p>
-->
        <p>전체 사이트 파일을 디스크에 생성한 직후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a page is initialized</p>
-->
        <p>페이지가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a page</p>
-->
        <p>페이지 렌더링 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a page, but before writing it to disk</p>
-->
        <p>페이지 렌더링 직후 (디스크에 생성 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a page to disk</p>
-->
        <p>페이지를 디스크에 생성한 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a post is initialized</p>
-->
        <p>포스트가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a post</p>
-->
        <p>포스트를 렌더링하기 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a post, but before writing it to disk</p>
-->
        <p>포스트 렌더링 후 (디스크에 쓰기 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a post to disk</p>
-->
        <p>포스트를 디스크에 생성한 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a document is initialized</p>
-->
        <p>문서가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a document</p>
-->
        <p>문서 렌더링 직후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a document, but before writing it to disk</p>
-->
        <p>문서를 렌더링한 후 (디스크에 쓰기 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a document to disk</p>
-->
        <p>문서를 디스크에 생성한 후</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Available Plugins
-->
## 사용가능한 플러그인

<!--
You can find a few useful plugins at the following locations:
-->
유용한 플러그인들을 모아두었습니다:

<!--
#### Generators
-->
#### 생성기

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
- [Typescript Generator by Matt Sheehan](https://github.com/sheehamj13/jekyll_ts): Generate Javascript on build from your Typescript.
- [Jekyll::AutolinkEmail by Ivan Tse](https://github.com/ivantsepp/jekyll-autolink_email): Autolink your emails.
- [Jekyll::GitMetadata by Ivan Tse](https://github.com/ivantsepp/jekyll-git_metadata): Expose Git metadata for your templates.
- [Jekyll Auto Image by Merlos](https://github.com/merlos/jekyll-auto-image): Gets the first image of a post. Useful to list your posts with images or to add [twitter cards](https://dev.twitter.com/cards/overview) to your site.
- [Jekyll Portfolio Generator by Shannon Babincsak](https://github.com/codeinpink/jekyll-portfolio-generator): Generates project pages and computes related projects out of project data files.
- [Jekyll-Umlauts by Arne Gockeln](https://github.com/webchef/jekyll-umlauts): This generator replaces all german umlauts (äöüß) case sensitive with html.
- [Jekyll Flickr Plugin](https://github.com/lawmurray/indii-jekyll-flickr) by [Lawrence Murray](http://www.indii.org): Generates posts for photos uploaded to a Flickr photostream.
- [Jekyll::Paginate::Category](https://github.com/midnightSuyama/jekyll-paginate-category): Pagination Generator for Jekyll Category.
- [AMP-Jekyll by Juuso Mikkonen](https://github.com/juusaw/amp-jekyll): Generate [Accelerated Mobile Pages](https://www.ampproject.org) of Jekyll posts.
- [Jekyll Art Gallery plugin](https://github.com/alexivkin/Jekyll-Art-Gallery-Plugin): An advanced art/photo gallery generation plugin for creating galleries from a set of image folders. Supports image tagging, thumbnails, sorting, image rotation, post-processing (remove EXIF, add watermark), multiple collections and much more.
- [jekyll-ga](https://github.com/developmentseed/jekyll-ga): A Jekyll plugin that downloads Google Analytics data and adds it to posts. Useful for making a site that lists "most popular" content. [Read the introduction](https://developmentseed.org/blog/google-analytics-jekyll-plugin/) post on the developmentSEED blog.
- [jekyll-multi-paginate](https://github.com/fadhilnapis/jekyll-multi-paginate): Simple Jekyll paginator for multiple page. Ease you to make pagination on multiple page especially like multiple language.
- [jekyll-category-pages](https://github.com/field-theory/jekyll-category-pages): Easy-to-use category index pages with and without pagination. Supports non-URL-safe category keywords and has extensive documentation and test coverage.
- [Tweetsert](https://github.com/ibrado/jekyll-tweetsert): Imports tweets (Twitter statuses) as new posts. Features multiple timeline support, hashtag import, filtering, automatic category and/or tags, optional retweets and replies.
- [Stickyposts](https://github.com/ibrado/jekyll-stickyposts): Moves or copies (pins) posts marked `sticky: true` to the top of the list. Perfect for keeping important announcements on the home page, or giving collections a descriptive entry. Paginator friendly.
- [Jekyll::Paginate::Content](https://github.com/ibrado/jekyll-paginate-content): Content paginator in the style of jekyll-paginator-v2 that splits pages, posts, and collection entries into several pages. Specify a separator or use HTML &lt;h1&gt; etc. headers. Automatic splitting, single-page view, pager/trail, self-adjusting links, multipage TOC, SEO support.
- [Premonition](https://github.com/amedia/premonition): Adds block-styled side content to your page. For example summary, notes, hints or warning boxes.
- [jekyll-fontello](https://github.com/ericcornelissen/jekyll-fontello): A Jekyll plugin that automatically downloads your webfont from Fontello.

<!--
#### Converters
-->
#### 변환기

- [Pug plugin by Doug Beney](http://jekyll-pug.dougie.io): Use the popular Pug (previously Jade) templating language in Jekyll. Complete with caching, includes support, and much more.
- [Textile converter](https://github.com/jekyll/jekyll-textile-converter): Convert `.textile` files into HTML. Also includes the `textilize` Liquid filter.
- [Slim plugin](https://github.com/slim-template/jekyll-slim): Slim converter and includes for Jekyll with support for Liquid tags.
- [Markdown References by Olov Lassus](https://github.com/olov/jekyll-references): Keep all your markdown reference-style link definitions in one \_references.md file.
- [ReStructuredText Converter](https://github.com/xdissent/jekyll-rst): Converts ReST documents to HTML with Pygments syntax highlighting.
- [Jekyll-pandoc-multiple-formats](https://github.com/fauno/jekyll-pandoc-multiple-formats) by [edsl](https://github.com/edsl): Use pandoc to generate your site in multiple formats. Supports pandoc’s markdown extensions.
- [Customized Kramdown Converter](https://github.com/mvdbos/kramdown-with-pygments): Enable Pygments syntax highlighting for Kramdown-parsed fenced code blocks.
- [Bigfootnotes Plugin](https://github.com/TheFox/jekyll-bigfootnotes): Enables big footnotes for Kramdown.
- [AsciiDoc Plugin](https://github.com/asciidoctor/jekyll-asciidoc): AsciiDoc convertor for Jekyll using [Asciidoctor](http://asciidoctor.org/).
- [Lazy Tweet Embedding](https://github.com/takuti/jekyll-lazy-tweet-embedding): Automatically convert tweet urls into twitter cards.
- [jekyll-commonmark](https://github.com/pathawks/jekyll-commonmark): Markdown converter that uses [libcmark](https://github.com/jgm/CommonMark), the reference parser for CommonMark.

<!--
#### Filters
-->
#### 필터

- [Truncate HTML](https://github.com/MattHall/truncatehtml) by [Matt Hall](https://codebeef.com/): A Jekyll filter that truncates HTML while preserving markup structure.
- [Domain Name Filter by Lawrence Woodman](https://github.com/LawrenceWoodman/domain_name-liquid_filter): Filters the input text so that just the domain name is left.
- [Smilify](https://github.com/SaswatPadhi/jekyll_smilify) by [SaswatPadhi](https://github.com/SaswatPadhi): Convert text emoticons in your content to themeable smiley pics.
- [Jekyll-timeago](https://github.com/markets/jekyll-timeago): Converts a time value to the time ago in words.
- [pluralize](https://github.com/bdesham/pluralize): Easily combine a number and a word into a grammatically-correct amount like “1 minute” or “2 minute**s**”.
- [reading_time](https://github.com/bdesham/reading_time): Count words and estimate reading time for a piece of text, ignoring HTML elements that are unlikely to contain running text.
- [Table of Content Generator](https://github.com/dafi/jekyll-toc-generator): Generate the HTML code containing a table of content (TOC), the TOC can be customized in many way, for example you can decide which pages can be without TOC.
- [jekyll-toc](https://github.com/toshimaru/jekyll-toc): A liquid filter plugin for Jekyll which generates a table of contents.
- [jekyll-humanize](https://github.com/23maverick23/jekyll-humanize): This is a port of the Django app humanize which adds a "human touch" to data. Each method represents a Fluid type filter that can be used in your Jekyll site templates. Given that Jekyll produces static sites, some of the original methods do not make logical sense to port (e.g. naturaltime).
- [Jekyll-Ordinal](https://github.com/PatrickC8t/Jekyll-Ordinal): Jekyll liquid filter to output a date ordinal such as "st", "nd", "rd", or "th".
- [Deprecated articles keeper](https://github.com/kzykbys/JekyllPlugins) by [Kazuya Kobayashi](http://blog.kazuya.co/): A simple Jekyll filter which monitor how old an article is.
- [Jekyll-jalali](https://github.com/mehdisadeghi/jekyll-jalali) by [Mehdi Sadeghi](http://mehdix.ir): A simple Gregorian to Jalali date converter filter.
- [Jekyll Thumbnail Filter](https://github.com/matallo/jekyll-thumbnail-filter): Related posts thumbnail filter.
- [liquid-md5](https://github.com/pathawks/liquid-md5): Returns an MD5 hash. Helpful for generating Gravatars in templates.
- [jekyll-roman](https://github.com/paulrobertlloyd/jekyll-roman): A liquid filter for Jekyll that converts numbers into Roman numerals.
- [jekyll-typogrify](https://github.com/myles/jekyll-typogrify): A Jekyll plugin that brings the functions of [typogruby](http://avdgaag.github.io/typogruby/).
- [Jekyll Email Protect](https://github.com/vwochnik/jekyll-email-protect): Email protection liquid filter for Jekyll
- [Jekyll Uglify Filter](https://github.com/mattg/jekyll-uglify-filter): A Liquid filter that runs your JavaScript through UglifyJS.
- [match_regex](https://github.com/sparanoid/match_regex): A Liquid filter to perform regex match.
- [replace_regex](https://github.com/sparanoid/replace_regex): A Liquid filter to perform regex replace.
- [Jekyll Money](https://rubygems.org/gems/jekyll-money): A Jekyll plugin for dealing with money. Because we all have to at some point.
- [jekyll-random](https://github.com/codecalm/jekyll-random) by [codecalm](https://nodecalm.net): A Jekyll plugin that generates pseudo-random data. Very useful when you want to generate a large amount of random data.

<!--
#### Tags
-->
#### 태그

You can find a few useful plugins at the following locations:

- [Jekyll-gist](https://github.com/jekyll/jekyll-gist): Use the `gist` tag to easily embed a GitHub Gist onto your site. This works with public or secret gists.
- [Asset Path Tag](https://github.com/samrayner/jekyll-asset-path-plugin) by [Sam Rayner](http://www.samrayner.com/): Allows organisation of assets into subdirectories by outputting a path for a given file relative to the current post or page.
- [Delicious Plugin by Christian Hellsten](https://github.com/christianhellsten/jekyll-plugins): Fetches and renders bookmarks from delicious.com.
- [Embed.ly client by Robert Böhnke](https://github.com/robb/jekyll-embedly-client): Autogenerate embeds from URLs using oEmbed.
- [FlickrSetTag by Thomas Mango](https://github.com/tsmango/jekyll_flickr_set_tag): Generates image galleries from Flickr sets.
- [Tweet Tag by Scott W. Bradley](https://github.com/scottwb/jekyll-tweet-tag): Liquid tag for [Embedded Tweets](https://dev.twitter.com/docs/embedded-tweets) using Twitter’s shortcodes.
- [Jekyll Twitter Plugin](https://github.com/rob-murray/jekyll-twitter-plugin): A Liquid tag plugin that renders Tweets from Twitter API. Currently supports the [oEmbed](https://dev.twitter.com/rest/reference/get/statuses/oembed) API.
- [Jekyll-contentblocks](https://github.com/rustygeldmacher/jekyll-contentblocks): Lets you use Rails-like content_for tags in your templates, for passing content from your posts up to your layouts.
- [Jekyll-beastiepress](https://github.com/okeeblow/jekyll-beastiepress): FreeBSD utility tags for Jekyll sites.
- [Bibjekyll](https://github.com/pablooliveira/bibjekyll): Render BibTeX-formatted bibliographies/citations included in posts and pages using bibtex2html.
- [Jekyll-citation](https://github.com/archome/jekyll-citation): Render BibTeX-formatted bibliographies/citations included in posts and pages (pure Ruby).
- [Jekyll Dribbble Set Tag](https://github.com/ericdfields/Jekyll-Dribbble-Set-Tag): Builds Dribbble image galleries from any user.
- [JekyllGalleryTag](https://github.com/redwallhp/JekyllGalleryTag) by [redwallhp](https://github.com/redwallhp): Generates thumbnails from a directory of images and displays them in a grid.
- [Jekyll-swfobject](https://github.com/sectore/jekyll-swfobject): Liquid plugin for embedding Adobe Flash files (.swf) using [SWFObject](https://github.com/swfobject/swfobject).
- [Jekyll Picture Tag](https://github.com/robwierzbowski/jekyll-picture-tag): Easy responsive images for Jekyll. Based on the proposed [`<picture>`](https://html.spec.whatwg.org/multipage/embedded-content.html#the-picture-element) element, polyfilled with Scott Jehl’s [Picturefill](https://github.com/scottjehl/picturefill).
- [Jekyll Image Tag](https://github.com/robwierzbowski/jekyll-image-tag): Better images for Jekyll. Save image presets, generate resized images, and add classes, alt text, and other attributes.
- [Jekyll Responsive Image](https://github.com/wildlyinaccurate/jekyll-responsive-image): Responsive images for Jekyll. Automatically resizes images, supports all responsive methods (`<picture>`, `srcset`, Imager.js, etc), super-flexible configuration.
- [Ditaa Tag](https://github.com/matze/jekyll-ditaa) by [matze](https://github.com/matze): Renders ASCII diagram art into PNG images and inserts a figure tag.
- [Jekyll Suggested Tweet](https://github.com/davidensinger/jekyll-suggested-tweet) by [David Ensinger](https://github.com/davidensinger/): A Liquid tag for Jekyll that allows for the embedding of suggested tweets via Twitter’s Web Intents API.
- [Jekyll Date Chart](https://github.com/GSI/jekyll_date_chart) by [GSI](https://github.com/GSI): Block that renders date line charts based on textile-formatted tables.
- [Jekyll Image Encode](https://github.com/GSI/jekyll_image_encode) by [GSI](https://github.com/GSI): Tag that renders base64 codes of images fetched from the web.
- [Jekyll Quick Man](https://github.com/GSI/jekyll_quick_man) by [GSI](https://github.com/GSI): Tag that renders pretty links to man page sources on the internet.
- [Image Set/Gallery Tag](https://github.com/callmeed/jekyll-image-set) by [callmeed](https://github.com/callmeed): Renders HTML for an image gallery from a folder in your Jekyll site. Just pass it a folder name and class/tag options.
- [jekyll_figure](https://github.com/lmullen/jekyll_figure): Generate figures and captions with links to the figure in a variety of formats
- [Jekyll GitHub Sample Tag](https://github.com/bwillis/jekyll-github-sample): A liquid tag to include a sample of a github repo file in your Jekyll site.
- [Jekyll Project Version Tag](https://github.com/rob-murray/jekyll-version-plugin): A Liquid tag plugin that renders a version identifier for your Jekyll site sourced from the git repository containing your code.
- [Piwigo Gallery](https://github.com/AlessandroLorenzi/piwigo_gallery) by [Alessandro Lorenzi](http://blog.alorenzi.eu/): Jekyll plugin to generate thumbnails from a Piwigo gallery and display them with a Liquid tag
- [mathml.rb](https://github.com/tmthrgd/jekyll-plugins) by Tom Thorogood: A plugin to convert TeX mathematics into MathML for display.
- [webmention_io.rb](https://github.com/aarongustafson/jekyll-webmention_io) by [Aaron Gustafson](http://aaron-gustafson.com/): A plugin to enable [webmention](https://indieweb.org/webmention) integration using [Webmention.io](https://webmention.io/). Includes an optional JavaScript for updating webmentions automatically between publishes and, if available, in realtime using WebSockets.
- [Jekyll 500px Embed](https://github.com/lkorth/jekyll-500px-embed) by Luke Korth. A Liquid tag plugin that embeds [500px](https://500px.com/) photos.
- [inline\_highlight](https://github.com/bdesham/inline_highlight): A tag for inline syntax highlighting.
- [jekyll-mermaid](https://github.com/jasonbellamy/jekyll-mermaid): Simplify the creation of mermaid diagrams and flowcharts in your posts and pages.
- [twa](https://github.com/Ezmyrelda/twa): Twemoji Awesome plugin for Jekyll. Liquid tag allowing you to use twitter emoji in your jekyll pages.
- [Fetch remote file content](https://github.com/dimitri-koenig/jekyll-plugins) by [Dimitri König](https://www.dimitrikoenig.net/): Using `remote_file_content` tag you can fetch the content of a remote file and include it as if you would put the content right into your markdown file yourself. Very useful for including code from github repo's to always have a current repo version.
- [jekyll-asciinema](https://github.com/mnuessler/jekyll-asciinema): A tag for embedding asciicasts recorded with [asciinema](https://asciinema.org) in your Jekyll pages.
- [Jekyll-Youtube](https://github.com/dommmel/jekyll-youtube)  A Liquid tag that embeds Youtube videos. The default emded markup is responsive but you can also specify your own by using an include/partial.
- [Jekyll Flickr Plugin](https://github.com/lawmurray/indii-jekyll-flickr) by [Lawrence Murray](http://www.indii.org): Embeds Flickr photosets (albums) as a gallery of thumbnails, with lightbox links to larger images.
- [jekyll-figure](https://github.com/paulrobertlloyd/jekyll-figure): A liquid tag for Jekyll that generates `<figure>` elements.
- [Jekyll Video Embed](https://github.com/eug/jekyll-video-embed): It provides several tags to easily embed videos (e.g. Youtube, Vimeo, UStream and Ted Talks)
- [jekyll-i18n_tags](https://github.com/KrzysiekJ/jekyll-i18n_tags): Translate your templates.
- [Jekyll Ideal Image Slider](https://github.com/jekylltools/jekyll-ideal-image-slider): Liquid tag plugin to create image sliders using [Ideal Image Slider](https://github.com/gilbitron/Ideal-Image-Slider).
- [Jekyll Tags List Plugin](https://github.com/crispgm/jekyll-tags-list-plugin): A Liquid tag plugin that creates tags list in specific order.
- [Jekyll Maps](https://github.com/ayastreb/jekyll-maps) by [Anatoliy Yastreb](https://github.com/ayastreb): A Jekyll plugin to easily embed maps with filterable locations.
- [Jekyll Cloudinary](https://nhoizey.github.io/jekyll-cloudinary/) by [Nicolas Hoizey](https://nicolas-hoizey.com/): a Jekyll plugin adding a Liquid tag to ease the use of Cloudinary for responsive images in your Markdown/Kramdown posts.
- [jekyll-include-absolute-plugin](https://github.com/tnhu/jekyll-include-absolute-plugin) by [Tan Nhu](https://github.com/tnhu): A Jekyll plugin to include a file from its path relative to Jekyll's source folder.
- [Jekyll Download Tag](https://github.com/mattg/jekyll-download-tag): A Liquid tag that acts like `include`, but for external resources.
- [Jekyll Brand Social Wall](https://github.com/MediaComem/jekyll-brand-social-wall): A jekyll plugin to generate a social wall with your favorite social networks
- [Jekyll If File Exists](https://github.com/k-funk/jekyll-if-file-exists): A Jekyll Plugin that checks if a file exists with an if/else block.
- [BibSonomy](https://github.com/rjoberon/bibsonomy-jekyll): Jekyll
  plugin to generate publication lists from [BibSonomy](https://www.bibsonomy.org/).
- [github-cards](https://github.com/edward-shen/github-cards): Creates styleable Github cards for your Github projects.
- [disqus-for-jekyll](https://github.com/kacperduras/disqus-for-jekyll): A Jekyll plugin to view the comments powered by Disqus.
- [jekyll-html](https://github.com/kacperduras/jekyll-html): A Jekyll plugin to use HTML tags in Jekyll pages, posts and collections.
- [jekyll-onebox](https://github.com/rriemann/jekyll-onebox): Liquid tag for displaying HTML previews (embeds) for links to popular domains. Plugin is based on [Onebox](https://github.com/discourse/onebox) that powers link previews in [Discourse](http://github.com/discourse/discourse) forums.
- [jekyll-w2m](https://github.com/kacperduras/jekyll-w2m): A Jekyll plugin to liberate content from Microsoft Word documents (powered by [word-to-markdown](https://github.com/benbalter/word-to-markdown)).
- [jekyll-flickr](https://github.com/rriemann/jekyll-flickr): Liquid tag for responsive Flickr images using HTML5 srcset. Subtitles and automatic license notices are supported.

<!--
#### Collections
-->
#### 콜렉션

- [Jekyll Plugins by Recursive Design](https://github.com/recurser/jekyll-plugins): Plugins to generate Project pages from GitHub readmes, a Category page, and a Sitemap generator.
- [Company website and blog plugins](https://github.com/flatterline/jekyll-plugins) by Flatterline, a Ruby on Rails development company: Portfolio/project page generator, team/individual page generator, an author bio liquid tag for use on posts, and a few other smaller plugins.
- [Jekyll plugins by Aucor](https://github.com/aucor/jekyll-plugins): Plugins for trimming unwanted newlines/whitespace and sorting pages by weight attribute.

<!--
#### Other
-->
#### 기타

- [Analytics for Jekyll](https://github.com/hendrikschneider/jekyll-analytics) by Hendrik Schneider: An effortless way to add various trackers like Google Analytics, Matomo (formerly Piwik), mPulse, etc. to your site.
- [ditaa-ditaa](https://github.com/tmthrgd/ditaa-ditaa) by Tom Thorogood: a drastic revision of jekyll-ditaa that renders diagrams drawn using ASCII art into PNG images.
- [Pygments Cache Path by Raimonds Simanovskis](https://github.com/rsim/blog.rayapps.com/blob/master/_plugins/pygments_cache_patch.rb): Plugin to cache syntax-highlighted code from Pygments.
- [Related Posts by Lawrence Woodman](https://github.com/LawrenceWoodman/related_posts-jekyll_plugin): Overrides `site.related_posts` to use categories to assess relationship.
- [jekyll-tagging-related_posts](https://github.com/toshimaru/jekyll-tagging-related_posts): Jekyll related_posts function based on tags (works on Jekyll3).
- [Jekyll-localization](https://github.com/blackwinter/jekyll-localization): Jekyll plugin that adds localization features to the rendering engine.
- [Jekyll-rendering](https://github.com/blackwinter/jekyll-rendering): Jekyll plugin to provide alternative rendering engines.
- [Jekyll-pagination](https://github.com/blackwinter/jekyll-pagination): Jekyll plugin to extend the pagination generator.
- [Jekyll-tagging](https://github.com/pattex/jekyll-tagging): Jekyll plugin to automatically generate a tag cloud and tag pages.
- [Jekyll-scholar](https://github.com/inukshuk/jekyll-scholar): Jekyll extensions for the blogging scholar.
- [Jekyll-assets](http://jekyll.github.io/jekyll-assets/) by [ixti](https://github.com/ixti): Rails-alike assets pipeline (write assets in CoffeeScript, Sass, LESS etc; specify dependencies for automatic bundling using simple declarative comments in assets; minify and compress; use JST templates; cache bust; and many-many more).
- [JAPR](https://github.com/kitsched/japr): Jekyll Asset Pipeline Reborn - Powerful asset pipeline for Jekyll that collects, converts and compresses JavaScript and CSS assets.
- [Jekyll-minibundle](https://github.com/tkareine/jekyll-minibundle): Asset bundling and cache busting using external minification tool of your choice. No gem dependencies.
- [Singlepage-jekyll](https://github.com/JCB-K/singlepage-jekyll) by [JCB-K](https://github.com/JCB-K): Turns Jekyll into a dynamic one-page website.
- [generator-jekyllrb](https://github.com/robwierzbowski/generator-jekyllrb): A generator that wraps Jekyll in [Yeoman](http://yeoman.io/), a tool collection and workflow for building modern web apps.
- [grunt-jekyll](https://github.com/dannygarcia/grunt-jekyll): A straightforward [Grunt](http://gruntjs.com/) plugin for Jekyll.
- [jekyll-postfiles](https://github.com/indirect/jekyll-postfiles): Add `_postfiles` directory and {% raw %}`{{ postfile }}`{% endraw %} tag so the files a post refers to will always be right there inside your repo.
- [A layout that compresses HTML](http://jch.penibelst.de/): GitHub Pages compatible, configurable way to compress HTML files on site build.
- [Jekyll CO₂](https://github.com/wdenton/jekyll-co2): Generates HTML showing the monthly change in atmospheric CO₂ at the Mauna Loa observatory in Hawaii.
- [remote-include](http://www.northfieldx.co.uk/remote-include/): Includes files using remote URLs
- [jekyll-minifier](https://github.com/digitalsparky/jekyll-minifier): Minifies HTML, XML, CSS, and Javascript both inline and as separate files utilising yui-compressor and htmlcompressor.
- [Jekyll views router](https://bitbucket.org/nyufac/jekyll-views-router): Simple router between generator plugins and templates.
- [Jekyll Language Plugin](https://github.com/vwochnik/jekyll-language-plugin): Jekyll 3.0-compatible multi-language plugin for posts, pages and includes.
- [Jekyll Deploy](https://github.com/vwochnik/jekyll-deploy): Adds a `deploy` sub-command to Jekyll.
- [Official Contentful Jekyll Plugin](https://github.com/contentful/jekyll-contentful-data-import): Adds a `contentful` sub-command to Jekyll to import data from Contentful.
- [jekyll-paspagon](https://github.com/KrzysiekJ/jekyll-paspagon): Sell your posts in various formats for cryptocurrencies.
- [Hawkins](https://github.com/awood/hawkins): Adds a `liveserve` sub-command to Jekyll that incorporates [LiveReload](http://livereload.com/) into your pages while you preview them.  No more hitting the refresh button in your browser!
- [Jekyll Autoprefixer](https://github.com/vwochnik/jekyll-autoprefixer): Autoprefixer integration for Jekyll
- [Jekyll-breadcrumbs](https://github.com/git-no/jekyll-breadcrumbs): Creates breadcrumbs for Jekyll 3.x, includes features like SEO optimization, optional breadcrumb item translation and more.
- [generator-jekyllized](https://github.com/sondr3/generator-jekyllized): A Yeoman generator for rapidly developing sites with Gulp. Live reload your site, automatically minify and optimize your assets and much more.
- [Jekyll-Spotify](https://github.com/MertcanGokgoz/Jekyll-Spotify): Easily output Spotify Embed Player for jekyll
- [jekyll-menus](https://github.com/forestryio/jekyll-menus): Hugo style menus for your Jekyll site... recursive menus included.
- [jekyll-data](https://github.com/ashmaroli/jekyll-data): Read data files within Jekyll Theme Gems.
- [jekyll-pinboard](https://github.com/snaptortoise/jekyll-pinboard-plugin): Access your Pinboard bookmarks within your Jekyll theme.
- [jekyll-migrate-permalink](https://github.com/mpchadwick/jekyll-migrate-permalink): Adds a `migrate-permalink` sub-command to help deal with side effects of changing your permalink.
- [Jekyll-Post](https://github.com/robcrocombe/jekyll-post): A CLI tool to easily draft, edit, and publish Jekyll posts.
- [jekyll-numbered-headings](https://github.com/muratayusuke/jekyll-numbered-headings): Adds ordered number to headings.
- [jekyll-pre-commit](https://github.com/mpchadwick/jekyll-pre-commit): A framework for running checks against your posts using a git pre-commit hook before you publish them.
- [jekyll-pwa-plugin](https://github.com/lavas-project/jekyll-pwa): A plugin provides PWA support for Jekyll. It generates a service worker in Jekyll build process and makes precache and runtime cache available in the runtime with Google Workbox.
- [jekyll-algolia](https://community.algolia.com/jekyll-algolia/): Add fast and relevant search to your Jekyll site through the Algolia API.

<div class="note info">
<!--
  <h5>Submit your gem plugins</h5>
  <p>
    You're encouraged to add your Jekyll gem plugins to this list, <a href="../contributing/">read the contributing page</a> to find
    out how to make that happen.
  </p>
-->
  <h5>플러그인을 보내주세요</h5>
  <p>
    이 목록에 포함시키고자 하는 자신만의 Jekyll 플러그인을 가지고 있다면, <a href="../contributing/">기여하기 페이지를
    읽어보세요</a>.
  </p>
</div>
