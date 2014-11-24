---
layout: docs
title: 지속적인 통합
prev_section: deployment-methods
next_section: troubleshooting
permalink: /docs/continuous-integration/
---

여러가지 Ruby 버전 상에서 웹사이트 생성을 테스트하는 것도 어렵지 않습니다. 이
안내서에서 Pull Request 로 [GitHub][1] 을 연동한 무료 [Travis][0] 빌드환경 구성
방법을 배울 수 있습니다. 비공개 저장소에 대해서는 유료로 구축할 수 있는 다른
방법이 있습니다.

[0]: https://travis-ci.org/
[1]: https://github.com/

## 1. Travis 와 GitHub 활성화

GitHub 저장소에 Travis 빌드를 활성화하는 것은 상당히 간단합니다:

1. 자신의 travis-ci.org 프로파일 페이지에 접속합니다: https://travis-ci.org/profile/username
2. 빌드를 활성화하려는 저장소를 찾습니다.
3. 오른편의 슬라이더를 클릭해서 어두운 회색의 "ON" 상태로 만듭니다.
4. 원한다면 공구모양 아이콘을 클릭해서 빌드에 대한 환경설정을 수정합니다.
   `.travis.yml` 파일로도 환경설정이 가능합니다. 더 자세한 설명은 다음을
   읽어보세요.

## 2. 테스트 스크립트

가장 단순한 형태의 테스트 스크립트는 그냥 `jekyll build` 를 실행하고 Jekyll 이
성공적으로 사이트 빌드를 마쳤는지만 확인합니다. 빌드 작업이 올바른지는
확인하지만, 생성된 사이트는 확인하지 않습니다.

Jekyll 결과물에 대한 테스트를 수행하려면, [html-proofer][2] 라는 더 좋은 도구가
있습니다. 이 도구는 생성된 사이트의 모든 링크와 이미지가 존재하는지 확인합니다.
명령행 실행 프로그램인 `htmlproof` 를 사용하거나, 해당 gem 을 활용하는 Ruby
스크립트를 작성하세요.

### HTML Proofer 실행파일

{% highlight bash %}
#!/usr/bin/env bash
set -e # halt script on error

bundle exec jekyll build
bundle exec htmlproof ./_site
{% endhighlight %}

명령행 스위치를 통해서 지정할 수 있는 옵션이 몇 가지 있습니다. 이 스위치에 대한
더 많은 정보를 얻으려면 `html-proofer` README 를 읽어보거나 `htmlproof --help`
를 실행해보세요.

### HTML Proofer 라이브러리

또한 Ruby 스크립트에서 `html-proofer` 를 호출할 수도 있습니다 (예시, Rakefile 안에서 호출):

{% highlight ruby %}
#!/usr/bin/env ruby

require 'html/proofer'
HTML::Proofer.new("./_site").run
{% endhighlight %}

옵션은 `.new` 의 두 번째 전달인자로 지정하고, 심볼-키 Ruby 해시로 인코딩 됩니다.
환경설정 옵션에 관련된 더 많은 정보는 `html-proofer` 의 README 파일을
읽어보세요.

[2]: https://github.com/gjtorikian/html-proofer

## 3. Travis 빌드 환경설정

이 파일은 Travis 빌드 환경설정에 사용됩니다. Jekyll 은 Ruby 로 작성되었고
요구사항 중에는 몇 가지 RubyGem 들의 설치가 포함되어 있기 때문에, Ruby 언어 빌드
환경을 사용합니다. 아래는 샘플 `.travis.yml` 파일이며, 그 뒤는 각 설정에 대한
설명입니다.

{% highlight yaml %}
language: ruby
rvm:
- 2.1
script: ./script/cibuild

# branch whitelist
branches:
  only:
  - gh-pages     # test the gh-pages branch
  - /pages-(.*)/ # test every branch which starts with "pages-"

env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # speeds up installation of html-proofer
{% endhighlight %}

좋습니다. 여기서부터는 각 줄에 관한 설명입니다:

{% highlight yaml %}
language: ruby
{% endhighlight %}

이 줄은 Travis 에게 Ruby 빌드 컨테이너를 사용하라고 지시합니다. Bundler,
RubyGem, Ruby 실행환경의 스크립트 접근 권한도 넘겨줍니다.

{% highlight yaml %}
rvm:
- 2.1
{% endhighlight %}

RVM 은 (rbenv, chruby 등과 같은) 대중적인 Ruby 버전 관리자입니다. 위 설정은
테스트 스크립트를 실행할 때 사용할 Ruby 버전을 Travis 에게 알려주는 역할을
합니다.

{% highlight yaml %}
script: ./script/cibuild
{% endhighlight %}

Travis 는 임의의 쉘 스크립트를 사용해서 사이트를 테스트하는 것도 허용합니다. 단
한가지 규약은 프로젝트에 관련된 모든 스크립트를 `script` 디렉토리에 넣어야 하고,
`cibuild` 라는 테스트 스크립트를 호출해야 한다는 것입니다. 이 줄은 완전히 다르게
수정할 수 있습니다. 만약 스크립트가 많이 바뀌지 않는다면 테스트 명령어를 여기에
직접 적을 수도 잇습니다:

{% highlight yaml %}
script: jekyll build && htmlproof ./_site
{% endhighlight %}

`script` 설정은 올바른 쉘 명령어라면 어떤 것이든 사용할 수 있습니다.

{% highlight yaml %}
# branch whitelist
branches:
  only:
  - gh-pages     # test the gh-pages branch
  - /pages-(.*)/ # test every branch which starts with "pages-"
{% endhighlight %}

사이트를 담고있는 브랜치 또는 브랜치들에만 Travis 빌드를 실행하는 경우를
생각해봅시다. 이렇게 빌드를 고립시키는 한 가지 방법은 Travis 환경설정 파일에
브랜치 화이트리스트를 넣는 것입니다.
`gh-pages` 브랜치를 지정해서, (위에 설명한) 관련된 테스트 스크립트가 사이트
브랜치에 대해서만 실행되게 할 수 있습니다.
변경을 제안할 때 Pull Request 방식을 사용한다면, 특정 접두사를 포함하는
브랜치에만 빌드를 적용하도록 지시할 수 있는데, 위 예제의 정규 표현식
`/pages-(.*)/` 이 그 전형적인 예시입니다.

`branches` 설정은 완전히 선택사항입니다.

{% highlight yaml %}
env:
  global:
  - NOKOGIRI_USE_SYSTEM_LIBRARIES=true # speeds up installation of html-proofer
{% endhighlight %}

`html-proofer` 를 사용하나요? 이 환경변수가 필요할 것입니다.
Nokogiri, 생성된 사이트의 HTML 파일을 파싱하는데에 사용합니다. 설치할 때마다
모든 라이브러리를 컴파일 해야하는데, 운 좋게도 환경 변수
`NOKOGIRI_USE_SYSTEM_LIBRARIES` 를 `true` 로 설정해서 Nokogiri 의 설치 시간을
극적으로 절감할 수 있습니다.

## 4. Gotchas

### `vendor` 제외시키기

Travis 는 빌드 서버의 `vendor` 디렉토리에 있는 모든 gem 들을 포함하는데, 의도치
않게 Jekyll 이 읽어들여 망가질 수 있습니다. 이를 예방하려면, `_config.yml` 에서
`verdor` 를 제외시키세요:

{% highlight yaml %}
exclude: [vendor]
{% endhighlight %}

### 질문?

이 안내서는 모두 오픈소스입니다. 마음껏 사용하고, 고칠 부분이 있다면
[수정][3]하거나, 문제가 발생하여 도움이 필요하다면 [도움을 요청][4]하세요.

[3]: https://github.com/jekyll/jekyll/edit/master/site/_docs/continuous-integration.md
[4]: https://github.com/jekyll/jekyll-help#how-do-i-ask-a-question
