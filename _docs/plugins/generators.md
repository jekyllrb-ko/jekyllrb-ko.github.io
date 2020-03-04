---
#title: Generators
title: 생성기
permalink: /docs/plugins/generators/
---

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
before the site is generated. Pages with front matter are stored as
instances of
[`Jekyll::Page`]({{ site.repository }}/blob/master/lib/jekyll/page.rb)
and are available via `site.pages`. Static files become instances of
[`Jekyll::StaticFile`]({{ site.repository }}/blob/master/lib/jekyll/static_file.rb)
and are available via `site.static_files`. See
[the Variables documentation page](/docs/variables/) and
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb)
for details.
-->
생성기는 Jekyll 이 컨텐츠 목록을 파악하고 난 후, 그리고 사이트가 생성되기 직전에
실행됩니다.
머리말을 가진 페이지들은
[`Jekyll::Page`]({{ site.repository }}/blob/master/lib/jekyll/page.rb)
인스턴스로 저장되어 `site.pages` 로 사용할 수 있습니다. 정적 파일들은
[`Jekyll::StaticFile`]({{ site.repository }}/blob/master/lib/jekyll/static_file.rb)
인스턴스가 되어 `site.static_files` 로 사용할 수 있습니다.
자세한 내용은 [변수 페이지](/docs/variables/)와
[`Jekyll::Site`]({{ site.repository }}/blob/master/lib/jekyll/site.rb) 를
살펴보세요.

<!--
For instance, a generator can inject values computed at build time for template
variables. In the following example, the template `reading.html` has two
variables `ongoing` and `done` that are filled in the generator:
-->
예를 들어, 생성기는 빌드 시점에 계산된 값을 템플릿 변수에 주입할 수 있습니다.
다음 예제에서, 템플릿 `reading.html` 의 두 변수 `ongoing` 과 `done` 의 값을
생성기에서 채우게 됩니다:

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
The following example is a more complex generator that generates new pages. In this example, the generator will create a series of files under the `categories` directory for each category, listing the posts in each category using the `category_index.html` layout.
-->
다음 예제는 좀 더 복잡한 생성기로서, 새 페이지를 생성합니다. 이 예제에서, 생성기는 `categories` 안에 각 카테고리 별로 파일을 생성하고, `category_index.html` 레이아웃을 사용하여 각 카테고리 별 포스트 목록을 만듭니다.

```ruby
module Jekyll
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

  # A Page subclass used in the `CategoryPageGenerator`
  class CategoryPage < Page
    def initialize(site, base, dir, category)
      @site = site
      @base = base
      @dir  = dir
      @name = 'index.html'

      self.process(@name)
      self.read_yaml(File.join(base, '_layouts'), 'category_index.html')
      self.data['category'] = category

      category_title_prefix = site.config['category_title_prefix'] || 'Category: '
      self.data['title'] = "#{category_title_prefix}#{category}"
    end
  end
end
```

<!--
Generators need to implement only one method:
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
        <p>컨텐츠를 생성한다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
If your generator is contained within a single file, it can be named whatever you want but it should have an `.rb` extension. If your generator is split across multiple files, it should be packaged as a Rubygem to be published at https://rubygems.org/. In this case, the name of the gem depends on the availability of the name at that site because no two gems can have the same name.
-->
당신이 만든 생성기가 파일 하나로 구성되어 있다면, 이름은 원하는대로 지을 수 있지만 확장자는 반드시 `.rb` 이어야 합니다. 만약 파일 여러개로 구성된 생성기라면, 루비젬 패키지로 만들어 https://rubygems.org/ 에 게시되어 있어야 합니다. 이 경우, 하나 이상의 젬이 같은 이름을 가질 수 없기 때문에 이에 맞춰 젬 이름을 결정해야 합니다.

<!--
By default, Jekyll looks for generators in the `_plugins` directory. However, you can change the default directory by assigning the desired name to the key `plugins_dir` in the config file.
-->
디폴트로, Jekyll 은 `_plugins` 디렉토리에서 생성기를 찾습니다. 하지만, 환경설정 파일의 `plugins_dir` 키에 원하는 디렉토리를 할당하여 디폴트 값을 변경할 수 있습니다.
