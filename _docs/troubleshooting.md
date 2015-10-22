---
layout: docs
title: 문제해결
permalink: /docs/troubleshooting/
---

여기 Jekyll 설치나 사용에 문제가 생겼을 때 도움이 될 만한 팁이 몇 가지 있습니다.
이 팁들로도 해결되지 않는 문제가 있다면, **[도움말 자료](/help/)**도
확인해보시기 바랍니다.

- [설치 관련 문제점](#installation-problems)
- [Jekyll 실행 관련 문제점](#problems-running-jekyll)
- [Base-URL 관련 문제점](#base-url-problems)
- [환경설정 관련 문제점](#configuration-problems)
- [마크업 관련 문제점](#markup-problems)

## 설치 관련 문제점

만약 Gem 설치 도중에 에러가 발생한다면, Ruby 2.0.0 확장 모듈의 컴파일링에 필요한
헤더파일들이 설치되어있지 않기 때문일 수 있습니다. Ubuntu 또는 Debian 에서의
설치 명령은 다음과 같습니다:

{% highlight bash %}
sudo apt-get install ruby2.0.0-dev
{% endhighlight %}

Red Hat 이나 CentOS, Fedora 에서는 다음과 같습니다:

{% highlight bash %}
sudo yum install ruby-devel
{% endhighlight %}

[NearlyFreeSpeech](https://www.nearlyfreespeech.net/) 에서는 Jekyll 을 설치하기 전에
다음 명령어를 실행해야 합니다:

{% highlight bash %}
export GEM_HOME=/home/private/gems
export GEM_PATH=/home/private/gems:/usr/local/lib/ruby/gems/1.8/
export PATH=$PATH:/home/private/gems/bin
export RB_USER_INSTALL='true'
{% endhighlight %}

Gentoo 에 RubyGems 를 설치하려면 다음 명령을 실행합니다:

{% highlight bash %}
sudo emerge -av dev-ruby/rubygems
{% endhighlight %}

Windows 에서는, [RubyInstaller
DevKit](https://wiki.github.com/oneclick/rubyinstaller/development-kit) 설치가 필요할 수도 있습니다.

맥 OS X 에서는, RubyGems 를 업데이트해야 할 수도 있습니다 (반드시 필요한 경우에만 `sudo` 와 함께 실행함):

{% highlight bash %}
sudo gem update --system
{% endhighlight %}

여전히 문제가 해결되지 않는다면, 이 명령으로 (`gcc` 같은) 새 명령행 도구를
다운로드하고 설치할 수 있으며,

{% highlight bash %}
xcode-select --install
{% endhighlight %}

그 다음, 이 명령으로 Native Gem 을 설치할 수 있게 됩니다
(반드시 필요한 경우에만 `sudo` 와 함께 실행함):

{% highlight bash %}
sudo gem install jekyll
{% endhighlight %}

맥 OS X 을 업그레이드 한다고 해서 Xcode 까지 자동으로 업그레이드 되지는 않는다는
것과 (Xcode 업그레이드는 App Store 에서 별도로 수행합니다), 최신 버전이 아닌
Xcode.app 은 앞서 설명한 명령행 도구와 충돌을 일으킬 수 있다는 점에 주의하기
바랍니다. 이런 문제가 발생한다면, Xcode 를 업그레이드 하고 최신 명령행 도구를
설치하세요.

### Jekyll &amp; 맥 OS X 10.11

시스템 무결성 보호 (System Integrity Protection) 기능의 도입으로 인해, 쓰기
권한이 있었던 몇몇 디렉토리들이 이제부터는 시스템 디렉토리로 인식되어 더 이상
사용할 수 없게 되었습니다. 이를 고려했을 때, 간편한 Jekyll 설치방법은 딱 두
가지로 정리됩니다. 첫 번째는 Gem 이 설치되는 위치를 변경하는 것입니다 (반드시
필요한 경우에만 `sudo` 와 함께 실행함):

{% highlight bash %}
sudo gem install -n /usr/local/bin jekyll
{% endhighlight %}

다른 방법은, Homebrew 를 설치해서 Ruby 를 관리하는 것입니다. Homebrew 설치
명령은 다음과 같습니다:

{% highlight bash %}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Homebrew 설치가 끝났으면, 나머지는 간단합니다:

{% highlight bash %}
brew install ruby
{% endhighlight %}

(더 많은 기능을 원하는) 고급 사용자들에게 도움이 될 만한 Jekyll 설치 방법은 Ruby
버전 관리자 ([RVM][], [rbenv][], [chruby][] 및 [기타][etc]) 를 하나 선택해 사용하는
것입니다.

[RVM]: https://rvm.io
[rbenv]: http://rbenv.org
[chruby]: https://github.com/postmodern/chruby
[etc]: https://github.com/rvm/rvm/blob/master/docs/alt.md

이 방법으로 Ruby 를 설치했다면, 다음과 같이 `$PATH` 변수를 수정하는 작업이
필요할 수도 있습니다:

{% highlight bash %}
export PATH=/usr/local/bin:$PATH
{% endhighlight %}

GUI 앱에서 `$PATH` 를 수정하는 방법은 다음과 같습니다:

{% highlight bash %}
launchctl setenv PATH "/usr/local/bin:$PATH"
{% endhighlight %}

이 방법들은 `/usr/local` 을 SIP 가 활성화 된 "안전한" 위치로 인식하여, Apple 에
내장된 Ruby 버전과의 충돌을 피하고, Jekyll 과 그 의존요소들을 샌드박스 환경에서
사용할 수 있게 해줍니다. 또 하나의 장점은 Gem 을 추가하거나 삭제할 때 `sudo` 를
입력할 필요가 없다는 것입니다.


### Could not find a JavaScript runtime. (ExecJS::RuntimeUnavailable)

만약 적절한 javaScript 실행환경이 없다면 `jekyll-coffeescript` 설치 단계에서
이와 같은 에러 메시지가 발생할 수 있습니다. 이 문제를 해결하려면, `execjs` 와
`therubyracer` gem 을 설치하거나 `nodejs` 를 설치해야 합니다. 더 자세한 내용은
[이슈 #2327](https://github.com/jekyll/jekyll/issues/2327) 을 확인해보세요.

## Jekyll 실행 관련 문제점

Debian 이나 Ubuntu 에서는, 터미널에서 `jekyll` 실행파일을 사용하기 위해
`/var/lib/gems/1.8/bin/` 을 `$PATH` 에 추가해야 할 수도 있습니다.

## Base-URL 관련 문제점

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

## 환경설정 관련 문제점

[환경설정](../configuration/)이 충돌하는 경우의 우선순위는 다음과 같습니다:


1. 명령행 플래그
2. 환경설정 파일
3. 디폴트값

한 마디로 정리하면 이런 뜻입니다: 환경설정 파일 `_config.yml` 에 설정된 옵션이
디폴트값 대신 사용되고, 명령행에 사용된 플래그들은 다른 모든 설정들보다
우선순위가 높습니다.

## 마크업 관련 문제점

Jekyll 에 사용된 마크업 엔진들의 종류는 다양하고, 각 엔진에는 저마다의
특이사항이 있을 수 있습니다. 동일한 문제를 겪고 있는 이들에게 도움이 될 만한
정보를 여기에 모아두었습니다.

### Liquid

최신 버전인 2.0 에서는, 템플릿에 사용하는 `{{ "{{" }}` 가 고장난 것 같습니다.
이전 버전과는 다르게, 2.0 에서 `{{ "{{" }}` 를 사용하면 다음과 같은 에러가
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
