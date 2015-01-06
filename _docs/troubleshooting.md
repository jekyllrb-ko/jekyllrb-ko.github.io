---
layout: docs
title: 문제해결
prev_section: deployment-methods
next_section: sites
permalink: /docs/troubleshooting/
---

Jekyll 설치나 사용에 문제가 생겼을 때 도움이 될 만한
몇 가지 팁이 여기 있습니다. 이 팁들로도 해결되지 않는 문제가 있다면,
Jekyll 커뮤니티에서 조치할 수 있도록 [이슈를
등록]({{site.help_url}}/issues/new)해 주세요.

- [Installation Problems](#installation-problems)
- [Problems running Jekyll](#problems-running-jekyll)
- [Base-URL Problems](#base-url-problems)
- [Configuration problems](#configuration-problems)
- [Markup Problems](#markup-problems)

## 설치 시 문제점

만약 Gem 설치 시 에러가 발생한다면,
루비 1.9.1 컴파일 확장기능 모듈의 헤더 파일이 필요한 것일 수 있습니다.
우분투 또는 데비안에서는 다음 명령을 실행합니다:

{% highlight bash %}
sudo apt-get install ruby1.9.1-dev
{% endhighlight %}

레드햇이나 CentOS, 페도라에서는 다음과 같이 실행합니다:

{% highlight bash %}
sudo yum install ruby-devel
{% endhighlight %}

[NearlyFreeSpeech](http://nearlyfreespeech.net/) 에서는 Jekyll 을 설치하기 전에
다음 명령어를 실행해야 합니다:

{% highlight bash %}
export GEM_HOME=/home/private/gems
export GEM_PATH=/home/private/gems:/usr/local/lib/ruby/gems/1.8/
export PATH=$PATH:/home/private/gems/bin
export RB_USER_INSTALL='true'
{% endhighlight %}

OSX 에서는, RubyGems 업데이트가 필요할 수도 있습니다:

{% highlight bash %}
sudo gem update --system
{% endhighlight %}

여전히 문제가 해결되지 않는다면, [XCode 의 명령행 도구를
설치](http://www.zlu.me/ruby/os%20x/gem/mountain%20lion/2012/02/21/install-native-ruby-gem-in-mountain-lion-preview.html)해야
할 수도 있습니다. 이 도구를 설치하면, 다음 명령으로 Native Gem 을 설치할 수 있습니다:

{% highlight bash %}
sudo gem install jekyll
{% endhighlight %}

Gentoo 에 RubyGems 를 설치하려면 다음 명령을 실행합니다:

{% highlight bash %}
sudo emerge -av dev-ruby/rubygems
{% endhighlight %}

윈도우즈에서는 [RubyInstaller
DevKit](https://wiki.github.com/oneclick/rubyinstaller/development-kit) 을 설치해야 할 수도 있습니다.

### Could not find a JavaScript runtime. (ExecJS::RuntimeUnavailable)

만약 적절한 javaScript 실행환경이 없다면 `jekyll-coffeescript` 설치 단계에서
이와 같은 에러 메시지가 발생할 수 있습니다. 이 문제를 해결하려면, `execjs` 와
`therubyracer` gem 을 설치하거나 `nodejs` 를 설치해야 합니다. 더 자세한 내용은
[이슈 #2327](https://github.com/jekyll/jekyll/issues/2327) 을 확인해보세요.

## Jekyll 실행 시 문제점

데비안이나 우분투에서는, 터미널에서 `jekyll` 실행파일을 사용하기 위해서
`/var/lib/gems/1.8/bin/` 을 `$PATH` 에 추가해야 할 수도 있습니다.

## Base-URL 문제점

다음과 같이 base-url 옵션을 사용할 경우:

{% highlight bash %}
jekyll serve --baseurl '/blog'
{% endhighlight %}

… 아래 주소로 접속하고 있는지 확인하세요:

{% highlight bash %}
http://localhost:4000/blog/index.html
{% endhighlight %}

아래 주소로는 접근할 수 없을 것입니다:

{% highlight bash %}
http://localhost:4000/blog
{% endhighlight %}

## 환경설정 문제점

[환경설정](../configuration/)의 우선순위는 다음과 같습니다:


1.  명령행 플래그
2.  환경설정 파일
3.  기본값

다시 말해: `_config.yml` 에 설정된 옵션이 기본값 대신 사용되고,
명령행에 사용된 플래그들이 다른 모든 설정들보다 우선순위가 높습니다.


## 마크업 문제점

다양한 마크업 엔진들이 Jekyll 에 사용되고 있으며, 각 엔진만의 문제점이 있을 수
있습니다. 동일한 문제를 겪고 있는 이들에게 도움이 될 만한 정보를 이 페이지에
모아두었습니다.

### Maruku

링크에 이스케이프해야 할 문자가 포함되어 있다면,
다음 문법을 사용하세요:

{% highlight text %}
![Alt text](http://yuml.me/diagram/class/[Project]->[Task])
{% endhighlight %}

Maruku 는 `<script src="js.js"></script>` 와 같은 비어있는 태그를 `<script
src="js.js" />` 로 변환시킵니다. 이것은 Firefox 에서 문제를 일으키며 다른
브라우저에서도 문제가 될 가능성이 있습니다. 또, [XHTML
관례](http://www.w3.org/TR/xhtml1/#C_3)에 위반됩니다. 간단한 해결방법으로는 여는
태그와 닫는 태그 사이에 공백을 넣는 것입니다.

### Liquid

최신 버전인 2.0 에서는, 템플릿 안의 `{{ "{{" }}` 가 고장난 것 같습니다. 이전
버전과는 다르게, 2.0 에서 `{{ "{{" }}` 를 사용하면 다음과 같은 에러가
발생합니다:

{% highlight bash %}
'{{ "{{" }}' was not properly terminated with regexp: /\}\}/  (Liquid::SyntaxError)
{% endhighlight %}

### 발췌

v1.0.0 이후부터, Jekyll 에 자동으로 생성된 포스트 발췌 기능이 있었습니다. v1.1.0
이후부터는, Jekyll 이 이 발췌를 Liquid 에 전달하게 되어 레퍼런스가 존재하지
않는다거나 태그가 올바르게 닫히지 않았다는 이상한 에러를 발생시킵니다. 이런
문제가 발생하면, `_config.yml` 에 `excerpt_separator: ""` 설정을 추가하거나
이상한 문자열로 설정해보세요.

<div class="note">
  <h5>문제를 발견하면 알려주세요!</h5>
  <p>
  만약 버그를 발견했다면, GitHub 에
  <a href="{{ site.help_url }}/issues/new">이슈를 생성</a>해서 문제 상황과
  대처법을 설명해주세요. 다른 이들이 볼 수 있도록 이 문서에 포함하겠습니다.
  </p>
</div>
