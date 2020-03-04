---
#title: Plugins
title: 플러그인
permalink: /docs/plugins/installation/
---

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
   사용하려는 플러그인들의 루비 젬 이름을 나열하세요. 예를 들면 다음과 같습니다:

   ```yaml
   # 자동적으로 아래 플러그인들을 필요로 하게 됩니다.
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

   이제 Bundler 그룹의 모든 플러그인을 설치해야 하는데, 단 하나의 명령어 `bundle install` 을 실행하세요.

<div class="note info">
<!--
  <h5>Plugins on GitHub Pages</h5>
  <p>
    <a href="https://pages.github.com/">GitHub Pages</a> is powered by Jekyll.
    All Pages sites are generated using the <code>--safe</code> option
    to disable plugins (with the exception of some
    <a href="https://pages.github.com/versions">whitelisted plugins</a>) for
    security reasons. Unfortunately, this means
    your plugins won’t work if you’re deploying to GitHub Pages.<br><br>
    You can still use GitHub Pages to publish your site, but you’ll need to
    convert the site locally and push the generated static files to your GitHub
    repository instead of the Jekyll source files.
  </p>
-->
  <h5>GitHub Pages 와 플러그인</h5>
  <p>
    <a href="https://pages.github.com/">GitHub Pages</a> 는 Jekyll 을 사용합니다.
    모든 Pages 사이트는 보안상의 이유로 인해 <code>--safe</code> 옵션으로
    플러그인 (<a href="https://pages.github.com/versions">화이트리스트의 플러그인</a>
    제외)이 비활성화된 상태에서 생성됩니다. 안타깝게도
    이 말은, 당신의 플러그인을 GitHub Pages 에서 사용할 수 없다는
    뜻입니다.<br><br>
    그래도 GitHub Pages 와 사용자 플러그인을 함께 사용하는
    방법이 있습니다. GitHub 에 소스를 직접 올리는 대신, 로컬 시스템에서 변환을
    먼저 한 후 생성된 파일을 올리면 됩니다.
  </p>
</div>

<div class="note">
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
    동시에 사용할 수 있습니다
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
Jekyll 은 작업을 시작하기 전에 먼저 이 그룹에 속해있는 루비 젬들을
불러들입니다.

<!--
A gem included here will be activated even if its not explicitly listed under
the `plugins:` key in your site's config file.
-->
심지어 사이트 환경설정 파일의 `plugins:` 키에 정의되어 있지 않더라도, 이
안에 있는 루비 젬들은 활성화됩니다.

{: .note .warning}
<!--
Gems included in the <code>:jekyll-plugins</code> group are activated
regardless of the <code>--safe</code> mode setting. Be aware of which
gems are included under this group!
-->
그룹 <code>:jekyll-plugins</code> 에 포함되어 있는 루비 젬들은
<code>--safe</code> 모드 설정에 관계없이 활성화됩니다. 이 그룹에
어떤 루비 젬들을 포함시킬 것인지 주의를 기울이세요!
