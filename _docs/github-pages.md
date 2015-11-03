---
layout: docs
title: GitHub Pages
permalink: /docs/github-pages/
---

[GitHub Pages](http://pages.github.com) 는 개인이나 단체 또는 저장소를 위한 공개
웹 페이지로서, GitHub 이 제공하는 `github.io` 도메인이나 자신만의 도메인에
자유롭게 호스팅할 수 있습니다. GitHub Pages 는 내부적으로 Jekyll 에 의해
작동되고 있기 때문에 단순한 HTML 컨텐츠를 지원하는 것 뿐만 아니라, Jekyll 기반의
웹사이트를 무료로 호스팅하기에 탁월한 방법이기도 합니다.

## GitHub Pages 에 Jekyll 사용하기

GitHub Pages 는 GitHub 에 있는 저장소들의 특정 브랜치를 검색하여 작동합니다.
지원하는 방식은 두 가지: 사용자/단체 페이지와 프로젝트 페이지가 있습니다.
이 두 가지 사이트 게시 방법은 아주 조그만 차이점 몇 가지를 제외하고는 거의
동일합니다.

<div class="note protip">
  <h5><code>github-pages</code> Gem 을 사용하세요</h5>
  <p>
    GitHub 에 있는 우리 친구들이 제공해 준
    <a href="https://github.com/github/pages-gem">github-pages</a>
    Gem 으로 GitHub Pages 에서 사용하는 Jekyll 과 그 의존요소들을 관리할 수
    있습니다. GitHub Pages 에 사이트를 게시할 때, 예상치 못하게 여러 Gem 들에
    대한 버전 불일치 문제를 마주칠수도 있는데, 당신의 프로젝트에 이 Gem 을
    사용해서 이러한 문제들을 피할 수 있습니다. 당신의 프로젝트에서 현재 운영중인
    것과 동일한 버전의 Gem 을 사용하려면, <code>Gemfile</code> 에 아래 내용을
    추가하세요:

{% highlight ruby %}
source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
{% endhighlight %}

    이로서 <code>bundle install</code> 을 실행하면 올바른 버전의
    <code>github-pages</code> Gem 을 사용할 수 있습니다.

    이 방법이 제대로 작동하지 않으면, Gemfile 내용을:

{% highlight ruby %}
source 'https://rubygems.org'

gem 'github-pages'
{% endhighlight %}

    처럼 단순하게 정리하고 <code>bundle update</code> 를 자주 실행해주세요.
  </p>
</div>

### 사용자 페이지와 단체 페이지

사용자 페이지와 단체 페이지는 오로지 GitHub Pages 에 관련된 파일만을 위한 특별한
GitHub 저장소를 필요로 합니다. 저장소의 이름은 반드시 계정명으로 시작해야
합니다. 예를 들어, [@mojombo 의 사용자 페이지
저장소](https://github.com/mojombo/mojombo.github.io)의 이름은
`mojombo.github.io` 입니다.

저장소의 `master` 브랜치를 가지고 GitHub Pages 사이트를 구성하고 게시하기
때문에, 반드시 해당 브랜치에 Jekyll 사이트 컨텐츠를 저장하세요.

<div class="note info">
  <h5>커스텀 도메인은 저장소 이름에 영향을 미치지 않습니다</h5>
  <p>
    GitHub Pages 는 최초에 <code>username.github.io</code> 서브 도메인에서
    제공됩니다. 따라서 저장소의 이름은 <strong>커스텀 도메인이
    사용되더라도</strong> 이 방식을 따라야 합니다.
  </p>
</div>

### 프로젝트 페이지

사용자/단체 페이지와는 다르게, 프로젝트 페이지는 해당 프로젝트의 실제 저장소에
함께 보관하는데, 단, `gh-pages` 라는 특별한 이름의 브랜치에 저장한다는 차이점이
있습니다. 이 브랜치의 내용은 Jekyll 에 의해 처리된 후,
`username.github.io/project` (커스텀 도메인을 사용하지 않았을 때 기준—아래 참조)
와 같이 사용자 페이지 서브도메인의 하위 경로에 결과물이 만들어집니다.


Jekyll 프로젝트의 저장소 자체가 이러한 브랜치 구조에 대한 완벽한
예시입니다—[master 브랜치]({{ site.repository }})에는 실제 Jekyll
소프트웨어 프로젝트가 담겨 있지만, (바로 지금 보고있는) Jekyll 웹 사이트는
동일한 저장소의 [gh-pages 브랜치]({{ site.repository }}/tree/gh-pages)에 들어
있습니다.

<div class="note warning">
  <h5>소스 파일은 반드시 루트 디렉토리에 있어야 합니다</h5>
  <p>
GitHub Pages 는 <a href="http://jekyllrb.com/docs/configuration/#global-configuration">“Site Source”</a> 환경설정을 <a href="https://help.github.com/articles/troubleshooting-github-pages-build-failures#source-setting">덮어쓰기</a> 때문에, 루트 디렉토리가 아닌 다른 디렉토리에 파일을 넣어두면 사이트가 올바르게 구성되지 않을 수 있습니다.
  </p>
</div>


### 프로젝트 페이지 URL 구조

자신의 `gh-pages` 브랜치 내용을 GitHub 에 올리기 전에 사이트를 미리보기 해보는
것이 유용할 때가 종종 있습니다. 하지만, GitHub 이 프로젝트 페이지에 사용하는
하위 디렉토리 URL 구조는 URL 을 복잡하게 만듭니다. 여기, 로컬에서의 Jekyll
사이트 미리보기 기능은 유지한 채로 GitHub 프로젝트 페이지 URL 구조
(`username.github.io/project-name/`) 를 활용하는 방법이 있습니다.

1. `_config.yml` 의 `baseurl` 옵션을 `/project-name` 으로 지정한다 -- 맨 앞에는
   슬래시가 있고, 끝에는 슬래시가 **없음**
2. JS 또는 CSS 파일을 사용할 때는 이렇게 한다:
   `{% raw %}{{ site.baseurl }}/path/to/css.css{% endraw %}` -- 슬래시가 변수
   다음에 바로 이어짐 ("path" 바로 앞).
3. 고유주소나 내부 링크를 사용할 때는 이렇게 한다:
   `{% raw %}{{ site.baseurl }}{{ post.url }}{% endraw %}` -- 두 변수 사이에는
   슬래시가 **없음**
4. 마지막으로, 커밋/게시 전에 `jekyll serve` 를 사용하여 사이트를 미리보기
   하려면, `--baseurl` 옵션에 **빈 문자열** 을 전달해야지만 `localhost:4000`
   에서 모든 것을 볼 수 있다 (시작 부분에 `/project-name` 없음):
   `jekyll serve --baseurl ''`

이 방법을 사용하면 로컬에서는 미리보기 사이트가 localhost 의 루트에 생성되지만,
GitHub 이 gh-pages 브랜치에서 페이지를 생성할 때에는 모든 URL 이 `/project-name`
으로 시작하고 정상적으로 작동합니다.

<div class="note">
  <h5>GitHub Pages 문서와 도움말, 지원</h5>
  <p>
    문제해결 안내서와 더불어, GitHub Pages 로 할 수 있는 일에 관련된 더 많은
    정보가 필요하다면, <a
    href="https://help.github.com/categories/20/articles">GitHub’s Pages 도움말
    섹션</a>을 확인하세요. 이걸로도 해결되지 않는 문제가 있다면 <a
    href="https://github.com/contact">GitHub Support</a> 에 연락하세요.
  </p>
</div>
