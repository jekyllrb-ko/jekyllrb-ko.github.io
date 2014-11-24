---
layout: docs
title: 설치
prev_section: quickstart
next_section: usage
permalink: /docs/installation/
---

Jekyll 을 설치하고 실행을 준비하는 것은 단 몇 분밖에 안 걸립니다.
만약 무언가 골치 아픈 일이 발생한다면, 문제점에 대한 설명과 개선 방안을 [이슈로
등록]({{ site.repository }}/issues/new) (또는 Pull Request 를 제출) 해 주시기
바랍니다.

### 준비물

Jekyll 설치는 아주 쉽고 단순합니다만, 시작하기 전에 먼저 확인해야 할 준비물이 몇
가지 있습니다.

- [Ruby](http://www.ruby-lang.org/en/downloads/)
  (개발 패키지 포함)
- [RubyGems](http://rubygems.org/pages/download)
- 리눅스, 유닉스, 또는 맥 OS X
- [NodeJS](http://nodejs.org), 또는 다른 JavaScript 실행환경 (CoffeeScript
  지원에 필요함).

<div class="note info">
  <h5>Windows 에서 Jekyll 실행하기</h5>
  <p>
    Windows 는 공식적으로 지원하지 않지만, 실행은 가능합니다. 방법은
    <a href="../windows/#installation">Windows 관련 문서 페이지</a>에서 찾을 수
    있습니다.
  </p>
</div>

## RubyGems 로 설치하기

Jekyll 을 설치하는 가장 좋은 방법은
[RubyGems](http://rubygems.org/pages/download) 를 사용하는 것입니다. 터미널
프롬프트에서, 이 명령을 실행합니다:

{% highlight bash %}
$ gem install jekyll
{% endhighlight %}

이 명령 하나로 Jekyll 의 모든 gem 의존요소들이 자동적으로 설치되기 때문에,
별도로 신경쓸 것은 전혀 없습니다. 만약 Jekyll 설치중에 문제가 발생한다면,
[문제해결](../troubleshooting/) 페이지를 확인해보거나 [이슈로
등록]({{ site.repository }}/issues/new)해서 Jekyll 커뮤니티가 해당 문제를 개선할
수 있도록 도와주시기 바랍니다.

<div class="note info">
  <h5>Xcode Command-Line Tools 설치하기</h5>
  <p>
    맥 OS X 환경에서, Native extension 을 사용하는 Jekyll 의 의존요소 설치 시에
    문제가 발생한다면, Xcode 및 그와 함께 제공되는 Command-Line Tools 를
    설치해야 합니다. <code>Preferences &#8594; Downloads &#8594; Components</code>
    에서 다운로드 하세요.
  </p>
</div>

## 예비-출시(Pre-release) 버전

예비-출시 버전을 설치하려면, 준비물이 모두 올바르게 설치되었는지 확인한 후
다음 명령을 실행합니다:

{% highlight bash %}
gem install jekyll --pre
{% endhighlight %}

이 명령으로 가장 최신의 예비-출시 버전이 설치됩니다. 만약 예비-출시의 특정
버전이 필요하다면 `-v` 스위치를 사용하여 설치하려는 버전을 지정하세요:

{% highlight bash %}
gem install jekyll -v '2.0.0.alpha.1'
{% endhighlight %}

만약 개발 버전의 Jekyll 을 설치하고 싶다면, 약간의 절차가 더 추가됩니다.
이것으로 가장 최신의, 가장 뛰어난 기능을 사용할 수 있지만, 불안정할 수도
있습니다.

{% highlight bash %}
$ git clone git://github.com/jekyll/jekyll.git
$ cd jekyll
$ script/bootstrap
$ bundle exec rake build
$ ls pkg/*.gem | head -n 1 | xargs gem install -l
{% endhighlight %}

## 부가 기능

Jekyll 은 다양한 (선택적) 부가기능을 지원하고 있습니다. 당신이 Jekyll 을 어떻게
사용할 것인가에 따라 필요한 기능을 골라서 설치하면 됩니다. LaTeX 지원이나 다른
컨텐츠 렌더링 엔진 등을 예로 들 수 있습니다. 더 자세한 내용은 [부가 기능
페이지](../extras/)를 확인해보세요.

<div class="note">
  <h5>ProTip™: 구문 강조 기능을 사용하세요</h5>
  <p>
    Jekyll 을 사용하는 당신과 같은 사람에게는, <a href="http://pygments.org/">Pygments</a> 또는
    <a href="https://github.com/jayferd/rouge">Rouge</a> 를 사용한 구문 강조
    기능이 필요할 수도 있습니다. 필요하다면 꼭 한번 이 기능을
    <a href="../templates/#code-snippet-highlighting">사용하는 방법을 확인</a>
    해보세요.
  </p>
</div>

이제 필요한 것들이 모두 설치되었습니다. 시작해 봅시다!
