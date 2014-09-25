---
layout: docs
title: 설치
prev_section: quickstart
next_section: usage
permalink: /docs/installation/
---

단 몇 분만에 Jekyll 설치와 실행 준비를 끝마칠 수 있습니다. 만약 골치 아픈 일이 발생한다면, 문제점에 대한 설명과 개선 방안을 [이슈로 등록]({{ site.repository }}/issues/new) (또는 Pull Request 제출)해 주시기 바랍니다.

### 필요한 것들

Jekyll 설치는 아주 쉽고 간단합니다. 하지만, 필요한 것들이 모두 준비되어 있는지 시작하기 전에 먼저 확인해보세요.

- [Ruby](http://www.ruby-lang.org/en/downloads/) (개발 패키지 포함)
- [RubyGems](http://rubygems.org/pages/download)
- 리눅스, 유닉스, 또는 맥 OS X
- [NodeJS](http://nodejs.org), 또는 다른 JavaScript 실행환경 (CoffeeScript 지원을 위하여).

<div class="note info">
  <h5>Windows 에서 Jekyll 실행하기</h5>
  <p>
    공식적으로 Windows 는 지원하지 않지만, 실행할 수는 있습니다.
    <a href="../windows/#installation">Windows 관련 문서 페이지</a>에서 그 방법을 찾을 수 있습니다.
  </p>
</div>

## RubyGems 로 설치하기

Jekyll 을 설치하는 가장 좋은 방법은 [RubyGems](http://rubygems.org/pages/download) 를 사용하는 것입니다. 터미널 프롬프트에서, 이 명령을 실행합니다:

{% highlight bash %}
$ gem install jekyll
{% endhighlight %}

이 명령으로 Jekyll 의 모든 gem 의존요소들이 자동으로 설치되기 때문에, 신경쓸 것은 전혀 없습니다. Jekyll 설치에 문제가 발생한다면, [문제해결](../troubleshooting/) 페이지를 확인해보거나 Jekyll 커뮤니티가 해당 문제를 개선할 수 있도록 [이슈로 등록]({{ site.repository }}/issues/new)해 주시기 바랍니다.

<div class="note info">
  <h5>Xcode Command-Line Tools 설치하기</h5>
  <p>
    맥 OS X 환경에서, Native extension 을 사용하는 Jekyll 의 의존요소 설치 시에 문제가 발생한다면, Xcode 및 그와 함께 제공되는 Command-Line Tools 를 설치해야 합니다. <code>Preferences &#8594; Downloads &#8594; Components</code> 에서 다운로드 하세요.
  </p>
</div>

## 예비 릴리스

예비 릴리스를 설치하려면, 필요한 것들이 모두 준비되었는지 확인한 후 다음 명령을 실행합니다:

{% highlight bash %}
gem install jekyll --pre
{% endhighlight %}

이 명령으로 최신 버전의 예비 릴리스가 설치됩니다. 만약 특정 버전의 예비 릴리스가 필요하다면 `-v` 스위치를 사용하여 설치하고자 하는 버전을 지정하세요:

{% highlight bash %}
gem install jekyll -v '2.0.0.alpha.1'
{% endhighlight %}

만약 개발 버전의 Jekyll 을 설치하고 싶다면, 약간의 절차가 더 필요합니다. 이렇게 하면 최신의 가장 뛰어난, 하지만 안정적이지 않을 수도 있는 기능을 사용할 수 있습니다.

{% highlight bash %}
$ git clone git://github.com/jekyll/jekyll.git
$ cd jekyll
$ script/bootstrap
$ bundle exec rake build
$ ls pkg/*.gem | head -n 1 | xargs gem install -l
{% endhighlight %}

## 부가 기능

Jekyll 은 다양한 (선택적) 부가기능을 지원하고 있습니다. 당신이 Jekyll 을 어떻게 사용할 것인가에 따라 원하는 기능을 골라서 설치하면 됩니다. 예를 들면, LaTeX 지원이나 다른 컨텐츠 렌더링 엔진을 사용할 수 있습니다. 더 자세한 내용은 [부가 기능 페이지](../extras/)를 확인해보세요.

<div class="note">
  <h5>ProTip™: 구문강조 활성화 하기</h5>
  <p>
    Jekyll 을 사용하는 친절한 당신이라면 <a href="http://pygments.org/">Pygments</a> 또는 <a href="https://github.com/jayferd/rouge">Rouge</a> 를 사용하여 구문 강조를 하고자 할 수도 있을 것입니다. 이 기능이 필요하다면, 반드시 <a href="../templates/#code-snippet-highlighting">활성화 방법</a>을 먼저 확인하세요.
  </p>
</div>

이제 필요한 것들이 모두 설치되었습니다. 시작해 봅시다!
