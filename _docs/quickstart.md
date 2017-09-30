---
layout: docs
title: 빠른시작 설명서
permalink: /docs/quickstart/
---

이미 모든 헤더와 [RubyGems](https://rubygems.org/pages/download)을 통해 완전한 [Ruby](https://www.ruby-lang.org/en/downloads/) 개발 환경을 갖추고 있다면, 다음과 같은 명령을 따라 새로운 Jekyll 사이트를 만들 수 있습니다:

{% highlight bash %}
# RubyGems을 통해 Jekyll과 Bundler 을 설치한다.
~ $ gem install jekyll bundler
# ./myblog 에 새로운 Jekyll 사이트를 만든다.
~ $ jekyll new myblog
# 새로 만들어진 디렉토리로 이동한다.
~ $ cd myblog

# 미리보기 서버로 사이트를 빌드한다.
~/myblog $ jekyll serve

# => 이제 http://localhost:4000 로 접속하면 된다.
{% endhighlight %}

만약 위 명령을 실행하다가 예기치 않은 문제가 발생했다면, [트러블슈팅](/docs/troubleshooting/) 페이지를 참고하거나 앞서 언급된 [준비물](/docs/installation/#준비물) 페이지를 참고하세요, 개발 헤더나 기타 전제 조건이 누락되었을 수 있습니다.

여기까진 별로 특별한 것이 없습니다. 하지만, 블로그 포스트를 작성한다거나
머리말을 사용해서 템플릿과 레이아웃을 조정할 때, Jekyll 의 다양한 환경설정
옵션들을 활용할 때, 진짜 마술같은 일이 벌어집니다.

만약 문제가 발생한다면, [준비물 설치][Installation]가 모두 올바르게 되어 있는지
확인해보세요.

## Bundler에 관해

`gem install jekyll bundler` 명령은 [RubyGems](https://rubygems.org/)을 통해 [jekyll](https://rubygems.org/gems/jekyll/) 과 [bundler](https://rubygems.org/gems/bundler) 젬을 설치합니다. 이 명령은 젬을 설치하기 위한 것으로 한번만 실행하면 됩니다. &mdash; 새로운 Jekyll 프로젝트를 만드는 경우가 아니라면. 자세한 내용은 다음을 참고하세요:

* `bundler`는 다른 Ruby의 젬들을 관리하기 위한 젬입니다. 각각의 젬들이 의존하는 모든 의존 관계를 따라 필요한 젬을 추적해서 젬과 젬의 버전 사이의 호환성을 유지하도록 해줍니다.
* `GemFile`과 `Gemfile.lock` 파일은 우리가 만드는 사이트가 필요로 하는 젬들을 Bundler에게 알려주는 역할을 합니다. 만약 사이트에 이 Gemfile들이 없는 상태라면, `bundle exec`를 생략하고 `jekyll serve`만으로 실행할 수 있습니다.
* `bundle exec jekyll serve`로 실행하면, Bundler는 `Gemfile.lock`에 명시된 젬과 그 버전을 사용해서 당신의 Jekyll 사이트를 어떤 의존성 충돌이나 호환되지 않는 일이 없이 빌드를 하게 됩니다.

## Jekyll로 새로운 사이트를 만들기 위한 옵션들

`jekyll new <경로>` 명령은 새로운 Jekyll 사이트를 지정한 경로(현재 디렉토리에 상대적임)에 만들어줍니다. 이 경우에, `myblog` 디렉토리에 설치하게 될 것입니다. 더 자세한 내용은 다음과 같습니다:

* 현재 디렉토리에 Jekyll 사이트를 만드려면, `jekyll new .` 명령을 실행하세요. 만약 현재 디렉토리가 비어 있지 않은 상태라면, `--force` 옵션을 넣어서 `jekyll new . --force` 명령으로 실행할 수 있습니다.
* `jekyll new` 명령은 자동으로 `bundle install` 을 실행해서 의존하는 젬들을 설치합니다. (만약 젬을 설치하기 위해 Bundler을 사용하고 싶지 않다면, `jekyll new myblog --skip-bundle`로 실행하세요.)
* 기본적으로, `jekyll new`로 설치된 Jekyll 사이트는 [Minima](https://github.com/jekyll/minima)라는 젬 기반의 테마를 사용하게 됩니다. 해당 테마-젬에 저장된 일부 디렉토리나 파일들은 감춰져 있을 수 있습니다.
* 저희는 젬 기반의 테마를 사용해 Jekyll을 설정하기를 권해드리지만 비어있는 사이트를 만들고 싶다면, `jekyll new myblog --blank` 명령을 사용하세요.
* `jekyll new` 에 포함된 다른 파라미터가 궁금하시면, `jekyll new --help` 명령을 사용하세요.

언제든지, <code>help</code> 명령을 사용해서 이용 가능한 모든 옵션이나 사용법을 확인할 수 있습니다, 이 명령은 <code>new</code>, <code>build</code>와 <code>serve</code> 같은 서브 커맨드에서도 동작합니다, 예를 들어 <code>jekyll help new</code> 또는 <code>jekyll help build</code>.
{: .note .info }

## 다음 단계

기본 테마를 가지고 Jekyll 사이트를 빌드하는 것은 그저 첫 단계에 불과합니다. 진정한 마법은 블로그 포스트를 등록하기 시작하면서, 템플릿이나 레이아웃을 제어할 목적으로 프론트매터를 사용하거나 Jekyll이 제공하는 멋진 설정 옵션들을 활용하면서 시작됩니다.