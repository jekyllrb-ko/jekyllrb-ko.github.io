---
#title: Themes
title: 테마
permalink: /docs/themes/
---

<!--
Jekyll has an extensive theme system that allows you to leverage community-maintained templates and styles to customize your site's presentation. Jekyll themes specify plugins and package up assets, layouts, includes, and stylesheets in a way that can be overridden by your site's content.
-->
Jekyll 의 테마 시스템은 확장성이 뛰어나서 공개 프로젝트 템플릿과 스타일을 활용하여 사이트의 외관을 꾸밀 수 있습니다. Jekyll 테마는 몇 가지 플러그인과 레이아웃, 조각파일, 스타일시트, 기타 자원들을 하나로 묶은 일종의 패키지이며, 그 안에 사이트의 컨텐츠를 집어넣을 수 있습니다.

<!--
## Understanding gem-based themes
-->
## 루비 젬 기반 테마 이해하기

<!--
When you [create a new Jekyll site](/docs/quickstart) (by running the `jekyll new <PATH>` command), Jekyll installs a site that uses a gem-based theme called [Minima](https://github.com/jekyll/minima).
-->
당신이 [새 Jekyll 사이트를 생성](/docs/quickstart)하면 (`jekyll new <PATH>` 명령을 사용), Jekyll 은 [Minima](https://github.com/jekyll/minima) 라고 하는 루비 젬 기반 테마가 적용된 사이트를 생성합니다.

<!--
With gem-based themes, some of the site's directories (such as the `assets`, `_layouts`, `_includes`, and `_sass` directories) are stored in the theme's gem, hidden from your immediate view. Yet all of the necessary directories will be read and processed during Jekyll's build process.
-->
루비 젬 기반 테마로, 사이트의 몇몇 (`assets` 와 `_layouts`, `_includes`, `_sass` 와 같은) 디렉토리들은 테마 젬 안에 저장되어 있어, 실제로 볼 수 없습니다. 그래도 Jekyll 은 빌드작업에 필요한 모든 디렉토리를 읽고 처리합니다.

<!--
In the case of Minima, you see only the following files in your Jekyll site directory:
-->
Minima 의 경우에, 당신의 Jekyll 디렉토리에서 볼 수 있는 파일은 다음과 같습니다:

```
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2016-12-04-welcome-to-jekyll.markdown
├── about.md
└── index.md
```

<!--
The `Gemfile` and `Gemfile.lock` files are used by Bundler to keep track of the required gems and gem versions you need to build your Jekyll site.
-->
`Gemfile` 과 `Gemfile.lock` 은 Bundler 관련 파일로서, 당신의 Jekyll 사이트를 빌드하기 위해 필요한 루비 젬과 그 버전을 기록하는데 사용합니다.

<!--
Gem-based themes make it easy for theme developers to make updates available to anyone who has the theme gem. When there's an update, theme developers push the update to RubyGems.
-->
루비 젬 기반 테마는 테마 개발자로 하여금 해당 테마 젬 사용자들에게 쉽게 업데이트를 제공할 수 있게 해줍니다.

<!--
If you have the theme gem, you can (if you desire) run `bundle update` to update all gems in your project. Or you can run `bundle update <THEME>`, replacing `<THEME>` with the theme name, such as `minima`, to just update the theme gem. Any new files or updates the theme developer has made (such as to stylesheets or includes) will be pulled into your project automatically.
-->
테마 젬을 사용중인 경우, 당신은 (원한다면) `bundle update` 를 실행해서 당신의 프로젝트에 있는 모든 젬을 업데이트할 수 있습니다. 또는 `bundle update <THEME>` 로, `<THEME>` 에 테마 이름을 넣어서, 예를 들면 `minima`, 특정 테마 젬만 업데이트할 수 있습니다.

<!--
The goal of gem-based themes is to allow you to get all the benefits of a robust, continually updated theme without having all the theme's files getting in your way and over-complicating what might be your primary focus: creating content.
-->
루비 젬 기반 테마의 목적은 지속적으로 업데이트되는 강력한 테마의 모든 장점을 제공하는 것과 동시에, 테마의 여러 파일들로 인해 필요 이상으로 복잡해지는 것을 방지하여 당신이 해야하는 일에 집중할 수 있게 하는 것입니다: 컨텐츠 작성말이죠.

<!--
## Overriding theme defaults
-->
## 테마 기본값 덮어쓰기

<!--
Jekyll themes set default layouts, includes, and stylesheets. However, you can override any of the theme defaults with your own site content.
-->
Jekyll 테마에는 레이아웃과 조각파일, 스타일시트의 기본값이 설정되어 있습니다. 그러나, 당신이 작성한 내용으로 테마의 어떤 기본값이든 덮어쓸 수 있습니다.

<!--
To replace layouts or includes in your theme, make a copy in your `_layouts` or `_includes` directory of the specific file you wish to modify, or create the file from scratch giving it the same name as the file you wish to override.
-->
사용중인 테마의 레이아웃이나 조각파일을 변경하려면, `_layouts` 이나 `_includes` 디렉토리를 복사하여 그 안의 원하는 파일을 수정하거나, 완전히 파일을 새로 만들어 덮어쓰려는 파일의 이름과 동일하게 저장하면 됩니다.

<!--
For example, if your selected theme has a `page` layout, you can override the theme's layout by creating your own `page` layout in the `_layouts` directory (that is, `_layouts/page.html`).
-->
예를 들어, 사용하는 테마에 `page` 라는 레이아웃이 있을 경우, `_layouts` 디렉토리에 `page` 레이아웃 (다시 말해, `_layouts/page.html`) 을 생성 하여 테마의 레이아웃을 덮어쓸 수 있습니다.

<!--
To locate a theme's files on your computer:
-->
자신의 컴퓨터에서 테마파일의 위치를 찾으려면:

<!--
1. Run `bundle show` followed by the name of the theme's gem, e.g., `bundle show minima` for Jekyll's default theme.

   This returns the location of the gem-based theme files. For example, the Minima theme's files might be located in `/usr/local/lib/ruby/gems/2.3.0/gems/minima-2.1.0` on macOS.

2. Open the theme's directory in Finder or Explorer:

   ```sh
   # On MacOS
   open $(bundle show minima)
   # On Windows
   explorer /usr/local/lib/ruby/gems/2.3.0/gems/minima-2.1.0
   ```

   A Finder or Explorer window opens showing the theme's files and directories. The Minima theme gem contains these files:

    ```
    ├── LICENSE.txt
    ├── README.md
    ├── _includes
    │   ├── disqus_comments.html
    │   ├── footer.html
    │   ├── google-analytics.html
    │   ├── head.html
    │   ├── header.html
    │   ├── icon-github.html
    │   ├── icon-github.svg
    │   ├── icon-twitter.html
    │   └── icon-twitter.svg
    ├── _layouts
    │   ├── default.html
    │   ├── home.html
    │   ├── page.html
    │   └── post.html
    ├── _sass
    │   ├── minima
    │   │   ├── _base.scss
    │   │   ├── _layout.scss
    │   │   └── _syntax-highlighting.scss
    │   └── minima.scss
    └── assets
        └── main.scss
     ```
-->
1. 테마의 젬 이름과 함께 `bundle show` 를 실행합니다. 예, Jekyll 기본 테마의 경우 `bundle show minima`.

   이 명령은 루비 젬 기반 테마 파일의 위치를 보여줍니다. 예를 들어, 맥OS 에서 Minima 테마 파일의 위치는 `/usr/local/lib/ruby/gems/2.3.0/gems/minima-2.1.0` 입니다.

2. Finder 나 탐색기로 테마 디렉토리를 엽니다:

   ```sh
   # 맥OS 일 경우
   open $(bundle show minima)
   # 윈도우즈일 경우
   explorer /usr/local/lib/ruby/gems/2.3.0/gems/minima-2.1.0
   ```

   Finder 나 익스플로러 창이 열려 테마의 파일과 디렉토리를 보여줍니다. Minima 테마 젬에는 다음 파일들이 포함되어 있습니다:

    ```
    ├── LICENSE.txt
    ├── README.md
    ├── _includes
    │   ├── disqus_comments.html
    │   ├── footer.html
    │   ├── google-analytics.html
    │   ├── head.html
    │   ├── header.html
    │   ├── icon-github.html
    │   ├── icon-github.svg
    │   ├── icon-twitter.html
    │   └── icon-twitter.svg
    ├── _layouts
    │   ├── default.html
    │   ├── home.html
    │   ├── page.html
    │   └── post.html
    ├── _sass
    │   ├── minima
    │   │   ├── _base.scss
    │   │   ├── _layout.scss
    │   │   └── _syntax-highlighting.scss
    │   └── minima.scss
    └── assets
        └── main.scss
     ```

<!--
With a clear understanding of the theme's files, you can now override any theme file by creating a similarly named file in your Jekyll site directory.
-->
테마 파일에 대하여 완전히 이해했다면, 어떤 테마 파일이든지 당신의 Jekyll 사이트 디렉토리 안에 비슷한 이름으로 파일을 생성하여 덮어쓸 수 있습니다.

<!--
Let's say, for a second example, you want to override Minima's footer. In your Jekyll site, create an `_includes` folder and add a file in it called `footer.html`. Jekyll will now use your site's `footer.html` file instead of the `footer.html` file from the Minima theme gem.
-->
또 다른 예로, Minima 의 푸터를 덮어쓰는 경우를 생각해 봅시다. Jekyll 사이트에, `_includes` 폴더를 만들고 그 안에 `footer.html` 이라는 파일을 저장합니다. 이제부터 Jekyll 은 Minima 테마 젬의 `footer.html` 대신 사이트에 들어있는 `footer.html` 파일을 사용할 것 입니다.

<!--
To modify any stylesheet you must take the extra step of also copying the main sass file (`_sass/minima.scss` in the Minima theme) into the `_sass` directory in your site's source.
-->
스타일시트를 수정하려는 경우에는 추가로 필요한 작업이 있는데, 메인 SASS 파일 (Minima 테마에서는 `_sass/minima.scss`) 을 Site Source 의 `_sass` 로 복사해야 합니다.

<!--
Jekyll will look first to your site's content before looking to the theme's defaults for any requested file in the following folders:
-->
Jekyll 은 아래 폴더에 있는 테마의 기본 파일들을 확인하기 전에 사이트의 컨텐츠를 먼저 확인합니다:

- `/assets`
- `/_layouts`
- `/_includes`
- `/_sass`

<!--
Note that making copies of theme files will prevent you from receiving any theme updates on those files. An alternative, to continue getting theme updates on all stylesheets, is to use higher specificity CSS selectors in your own additional, originally named CSS files.
-->
테마 파일의 복사본을 만든 경우 해당 파일에 대해서는 테마의 업데이트가 적용되지 않는다는 것을 기억하세요. 이에 관한 대안으로, 스타일시트에 관련된 테마 업데이트는 유지하고자 한다면, 직접 만든 CSS 파일을 고유한 이름으로 추가하고, 명시도가 높은 CSS 셀렉터를 사용하세요.

<!--
Refer to your selected theme's documentation and source repository for more information on what files you can override.
-->
사용중인 테마의 설명서나 소스 저장소를 참고하여 덮어쓸 수 있는 파일에 관한 더 많은 정보를 얻을 수 있습니다.
{: .note .info}

<!--
## Converting gem-based themes to regular themes
-->
## 루비 젬 기반 테마를 일반 테마로 변환하기

<!--
Suppose you want to get rid of the gem-based theme and convert it to a regular theme, where all files are present in your Jekyll site directory, with nothing stored in the theme gem.
-->
루비 젬 기반 테마를 없애고, 모든 파일이 테마의 젬 내부가 아닌, 당신의 Jekyll 사이트 디렉토리에 있는 일반 테마로 변환하려 한다고 가정해봅시다.

<!--
To do this, copy the files from the theme gem's directory into your Jekyll site directory. (For example, copy them to `/myblog` if you created your Jekyll site at `/myblog`. See the previous section for details.)
-->
그러기 위해서는, 테마 젬 디렉토리 안에 있는 모든 파일을 당신의 Jekyll 사이트 디렉토리에 복사하세요. (예, 당신의 Jekyll 사이트가 `/myblog` 에 있다면 모든 파일을 이 `/myblog` 에 복사합니다. 자세한 내용은 이전 섹션을 참고하세요.)

<!--
Then you must tell Jekyll about the plugins that were referenced by the theme. You can find these plugins in the theme's gemspec file as runtime dependencies. If you were converting the Minima theme, for example, you might see:
-->
그 다음 테마가 참조하고 있던 플러그인들을 Jekyll 에 알려주어야 합니다. 이 플러그인들은 테마 gemspec 파일의 런타임 종속성 (Runtime Dependency) 을 보면 알 수 있습니다. Minima 테마로부터 변환하는 상황을 예로 들어보면, 다음과 같은 내용이 있을 것입니다:

```
spec.add_runtime_dependency "jekyll-feed", "~> 0.9"
spec.add_runtime_dependency "jekyll-seo-tag", "~> 2.1"
```

<!--
You should include these references in the `Gemfile` in one of two ways.
-->
이 참조 내용을 `Gemfile` 에 추가해야 하는데, 두 가지 방법이 있습니다.

<!--
You could list them individually in both `Gemfile` and `_config.yml`.
-->
이것들을 개별적으로 `Gemfile` 과 `_config.yml` 모두에 나열합니다.

```ruby
# ./Gemfile

gem "jekyll-feed", "~> 0.9"
gem "jekyll-seo-tag", "~> 2.1"
```

```yaml
# ./_config.yml

plugins:
  - jekyll-feed
  - jekyll-seo-tag
```

<!--
Or you could list them explicitly as Jekyll plugins in your Gemfile, and not update `_config.yml`, like this:
-->
아니면 `_config.yml` 은 수정하지 않고, `Gemfile` 에 Jekyll 플러그인으로서 명시적으로 나열합니다. 이렇게요:

```ruby
# ./Gemfile

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.9"
  gem "jekyll-seo-tag", "~> 2.1"
end
```

<!--
Either way, don't forget to `bundle update`.
-->
어떤 방법이든지, `bundle update` 하는 것을 잊지 마세요.

<!--
However, if you're publishing on GitHub Pages you should update only your `_config.yml` as GitHub Pages doesn't load plugins via Bundler.
-->
하지만, GitHub Pages 는 Bundler 로 플러그인을 불러오지 않기 때문에 GitHub Pages 에 게시하는 경우에는 오직 `_config.yml` 만 수정해야 합니다.

<!--
Finally, remove references to the theme gem in `Gemfile` and configuration. For example, to remove `minima`:
-->
마지막으로, 환경설정 파일과 `Gemfile` 에서 테마 젬에 대한 참조를 제거합니다. 예를 들어, `minima` 를 제거하려면:

<!--
- Open `Gemfile` and remove `gem "minima", "~> 2.0"`.
- Open `_config.yml` and remove `theme: minima`.
-->
- `Gemfile` 을 열고 `gem "minima", "~> 2.0"` 를 제거합니다.
- `_config.yml` 을 열고 `theme: minima` 를 제거합니다.

<!--
Now `bundle update` will no longer get updates for the theme gem.
-->
이제 `bundle update` 명령은 테마 젬에 대한 업데이트를 수행하지 않습니다.

<!--
## Installing a gem-based theme {#installing-a-theme}
-->
## 루비 젬 기반 테마 설치하기 {#installing-a-theme}

<!--
The `jekyll new <PATH>` command isn't the only way to create a new Jekyll site with a gem-based theme. You can also find gem-based themes online and incorporate them into your Jekyll project.
-->
루비 젬 기반 테마를 사용하는 Jekyll 사이트를 만드는 방법은 `jekyll new <PATH>` 말고도 또 있습니다. 온라인 상에서 찾은 루비 젬 기반 테마를 당신의 Jekyll 프로젝트에 적용할 수 있습니다.

<!--
For example, search for [jekyll theme on RubyGems](https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme) to find other gem-based themes. (Note that not all themes are using `jekyll-theme` as a convention in the theme name.)
-->
예를 들어, [jekyll theme on RubyGems](https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme) 라고 검색하여 다른 루비 젬 기반 테마들을 찾을 수 있습니다. (이름에 `jekyll-theme` 을 포함하는 관례를 따르지 않는 테마도 있다는 것을 알아두세요.)

<!--
To install a gem-based theme:
-->
루비 젬 기반 테마를 설치하려면:

<!--
1. Add the theme to your site's `Gemfile`:

   ```ruby
   # ./Gemfile

   gem "jekyll-theme-awesome"
   ```
  Or if you've started with the `jekyll new` command, replace `gem "minima", "~> 2.0"` with your theme-gem:

   ```diff
   # ./Gemfile

   - gem "minima", "~> 2.0"
   + gem "jekyll-theme-awesome"
   ```

2. Install the theme:

   ```sh
   bundle install
   ```

3. Add the following to your site's `_config.yml` to activate the theme:

   ```yaml
   theme: jekyll-theme-awesome
   ```

4. Build your site:

   ```sh
   bundle exec jekyll serve
   ```
-->
1. 사이트의 `Gemfile` 에 테마를 추가합니다:

   ```ruby
   # ./Gemfile

   gem "jekyll-theme-awesome"
   ```
  아니면 처음에 `jekyll new` 명령으로 생성한 경우에는, `gem "minima", "~> 2.0"` 를 원하는 테마 젬으로 변경합니다:

   ```diff
   # ./Gemfile

   - gem "minima", "~> 2.0"
   + gem "jekyll-theme-awesome"
   ```

2. 테마를 설치합니다:

   ```sh
   bundle install
   ```

3. 다음 내용을 사이트의 `_config.yml` 에 추가하여 테마를 활성화합니다:

   ```yaml
   theme: jekyll-theme-awesome
   ```

4. 사이트를 빌드합니다:

   ```sh
   bundle exec jekyll serve
   ```

<!--
You can have multiple themes listed in your site's `Gemfile`, but only one theme can be selected in your site's `_config.yml`.
-->
여러 개의 테마를 `Gemfile` 에 나열할 수 있지만, `_config.yml` 파일에서 선택할 수 있는 테마는 오직 하나뿐입니다.
{: .note .info }

<!--
If you're publishing your Jekyll site on [GitHub Pages](https://pages.github.com/), note that GitHub Pages supports only some gem-based themes. See [Supported Themes](https://pages.github.com/themes/) in GitHub's documentation to see which themes are supported.
-->
당신의 사이트를 [GitHub Pages](https://pages.github.com/) 에 게시하는 경우, 모든 루비 젬 기반 테마가 지원되는건 아니라는 것을 알아두세요. GitHub 문서 중 [Supported Themes](https://pages.github.com/themes/) 를 보면 어떤 테마를 지원하는지 알 수 있습니다.

<!--
## Creating a gem-based theme
-->
## 루비 젬 기반 테마 만들기

<!--
If you're a Jekyll theme developer (rather than just a consumer of themes), you can package up your theme in RubyGems and allow users to install it through Bundler.
-->
당신이 만약 (단순히 테마를 사용하는 것이 아닌) Jekyll 테마 개발자라면, 자신의 테마를 RubyGems 로 패키지화 하여 다른 사용자들이 Bundler 로 설치할 수 있게 만들 수 있습니다.

<!--
If you're unfamiliar with creating Ruby gems, don't worry. Jekyll will help you scaffold a new theme with the `new-theme` command. Run `jekyll new-theme` with the theme name as an argument.
-->
루비 젬을 만드는 것에 익숙하지 않더라도, 걱정하지 마세요. Jekyll 의 `new-theme` 명령이 새 테마의 뼈대를 만드는 것을 도와줄 것입니다. `jekyll new-theme` 명령에 테마 이름을 인수로 전달해 실행하세요.

<!--
Here is an example:
-->
여기 예제가 하나 있습니다:

```sh
jekyll new-theme jekyll-theme-awesome
    create /path/to/jekyll-theme-awesome/_layouts
    create /path/to/jekyll-theme-awesome/_includes
    create /path/to/jekyll-theme-awesome/_sass
    create /path/to/jekyll-theme-awesome/_layouts/page.html
    create /path/to/jekyll-theme-awesome/_layouts/post.html
    create /path/to/jekyll-theme-awesome/_layouts/default.html
    create /path/to/jekyll-theme-awesome/Gemfile
    create /path/to/jekyll-theme-awesome/jekyll-theme-awesome.gemspec
    create /path/to/jekyll-theme-awesome/README.md
    create /path/to/jekyll-theme-awesome/LICENSE.txt
    initialize /path/to/jekyll-theme-awesome/.git
    create /path/to/jekyll-theme-awesome/.gitignore
Your new Jekyll theme, jekyll-theme-awesome, is ready for you in /path/to/jekyll-theme-awesome!
For help getting started, read /path/to/jekyll-theme-awesome/README.md.
```

<!--
Add your template files in the corresponding folders. Then complete the `.gemspec` and the README files according to your needs.
-->
관련된 폴더에 당신의 템플릿 파일을 추가하세요. 그 다음 `.gemspec` 과 README 파일을 작성하세요.

<!--
### Layouts and includes
-->
### 레이아웃과 조각파일

<!--
Theme layouts and includes work just like they work in any Jekyll site. Place layouts in your theme's `/_layouts` folder, and place includes in your themes `/_includes` folder.
-->
테마의 레이아웃과 조각파일은 사이트에 있는 것과 동일한 방식으로 동작합니다. 레이아웃은 테마의 `/_layouts` 폴더에, 조각파일은 테마의 `/_includes` 폴더에 저장하세요.

<!--
For example, if your theme has a `/_layouts/page.html` file, and a page has `layout: page` in its YAML front matter, Jekyll will first look to the site's `_layouts` folder for the `page` layout, and if none exists, will use your theme's `page` layout.
-->
예를 들어, 당신의 테마에 `/_layouts/page.html` 파일이 있고, YAML 머리말에 `layout: page` 가 적힌 페이지가 있다면, Jekyll 은 먼저 사이트의 `_layouts` 폴더에서 `page` 레이아웃을 찾아보고, 만약 없다면, 테마에 들어있는 `page` 레이아웃을 사용할 것입니다.

<!--
### Assets
-->
### 자원

<!--
Any file in `/assets` will be copied over to the user's site upon build unless they have a file with the same relative path. You can ship any kind of asset here: SCSS, an image, a webfont, etc. These files behave like pages and static files in Jekyll:
-->
동일한 상대경로를 가진 파일이 없다면 `/assets` 에 있는 모든 파일은 빌드 시 사용자의 사이트에 복사될 것입니다. 여기에 보관할 수 있는 자원의 종류는 제한이 없습니다: SCSS, 이미지, 웹 폰트, 등등. 이 파일들은 Jekyll 의 페이지나 정적 파일과 동일하게 동작합니다:

<!--
- If the file has [YAML front matter](/docs/frontmatter/) at the top, it will be rendered.
- If the file does not have YAML front matter, it will simply be copied over into the resulting site.
-->
- 파일의 첫 부분에 [YAML 머리말](/docs/frontmatter/)이 있다면, 렌더링 과정을 거칩니다.
- 파일에 YAML 머리말이 없다면, Site Destination 으로 단순 복사됩니다.

<!--
This allows theme creators to ship a default `/assets/styles.scss` file which their layouts can depend on as `/assets/styles.css`.
-->
이 덕분에 테마 제작자는 기본 `/assets/styles.scss` 파일을 제공할 수 있어 레이아웃들에 `/assets/styles.css` 를 적용할 수 있습니다.

<!--
All files in `/assets` will be output into the compiled site in the `/assets` folder just as you'd expect from using Jekyll on your sites.
-->
당신이 알고 있는 Jekyll 의 사용방식과 동일하게, `/assets` 안의 모든 파일은 생성된 사이트의 `/assets` 폴더에 출력될 것입니다.

<!--
### Stylesheets
-->
### 스타일시트

<!--
Your theme's stylesheets should be placed in your theme's `_sass` folder, again, just as you would when authoring a Jekyll site.
-->
반복되는 이야기지만, 당신이 알고 있는 Jekyll 의 사용방식과 동일하게, 테마의 스타일시트는 테마의 `_sass` 폴더에 저장해야 합니다.

```
_sass
├── jekyll-theme-awesome.scss
```

<!--
Your theme's styles can be included in the user's stylesheet using the `@import` directive.
-->
사용자의 스타일시트에 `@import` 지시어를 사용해서 테마에 들어있는 스타일을 포함시킬 수 있습니다.

{% raw %}
```css
@import "{{ site.theme }}";
```
{% endraw %}

<!--
### Theme-gem dependencies {%- include docs_version_badge.html version="3.5.0" -%}
-->
### 테마 젬 종속성 {%- include docs_version_badge.html version="3.5.0" -%}

<!--
Jekyll will automatically require all whitelisted `runtime_dependencies` of your theme-gem even if they're not explicitly included under the `plugins` array in the site's config file. (Note: whitelisting is only required when building or serving with the `--safe` option.)
-->
사이트 환경설정 파일의 `plugins` 배열에 명시되지 않은 경우에도 화이트리스트된 모든 `runtime_dependencies` 는 자동적으로 Jekyll 이 사용하려 할 것입니다. (메모: 화이트리스트는 `--safe` 옵션과 함께 빌드 혹은 미리보기하는 경우에만 필요합니다.)

<!--
With this, the end-user need not keep track of the plugins required to be included in their config file for their theme-gem to work as intended.
-->
이것으로, 최종 사용자는 자신이 사용하는 테마 젬을 올바르게 작동시키기 위해 필요한 플러그인들을 찾아 환경설정 파일에 넣을 필요가 없습니다.

<!--
### Documenting your theme
-->
### 테마 관련 문서 작성

<!--
Your theme should include a `/README.md` file, which explains how site authors can install and use your theme. What layouts are included? What includes? Do they need to add anything special to their site's configuration file?
-->
테마 안에는 사이트 작성자에게 테마를 설치하고 사용하는 방법을 설명하는 `/README.md` 파일이 있어야 합니다. 테마에 포함된 레이아웃과 조각파일은 어떠한지? 사이트 환경설정 파일에 특별히 추가해야할 사항이 있는지?

<!--
### Adding a screenshot
-->
### 스크린샷 추가하기

<!--
Themes are visual. Show users what your theme looks like by including a screenshot as `/screenshot.png` within your theme's repository where it can be retrieved programmatically. You can also include this screenshot within your theme's documentation.
-->
테마는 시각적입니다. 소스코드 저장소로부터 프로그램적으로 가져올 수 있는 경로인 `/screenshot.png` 에 스크린샷을 넣어두어 사용자들에게 테마가 어떻게 생겼는지 볼 수 있게 해주세요. 테마의 문서에도 스크린샷을 포함시킬 수 있습니다.

<!--
### Previewing your theme
-->
### 테마 미리보기

<!--
To preview your theme as you're authoring it, it may be helpful to add dummy content in, for example, `/index.html` and `/page.html` files. This will allow you to use the `jekyll build` and `jekyll serve` commands to preview your theme, just as you'd preview a Jekyll site.
-->
테마를 미리보기 하려면 실제로 사용해보세요. 임의의 가상 컨텐츠, 예를 들면 `/index.html` 과 `/page.html` 같은 파일을 넣어두는게 도움이 될 것입니다. 이로써 Jekyll 사이트의 미리보기를 하는 것과 동일하게, `jekyll build` 와 `jekyll serve` 명령으로 테마를 미리보기 할 수 있습니다.

<!--
If you do preview your theme locally, be sure to add `/_site` to your theme's `.gitignore` file to prevent the compiled site from also being included when you distribute your theme.
-->
로컬상에서 테마를 미리보기하는 경우, 컴파일된 사이트가 배포판에 포함되지 않도록 테마의 `.gitignore` 파일에 `/_site` 를 추가하는 것을 잊지 마세요.
{: .info .note}

<!--
### Publishing your theme
-->
### 테마 배포하기

<!--
Themes are published via [RubyGems.org](https://rubygems.org). You will need a RubyGems account, which you can [create for free](https://rubygems.org/sign_up).
-->
테마는 [RubyGems.org](https://rubygems.org) 를 통해 배포됩니다. RubyGems 계정이 필요한데, [무료로 생성](https://rubygems.org/sign_up)할 수 있습니다.

<!--
1. First, you need to have it in a git repository:

   ```sh
   git init # Only the first time
   git add -A
   git commit -m "Init commit"
   ```

2. Next, package your theme, by running the following command, replacing `jekyll-theme-awesome` with the name of your theme:

   ```sh
   gem build jekyll-theme-awesome.gemspec
   ```

3. Finally, push your packaged theme up to the RubyGems service, by running the following command, again replacing `jekyll-theme-awesome` with the name of your theme:

   ```sh
   gem push jekyll-theme-awesome-*.gem
   ```

4. To release a new version of your theme, update the version number in the gemspec file, ( `jekyll-theme-awesome.gemspec` in this example ), and then repeat Steps 1 - 3 above. We recommend that you follow [Semantic Versioning](http://semver.org/) while bumping your theme-version.
-->
1. 먼저, 모든 파일을 git 저장소에 넣어야합니다:

   ```sh
   git init # Only the first time
   git add -A
   git commit -m "Init commit"
   ```

2. 다음, 아래의 명령을 사용해서 테마를 패키지로 만드는데, `jekyll-theme-awesome` 부분을 당신의 테마 이름으로 바꾸세요:

   ```sh
   gem build jekyll-theme-awesome.gemspec
   ```

3. 마지막으로, 아래의 명령을 사용해서 패키지로 만든 테마를 RubyGems 서비스에 등록하는데, 이때 역시 `jekyll-theme-awesome` 부분을 당신의 테마 이름으로 바꾸세요:

   ```sh
   gem push jekyll-theme-awesome-*.gem
   ```

4. 테마의 새 버전을 배포할 때에는, gemspec 파일 (이 예제에서는 `jekyll-theme-awesome.gemspec`) 에 버전정보를 업데이트하고, 위의 1 - 3 단계를 다시 수행합니다. 테마의 버전정보를 변경할 때는 [유의적 버전](http://semver.org/) 규칙을 따르기를 권장합니다.
