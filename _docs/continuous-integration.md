---
layout: docs
title: 지속적인 통합
permalink: /docs/continuous-integration/
---

여러가지 버전의 Ruby 에서 웹사이트 생성 테스트를 하는 것도 어렵지 않습니다.
다음 안내서들은 [Travis][0] 에 무료 빌드환경을 구성하고 Pull Request 를
사용하여 [GitHub][1] 과 연동하는 방법을 설명하고 있습니다. 비공개 저장소의
경우에는 유료로 구축할 수 있는 다른 방법이 존재합니다.

[0]: https://travis-ci.org/
[1]: https://github.com/

## 1. Travis 와 GitHub 활성화

GitHub 저장소에 Travis 빌드를 활성화하는 것은 상당히 간단합니다:

1. 자신의 travis-ci.org 프로파일 페이지에 접속합니다: https://travis-ci.org/profile/username
2. 빌드를 활성화하려는 저장소를 찾습니다.
3. 오른편의 슬라이더를 클릭해서 어두운 회색의 "ON" 상태로 만듭니다.
4. 원한다면 공구모양 아이콘을 클릭해서 빌드에 대한 환경설정을 조정합니다.
   세부적인 환경설정은 `.travis.yml` 파일로 조정합니다. 더 자세한 설명은 다음을
   읽어보세요.

## 2. 테스트 스크립트

가장 단순한 형태의 테스트 스크립트는 그냥 `jekyll build` 를 실행하고 Jekyll 이
성공적으로 사이트 빌드를 마쳤는지만 확인합니다. 빌드 작업이 올바른지는
확인하지만, 생성된 사이트는 확인하지 않습니다.

Jekyll 의 출력 결과물을 테스트한다면, [html-proofer][2] 보다 좋은 도구는
없습니다. 이것을 사용하면 생성된 사이트의 모든 링크와 이미지가 존재하는지 확인할
수 있습니다. 해당 Gem 을 활용하는 Ruby 스크립트를 작성하거나, `htmlproof` 라는
편리한 명령행 실행 프로그램으로 이 도구의 기능을 활용할 수 있습니다.

실행하려는 명령어를 `./script/cibuild` 파일에 저장해두세요.

### HTML Proofer 실행파일

{% highlight bash %}
#!/usr/bin/env bash
set -e # 에러 발생 시 스크립트 중단

bundle exec jekyll build
bundle exec htmlproofer ./_site
{% endhighlight %}

몇몇 옵션은 명령행 스위치를 통해서 지정할 수 있습니다. 스위치들에 관한 더 많은
정보는 `html-proofer` README 를 읽어보거나, `htmlproofer --help` 를 실행하면
확인할 수 있습니다.

외부 사이트 테스트를 생략하는 방법을 예로 들면, 이렇게 실행합니다:

{% highlight bash %}
$ bundle exec htmlproof ./_site --disable-external
{% endhighlight %}

### HTML Proofer 라이브러리

또한 Ruby 스크립트에서 `html-proofer` 를 호출할 수도 있습니다 (예시, Rakefile 안에서 호출):

{% highlight ruby %}
#!/usr/bin/env ruby

require 'html/proofer'
HTML::Proofer.new("./_site").run
{% endhighlight %}

옵션은 `.new` 의 두 번째 전달인자이며, 심볼-키 Ruby 해시로 인코딩 됩니다.
환경설정 옵션에 관련된 더 많은 정보는 `html-proofer` 의 README 파일을 확인해
보세요.

[2]: https://github.com/gjtorikian/html-proofer

## 3. Travis 빌드 환경설정

이 파일은 Travis 빌드 환경설정에 사용됩니다. Jekyll 은 Ruby 로 작성되었고
몇 가지 RubyGem 들의 설치를 필요로 하기 때문에, Ruby 언어 빌드 환경을
선택했습니다. 아래는 샘플 `.travis.yml` 파일이며, 그 뒤는 각 설정에 대한
설명입니다.

**중요:** Travis 가 필요한 모든 의존성을 [자동으로 설치](http://docs.travis-ci.com/user/languages/ruby/#Dependency-Management)할 수 있도록, Gem 참조목록인 Gemfile 이 필요합니다.

{% highlight ruby %}
source "https://rubygems.org"

gem "jekyll"
gem "html-proofer"
{% endhighlight %}

`.travis.yml` 파일은 이런 내용을 갖고 있어야 합니다:

{% highlight yaml %}
language: ruby
rvm:
- 2.1

before_script:
 - chmod +x ./script/cibuild # 또는 로컬에서 직접 실행 후 커밋

# bundler 를 사용한다고 가정함. 따라서
# `install` 단계에 `bundle install` 이 디폴트로 실행됨.
script: ./script/cibuild

# 브랜치 화이트리스트. GitHub Pages 에서만 사용됨
branches:
  only:
  - gh-pages     # gh-pages 브랜치를 테스트 함
  - /pages-(.*)/ # "pages-" 로 시작하는 모든 브랜치를 테스트 함

env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # html-proofer 의 설치 속도를 높여줌
{% endhighlight %}

좋습니다. 여기서부터는 각 줄에 관한 설명입니다:

{% highlight yaml %}
language: ruby
{% endhighlight %}

Travis 에게 Ruby 빌드 컨테이너를 사용하도록 지시하는 내용입니다. 이 컨테이너는
Bundler, RubyGem, Ruby 실행환경의 스크립트 접근 권한을 제공합니다.

{% highlight yaml %}
rvm:
- 2.1
{% endhighlight %}

RVM 은 (rbenv, chruby 등과 같은) 대중적인 Ruby 버전 관리자입니다. 이 설정은
테스트 스크립트를 실행할 때 사용할 Ruby 버전을 Travis 에게 알려주는 역할을
합니다.

{% highlight yaml %}
before_script:
 - chmod +x ./script/cibuild
{% endhighlight %}

빌드 스크립트 파일에 *실행가능* 속성이 설정되어 있지 않으면 권한 거부 에러가
발생하여 Travis 가 올바르게 실행되지 않을 것입니다. 로컬상에서 이 명령을 실행한
후 커밋하는 것으로 권한을 직접 설정할 수도 있으며, 그럴 경우 이 단계는 필요하지
않습니다.

{% highlight yaml %}
script: ./script/cibuild
{% endhighlight %}

Travis 는 사이트 테스트에 임의의 쉘 스크립트를 사용하는 것도 허용합니다.
프로젝트에 관련된 모든 스크립트들은 `script` 디렉토리에 있어야 하고, `cibuild`
라는 테스트 스크립트를 호출한다는 단 하나의 규약만 지키면 됩니다. 이 줄은
자유롭게 수정할 수 있습니다. 스크립트에서 하는 일이 많지 않다면, 테스트 내용을
여기에 직접 적을 수도 있습니다:

{% highlight yaml %}
install: gem install jekyll html-proofer
script: jekyll build && htmlproof ./_site
{% endhighlight %}

`script` 설정에는 올바른 쉘 명령어라면 어떤 것이든 사용할 수 있습니다.

{% highlight yaml %}
# 브랜치 화이트리스트. GitHub Pages 에서만 사용됨
branches:
  only:
  - gh-pages     # gh-pages 브랜치를 테스트 함
  - /pages-(.*)/ # "pages-" 로 시작하는 모든 브랜치를 테스트 함
{% endhighlight %}

사이트를 담고있는 브랜치 또는 브랜치들에만 Travis 빌드를 실행하는 경우를
생각해봅시다. 이렇게 빌드를 고립시키는 한 가지 방법은 Travis 환경설정 파일에
브랜치 화이트리스트를 넣는 것입니다.
`gh-pages` 브랜치를 지정해서, (위에 설명한) 관련된 테스트 스크립트가 사이트
브랜치에 대해서만 실행되게 할 수 있습니다.
변경을 제안할 때 Pull Request 방식을 사용한다면, 특정 접두사를 포함하는
브랜치에만 빌드를 적용하도록 지시할 수 있는데, 그 전형적인 예시가 바로 위 예제의
정규 표현식 `/pages-(.*)/` 입니다.

`branches` 설정은 완전히 선택사항입니다. 이 설정을 하지 않으면 Travis 는
저장소의 어떤 브랜치에든 push 가 발생할 때마다 빌드를 수행할 것입니다.

{% highlight yaml %}
env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # html-proofer 의 설치 속도를 높여줌
{% endhighlight %}

`html-proofer` 를 사용하나요? 이 환경변수가 필요할 것입니다. Nokogiri 란, 생성된
사이트의 HTML 파일을 파싱하는데에 사용되는데, 설치할 때마다 매번 컴파일 해야하는
라이브러리와 함께 제공됩니다. 운 좋게도, 환경 변수인
`NOKOGIRI_USE_SYSTEM_LIBRARIES` 를 `true` 로 설정해서 Nokogiri 의 설치 시간을
극적으로 감소시킬 수 있습니다.

<div class="note warning">
  <h5><code>_config.yml</code> 에서 <code>vendor</code> 를 제외하는 것을 잊지
   마세요</h5>
  <p>Travis 는 빌드 서버의 <code>vendor</code> 디렉토리에 있는 모든 gem 들을 포함하는데,
   의도치 않게 Jekyll 이 읽어들여 망가질 수 있습니다.</p>
</div>

{% highlight yaml %}
exclude: [vendor]
{% endhighlight %}

### 문제해결

**Travis 에러:** *"You are trying to install in deployment mode after changing
your Gemfile. Run bundle install elsewhere and add the updated Gemfile.lock
to version control."*

**대안:** 로컬에서 `bundle install` 을 실행하고 `Gemfile.lock` 을 커밋하거나,
저장소의 `Gemfile.lock` 을 지우고 `.gitignore` 파일에 추가하여 더 이상 등록되지
않게 하세요.

### 질문?

이 안내서는 모두 오픈-소스입니다. 마음껏 사용하고, 고칠 부분이 있다면
[수정][3]하거나, 문제가 발생하여 도움이 필요하다면 [도움을 요청][4]하세요.

[3]: https://github.com/jekyll/jekyll/edit/master/site/_docs/continuous-integration.md
[4]: http://jekyllrb.com/help/
