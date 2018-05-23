---
#title: Quick-start guide
title: 빠른시작 설명서
permalink: /docs/quickstart/
---


<!--
If you already have a full [Ruby](https://www.ruby-lang.org/en/downloads/) development environment with all headers and [RubyGems](https://rubygems.org/pages/download) installed (see Jekyll's [requirements](/docs/installation/#requirements)), you can create a new Jekyll site by doing the following:
-->
모든 헤더와 [RubyGems](https://rubygems.org/pages/download) 가 포함된 완전한 [Ruby](https://www.ruby-lang.org/en/downloads/) 개발 환경이 이미 준비되었다면(Jekyll 에 [필요한 것들](/docs/installation/#requirements) 참고), 다음 명령으로 새 Jekyll 사이트를 생성할 수 있습니다:

<!--
```sh
# Install Jekyll and Bundler gems through RubyGems
gem install jekyll bundler

# Create a new Jekyll site at ./myblog
jekyll new myblog

# Change into your new directory
cd myblog

# Build the site on the preview server
bundle exec jekyll serve

# Now browse to http://localhost:4000
```
-->
```sh
# RubyGems 를 통해 Jekyll 과 Bundler 를 설치한다
gem install jekyll bundler

# ./myblog 에 새 Jekyll 사이트를 생성한다
jekyll new myblog

# 생성된 디렉토리로 이동한다
cd myblog

# 미리보기 서버로 사이트를 빌드한다
bundle exec jekyll serve

# 이제 브라우저로 http://localhost:4000 에 접속한다
```

<!--
If you encounter any unexpected errors during the above, please refer to the [troubleshooting](/docs/troubleshooting/#configuration-problems) page or the already-mentioned [requirements](/docs/installation/#requirements) page, as you might be missing development headers or other prerequisites.
-->
만약 위 명령을 실행하다가 예기치 않은 문제가 발생했다면, [문제해결](/docs/troubleshooting/) 페이지를 참고하거나 앞서 언급된 [필요한 것들](/docs/installation/#requirements) 페이지를 참고하세요, 개발 헤더나 기타 전제 조건이 누락되었을 수 있습니다.

<!--
## About Bundler
-->
## Bundler 에 관하여

<!--
`gem install bundler` installs the [bundler](https://rubygems.org/gems/bundler) gem through [RubyGems](https://rubygems.org/). You only need to install it once &mdash; not every time you create a new Jekyll project. Here are some additional details:
-->
`gem install bundler` 명령은 [RubyGems](https://rubygems.org/) 를 사용해 [bundler](https://rubygems.org/gems/bundler) gem 을 설치합니다. 이 명령은 gem 을 설치하기 위한 것으로 한 번만 실행하면 됩니다 &mdash; 매번 새 Jekyll 프로젝트를 만들 때마다가 아닙니다. 자세한 내용은 다음을 참고하세요:

<!--
* `bundler` is a gem that manages other Ruby gems. It makes sure your gems and gem versions are compatible, and that you have all necessary dependencies each gem requires.
* The `Gemfile` and `Gemfile.lock` files inform Bundler about the gem requirements in your site. If your site doesn't have these Gemfiles, you can omit `bundle exec` and just run `jekyll serve`.
-->
* `bundler` 는 다른 Ruby gem 들을 관리하는 gem 입니다. 각각의 gem 들이 작동하기 위한 필수 의존요소들을 설치해주기 때문에 언제나 당신은 호환되는 버전의 gem 들을 가지고 있게 됩니다.
* `Gemfile` 과 `Gemfile.lock` 은 당신의 사이트에 필요한 gem 들을 Bundler 에게 알려주는 역할을 합니다. 만약 사이트에 이 파일들이 없다면, `bundle exec` 를 생략하고 `jekyll serve` 만 실행해도 됩니다.

<!--
* When you run `bundle exec jekyll serve`, Bundler uses the gems and versions as specified in `Gemfile.lock` to ensure your Jekyll site builds with no compatibility or dependency conflicts.
-->
* `bundle exec jekyll serve` 라고 실행하면, Bundler 는 `Gemfile.lock` 에 명시된 버전의 gem 을 사용해 Jekyll 사이트를 생성하기 때문에 의존성과 호환성에 어떠한 충돌도 발생하지 않습니다.

<!--
For more information about how to use Bundler in your Jekyll project, this [tutorial](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/) should provide answers to the most common questions and explain how to get up and running quickly.
-->
Jekyll 프로젝트에 Bundler 를 사용하는 방법에 관하여 더 자세히 알고싶다면, 이 [튜토리얼](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/)을 살펴보세요. 빠른 설치와 실행 방법 및 자주 있는 질문에 대한 해답을 제공합니다.
 
<!--
## Options for creating a new site with Jekyll
-->
## Jekyll 사이트 생성 관련 옵션들

<!--
`jekyll new <PATH>` installs a new Jekyll site at the path specified (relative to current directory). In this case, Jekyll will be installed in a directory called `myblog`. Here are some additional details:
-->
`jekyll new <경로>` 명령은 지정한 경로(현재 디렉토리 기준의 상대경로)에 새 Jekyll 사이트를 생성합니다. 위의 예시에서는, `myblog` 라는 디렉토리에 Jekyll 사이트가 생성됩니다. 추가 설명을 몇 가지 하자면:

<!--
* To install the Jekyll site into the directory you're currently in, run `jekyll new .` If the existing directory isn't empty, you can pass the `--force` option with `jekyll new . --force`.
* `jekyll new` automatically initiates `bundle install` to install the dependencies required. (If you don't want Bundler to install the gems, use `jekyll new myblog --skip-bundle`.)
* By default, the Jekyll site installed by `jekyll new` uses a gem-based theme called [Minima](https://github.com/jekyll/minima). With [gem-based themes](../themes), some of the directories and files are stored in the theme-gem, hidden from your immediate view.
* We recommend setting up Jekyll with a gem-based theme but if you want to start with a blank slate, use `jekyll new myblog --blank`
* To learn about other parameters you can include with `jekyll new`, type `jekyll new --help`.
-->
* 현재 디렉토리에 Jekyll 사이트를 만드려면, `jekyll new .` 을 실행하세요. 만약 디렉토리가 비어있지 않은 경우에는, `--force` 옵션을 넣어서 `jekyll new . --force` 라고 실행하면 됩니다.
* `jekyll new` 명령은 자동으로 `bundle install` 을 실행해서 의존관계의 gem 들을 설치합니다. (만약 Bundler 를 통한 gem 설치를 원하지 않는다면, `jekyll new myblog --skip-bundle` 이라고 입력하세요.)
* 기본적으로, `jekyll new` 명령으로 설치된 Jekyll 사이트는 [Minima](https://github.com/jekyll/minima) 라는 gem 기반의 테마를 사용합니다. [gem 기반 테마들](../themes)의 일부 디렉토리나 파일은 감춰져서 보이지 않을 수도 있습니다.
* 저희가 권장하는 Jekyll 설정법은 gem 기반 테마를 사용하는 것이지만 백지 상태로 시작하고자 한다면, `jekyll new myblog --blank` 명령을 사용하세요.
* `jekyll new` 에 사용할 수 있는 다른 파라미터들을 더 알고 싶다면, `jekyll new --help` 라고 입력하세요.

<!--
When in doubt, use the <code>help</code> command to remind you of all available options and usage, it also works with the <code>new</code>, <code>build</code> and <code>serve</code> subcommands, e.g. <code>jekyll help new</code> or <code>jekyll help build</code>.
-->
언제든지, <code>help</code> 명령을 사용해서 이용 가능한 모든 옵션과 사용법을 확인할 수 있으며, 이 명령은 <code>new</code>, <code>build</code> 와 <code>serve</code> 같은 하위 명령어와 함께 사용할 수도 있습니다. 예시, <code>jekyll help new</code> 또는 <code>jekyll help build</code>.
{: .note .info }

<!--
## Next steps
-->
## 다음 단계

<!--
Building a Jekyll site with the default theme is just the first step. The real magic happens when you start creating blog posts, using the front matter to control templates and layouts, and taking advantage of all the awesome configuration options Jekyll makes available.
-->
기본 테마를 사용한 Jekyll 사이트 생성은 그저 첫 걸음에 불과합니다. 블로그 게시물 등록을 시작하고, 머리말을 사용하여 템플릿과 레이아웃을 조정하거나 Jekyll 이 제공하는 멋진 설정 옵션들을 활용할 때 비로소 진정한 마법이 발휘됩니다.
