---
title: "Travis CI"
---

<!--
You can test your website build against one or more versions of Ruby.
The following guide will show you how to set up a free build environment on
[Travis][travis], with [GitHub][github] integration for pull requests.
-->
웹사이트 빌드 테스트는 여러 버전의 루비에 대해서도 가능합니다.
다음 안내서들은 [Travis][travis] 에 무료 빌드환경을 구성하고 Pull Request 를
사용하여 [GitHub][github] 과 연동하는 방법을 설명하고 있습니다.

[travis]: https://travis-ci.org/
[github]: https://github.com/

<!--
## 1. Enabling Travis and GitHub
-->
## 1. Travis 와 GitHub 활성화

<!--
To enable Travis builds for your GitHub repository:
-->
GitHub 저장소에 Travis 빌드를 활성화하려면:

<!--
1. Go to your profile on travis-ci.org: https://travis-ci.org/profile/username
2. Find the repository for which you're interested in enabling builds.
3. Flick the repository switch on so that it turns blue.
4. Optionally configure the build by clicking on the gear icon. Further
   configuration happens via your `.travis.yml` file. More details below.
-->
1. 자신의 travis-ci.org 프로파일 페이지에 접속합니다: https://travis-ci.org/profile/username
2. 빌드를 활성화하려는 저장소를 찾습니다.
3. 저장소의 스위치를 밀면 파란 불이 켜집니다.
4. 원한다면 톱니모양 아이콘을 클릭해서 빌드에 대한 환경설정을 조정합니다.
   세부적인 환경설정은 `.travis.yml` 파일로 조정합니다. 더 자세한 설명은 다음을
   읽어보세요.

<!--
## 2. The Test Script
-->
## 2. 테스트 스크립트

<!--
The simplest test script runs `jekyll build` and ensures that Jekyll
doesn't fail to build the site. It doesn't check the resulting site, but it
does ensure things are built properly.
-->
가장 단순한 형태의 테스트 스크립트는 `jekyll build` 를 실행하고 Jekyll 이
성공적으로 사이트 빌드를 마쳤는지만 확인합니다. 빌드 작업이 올바른지는
확인하지만, 생성된 사이트는 확인하지 않습니다.

<!--
When testing Jekyll output, there is no better tool than [html-proofer][html-proofer].
This tool checks your resulting site to ensure all links and images exist.
Utilize it either with the convenient `htmlproofer` command-line executable,
or write a Ruby script which utilizes the gem.
-->
Jekyll 의 출력 결과물을 테스트한다면, [html-proofer][html-proofer] 보다 좋은 도구는
없습니다. 이것을 사용하면 생성된 사이트의 모든 링크와 이미지가 존재하는지 확인할
수 있습니다. 해당 루비 젬을 활용하는 루비 스크립트를 작성하거나, `htmlproofer` 라는
편리한 명령행 실행 프로그램으로 이 도구의 기능을 활용할 수 있습니다.

<!--
Save the commands you want to run and succeed in a file: `./script/cibuild`
-->
실행하려는 명령어를 `./script/cibuild` 파일에 저장해두세요.

<!--
### The HTML Proofer Executable
-->
### HTML Proofer 실행파일

```bash
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build
bundle exec htmlproofer ./_site
```

<!--
Some options can be specified via command-line switches. Check out the
`html-proofer` README for more information about these switches, or run
`htmlproofer --help` locally.
-->
몇몇 옵션은 명령행 스위치를 통해서 지정할 수 있습니다. 스위치에 관한 더 많은
정보는 `html-proofer` README 를 읽어보거나, `htmlproofer --help` 를 실행하면
확인할 수 있습니다.

<!--
For example to avoid testing external sites, use this command:
-->
외부 사이트 테스트를 생략하는 방법을 예로 들면, 이렇게 실행합니다:

```sh
bundle exec htmlproofer ./_site --disable-external
```

<!--
### The HTML Proofer Library
-->
### HTML Proofer 라이브러리

<!--
You can also invoke `html-proofer` in Ruby scripts (e.g. in a Rakefile):
-->
또한 루비 스크립트에서 `html-proofer` 를 호출할 수도 있습니다 (예시, Rakefile 안에서 호출):

```ruby
#!/usr/bin/env ruby

require 'html-proofer'
HTMLProofer.check_directory("./_site").run
```

<!--
Options are given as a second argument to `.new`, and are encoded in a
symbol-keyed Ruby Hash. For more information about the configuration options,
check out `html-proofer`'s README file.
-->
옵션은 `.new` 의 두 번째 파라메터이며, 심볼-키 루비 해시로 인코딩 됩니다.
환경설정 옵션에 관련된 더 많은 정보는 `html-proofer` 의 README 파일을 확인해
보세요.

[html-proofer]: https://github.com/gjtorikian/html-proofer

<!--
## 3. Configuring Your Travis Builds
-->
## 3. Travis 빌드 환경설정

<!--
This file is used to configure your Travis builds. Because Jekyll is built
with Ruby and requires RubyGems to install, we use the Ruby language build
environment. Below is a sample `.travis.yml` file, followed by
an explanation of each line.
-->
이 파일은 Travis 빌드 환경설정에 사용됩니다. Jekyll 은 루비로 작성되었고
RubyGems 설치를 필요로 하기 때문에, 루비 언어 빌드 환경을 선택했습니다.
아래는 샘플 `.travis.yml` 파일이며, 그 뒤는 각 설정에 대한
설명입니다.

<!--
**Note:** You will need a Gemfile as well, [Travis will automatically install](https://docs.travis-ci.com/user/languages/ruby/#Dependency-Management) the dependencies based on the referenced gems. Here is an example `Gemfile` with two referenced gems, "jekyll" and "html-proofer":
-->
**중요:** Travis 가 필요한 모든 의존성을 [자동으로 설치](https://docs.travis-ci.com/user/languages/ruby/#Dependency-Management)할 수 있도록, 루비 젬 참조목록인 Gemfile 이 필요합니다. 다음은 두 개의 젬 ("jekyll" 과 "html-proofer") 을 의존요소로 가진 `Gemfile` 예시입니다.

```ruby
source "https://rubygems.org"

gem "jekyll"
gem "html-proofer"
```

<!--
Your `.travis.yml` file should look like this:
-->
`.travis.yml` 파일은 이런 내용을 갖고 있어야 합니다:

```yaml
language: ruby
rvm:
  - 2.6.3

before_script:
 - chmod +x ./script/cibuild # or do this locally and commit

# Assume bundler is being used, therefore
# the `install` step will run `bundle install` by default.
script: ./script/cibuild

# branch whitelist, only for GitHub Pages
branches:
  only:
  - gh-pages     # test the gh-pages branch
  - /pages-(.*)/ # test every branch which starts with "pages-"

env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # speeds up installation of html-proofer

addons:
  apt:
    packages:
    - libcurl4-openssl-dev

sudo: false # route your build to the container-based infrastructure for a faster build

cache: bundler # caching bundler gem packages will speed up build

# Optional: disable email notifications about the outcome of your builds
notifications:
  email: false
```

<!--
Ok, now for an explanation of each line:
-->
좋습니다. 여기서부터는 각 줄에 관한 설명입니다:

```yaml
language: ruby
```

<!--
This line tells Travis to use a Ruby build container. It gives your script
access to Bundler, RubyGems, and a Ruby runtime.
-->
Travis 에게 루비 빌드 컨테이너를 사용하도록 지시하는 내용입니다. 이
컨테이너는 Bundler, RubyGems, 루비 런타임에 접근하는 스크립트를 제공합니다.

```yaml
rvm:
  - 2.6.3
```

<!--
RVM is a popular Ruby Version Manager (like rbenv, chruby, etc). This
directive tells Travis the Ruby version to use when running your test
script. Use a [version which is pre-installed on the Travis build docker][5]
image to speed up the build.
-->
RVM 은 (rbenv, chruby 등과 같은) 대중적인 루비 버전 관리자입니다. 이 설정은
테스트 스크립트를 실행할 때 사용할 루비 버전을 Travis 에게 알려주는 역할을
합니다. [Travis 빌드 도커에 포함된 버전][5]
이미지를 사용하면 빌드 속도가 향상됩니다.

```yaml
before_script:
 - chmod +x ./script/cibuild
```

<!--
The build script file needs to have the *executable* attribute set or
Travis will fail with a permission denied error. You can also run this
locally and commit the permissions directly, thus rendering this step
irrelevant.
-->
빌드 스크립트 파일에 *실행가능* 속성이 설정되어 있지 않으면 권한 거부 에러가
발생하여 Travis 가 올바르게 실행되지 않을 것입니다. 로컬상에서 이 명령을 실행한
후 커밋하는 것으로 권한을 직접 설정할 수도 있으며, 그럴 경우 이 단계는 필요하지
않습니다.

```yaml
script: ./script/cibuild
```

<!--
Travis allows you to run any arbitrary shell script to test your site. One
convention is to put all scripts for your project in the `script`
directory, and to call your test script `cibuild`. This line is completely
customizable. If your script won't change much, you can write your test
incantation here directly:
-->
Travis 는 사이트 테스트에 임의의 쉘 스크립트를 사용하는 것도 허용합니다.
프로젝트에 관련된 모든 스크립트는 `script` 디렉토리에 있어야 하고, `cibuild`
라는 테스트 스크립트를 호출한다는 단 하나의 규약만 지키면 됩니다. 이 줄은
자유롭게 수정할 수 있습니다. 스크립트에서 하는 일이 많지 않다면, 테스트 내용을
여기에 직접 적을 수도 있습니다:

```yaml
install: gem install jekyll html-proofer
script: jekyll build && htmlproofer ./_site
```

<!--
The `script` directive can be absolutely any valid shell command.
-->
`script` 설정에는 올바른 쉘 명령어라면 어떤 것이든 사용할 수 있습니다.

```yaml
# branch whitelist, only for GitHub Pages
branches:
  only:
  - gh-pages     # test the gh-pages branch
  - /pages-(.*)/ # test every branch which starts with "pages-"
```

<!--
You want to ensure the Travis builds for your site are being run only on
the branch or branches which contain your site. One means of ensuring this
isolation is including a branch whitelist in your Travis configuration
file. By specifying the `gh-pages` branch, you will ensure the associated
test script (discussed above) is only executed on site branches. If you use
a pull request flow for proposing changes, you may wish to enforce a
convention for your builds such that all branches containing edits are
prefixed, exemplified above with the `/pages-(.*)/` regular expression.
-->
사이트를 담고있는 브랜치 또는 브랜치들에만 Travis 빌드를 실행하는 경우를
생각해봅시다. 이렇게 빌드를 고립시키는 한 가지 방법은 Travis 환경설정 파일에
브랜치 화이트리스트를 넣는 것입니다.
`gh-pages` 브랜치를 지정해서, (위에 설명한) 관련된 테스트 스크립트가 사이트
브랜치에 대해서만 실행되게 할 수 있습니다.
변경을 제안할 때 Pull Request 방식을 사용한다면, 특정 접두사를 포함하는
브랜치에만 빌드를 적용하도록 지시할 수 있는데, 그 전형적인 예시가 바로 위 예제의
정규 표현식 `/pages-(.*)/` 입니다.

<!--
The `branches` directive is completely optional. Travis will build from every
push to any branch of your repo if leave it out.
-->
`branches` 설정은 완전히 선택사항입니다. 이 설정을 하지 않으면 Travis 는
저장소의 어떤 브랜치에든 push 가 발생할 때마다 빌드를 수행할 것입니다.

```yaml
env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # speeds up installation of html-proofer
```

<!--
Using `html-proofer`? You'll want this environment variable. Nokogiri, used
to parse HTML files in your compiled site, comes bundled with libraries
which it must compile each time it is installed. Luckily, you can
dramatically decrease the install time of Nokogiri by setting the
environment variable `NOKOGIRI_USE_SYSTEM_LIBRARIES` to `true`.
-->
`html-proofer` 를 사용하나요? 이 환경변수가 필요할 것입니다. Nokogiri 란, 생성된
사이트의 HTML 파일을 파싱하는데에 사용되는데, 설치할 때마다 매번 컴파일 해야하는
라이브러리와 함께 제공됩니다. 운 좋게도, 환경 변수인
`NOKOGIRI_USE_SYSTEM_LIBRARIES` 를 `true` 로 설정해서 Nokogiri 의 설치 시간을
극적으로 감소시킬 수 있습니다.

<div class="note warning">
<!--
  <h5>Be sure to exclude <code>vendor</code> from your
   <code>_config.yml</code></h5>
  <p>Travis bundles all gems in the <code>vendor</code> directory on its build
   servers, which Jekyll will mistakenly read and explode on.</p>
-->
  <h5><code>_config.yml</code> 에서 <code>vendor</code> 를 제외하는 것을 잊지
   마세요</h5>
  <p>Travis 는 빌드 서버의 <code>vendor</code> 디렉토리에 있는 모든 루비 젬들을 포함하는데,
   의도치 않게 Jekyll 이 읽어들여 망가질 수 있습니다.</p>
</div>

```yaml
exclude: [vendor]
```

By default you should supply the `sudo: false` command to Travis. This command
explicitly tells Travis to run your build on Travis's [container-based
 infrastructure](https://docs.travis-ci.com/user/workers/container-based-infrastructure/#Routing-your-build-to-container-based-infrastructure). Running on the container-based infrastructure can often times
speed up your build. If you have any trouble with your build, or if your build
does need `sudo` access, modify the line to `sudo: required`.

```yaml
sudo: false
```

To speed up the build, you should cache the gem packages created by `bundler`.
Travis has a pre-defined [cache strategy for this tool][6] which should have
all the default configs to do exactly that.

```yaml
cache: bundler
```

Optionally, if you are not interested in the build email notifications you
can disable them with this configuration. Travis supports a wide array of
notification services, you may find [another one more useful (e.g. slack)][7].

```yaml
notifications:
  email: false
```

<!--
### Troubleshooting
-->
### 문제해결

<!--
**Travis error:** *"You are trying to install in deployment mode after changing
your Gemfile. Run bundle install elsewhere and add the updated Gemfile.lock
to version control."*
-->
**Travis 에러:** *"You are trying to install in deployment mode after changing
your Gemfile. Run bundle install elsewhere and add the updated Gemfile.lock
to version control."*

<!--
**Workaround:** Either run `bundle install` locally and commit your changes to
`Gemfile.lock`, or remove the `Gemfile.lock` file from your repository and add
an entry in the `.gitignore` file to avoid it from being checked in again.
-->
**대안:** 로컬에서 `bundle install` 을 실행하고 `Gemfile.lock` 을 커밋하거나,
저장소의 `Gemfile.lock` 을 지우고 `.gitignore` 파일에 추가하여 더 이상 등록되지
않게 하세요.

<!--
### Questions?
-->
### 질문?

<!--
This entire guide is open-source. Go ahead and [edit it][3] if you have a
fix or [ask for help][4] if you run into trouble and need some help.
-->
이 안내서는 모두 오픈-소스입니다. 마음껏 사용하고, 고칠 부분이 있다면
[수정][3]하거나, 문제가 발생하여 도움이 필요하다면 [도움을 요청][4]하세요.

[3]: https://github.com/jekyll/jekyll/edit/master/docs/_docs/continuous-integration/travis-ci.md
[4]: https://jekyllrb.com/help/
[5]: https://docs.travis-ci.com/user/languages/ruby/#Specifying-Ruby-versions-and-implementations
[6]: https://docs.travis-ci.com/user/caching/#Caching-directories-(Bundler%2C-dependencies)
[7]: https://docs.travis-ci.com/user/notifications/
