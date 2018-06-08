---
#title: Installation
title: 설치
description: Official guide to install Jekyll on macOS, GNU/Linux or Windows.
permalink: /docs/installation/
---

<!--
Jekyll is a [Ruby Gem](http://guides.rubygems.org/rubygems-basics/), and can be
installed on most systems.
-->
Jekyll 은 단순히 하나의 [루비 젬](http://guides.rubygems.org/rubygems-basics/)일 뿐이고, 거의 모든 시스템에 설치가 가능합니다.

<!--
- [Requirements](#requirements)
- [Install Jekyll on macOS](#macOS)
- [Install Jekyll on Ubuntu Linux](#ubuntu)
- [Install Jekyll on Windows](../windows/)
- [Upgrade Jekyll](#upgrade-jekyll)
-->
- [준비물](#requirements)
- [맥OS 에 설치하기](#macOS)
- [우분투 리눅스에 설치하기](#ubuntu)
- [윈도우즈에 설치하기](../windows/)
- [업그레이드 하기](#upgrade-jekyll)

<!--
## Requirements
-->
## 준비물 {#requirements}

<!--
Before you start, make sure your system has the following:
-->
시작하기 전에, 자신의 시스템에 다음 것들이 준비되어 있는지 확인하세요:

<!--
- [Ruby](https://www.ruby-lang.org/en/downloads/) version 2.2.5 or above, including all development headers (ruby installation can be checked by running `ruby -v`)
- [RubyGems](https://rubygems.org/pages/download) (which you can check by running `gem -v`)
- [GCC](https://gcc.gnu.org/install/) and [Make](https://www.gnu.org/software/make/) (in case your system doesn't have them installed, which you can check by running `gcc -v`,`g++ -v`  and `make -v` in your system's command line interface)
-->
- [루비](https://www.ruby-lang.org/en/downloads/) 버전 2.2.5 또는 그 이상. 모든 개발환경 헤더 포함 (루비 설치정보는 `ruby -v` 로 확인할 수 있습니다)
- [RubyGems](https://rubygems.org/pages/download) (명령어 `gem -v` 로 확인할 수 있습니다)
- [GCC](https://gcc.gnu.org/install/) 와 [Make](https://www.gnu.org/software/make/) (명령행 인터페이스에서 `gcc -v` 와 `g++ -v`, `make -v` 로 확인할 수 있습니다)

<!--
## Install on macOS {#macOS}
-->
## 맥OS 에 설치하기 {#macOS}

<!--
We only cover macOS High Sierra 10.13 here, which comes with Ruby 2.3.3, older systems will need to [install a more recent Ruby version via Homebrew](#homebrew).
-->
여기서는 루비 2.3.3 이 함께 제공되는 맥OS High Sierra 10.13 를 기준으로 설명하며, 이전 버전의 시스템에서는 [Homebrew 로 상위버전 루비를 설치](#homebrew)할 필요가 있습니다.

<!--
First, you need to install the command-line tools to be able to compile native extensions, open a terminal and run:
-->
먼저, Native 확장기능을 컴파일할 수 있게 해주는 명령줄 도구를 설치해야 하므로, 터미널을 열어 다음 명령을 실행합니다:

```sh
xcode-select --install
```

<!--
### Set up Ruby included with the OS
-->
### 루비 환경 설정하기

<!--
Check your Ruby version meet our requirements:
-->
가지고 있는 루비 버전이 요구조건을 충족하는지 확인하세요:

```sh
ruby -v
2.3.3
```

<!--
Great, let's install Jekyll. We also need [Bundler](https://bundler.io/) to help us handle [plugins](../plugins) and [themes](../themes):
-->
좋습니다. 이제 Jekyll 을 설치합시다.  또 [Bundler](https://bundler.io/) 도 필요한데, [플러그인](../plugins)과 [테마](../themes)를 사용하기 위해 필요합니다:

```sh
gem install bundler jekyll
```

<!--
That's it, you're ready to go, either by installing our [default minimal blog theme](https://github.com/jekyll/minima) with `jekyll new jekyll-website` or by starting from scratch:
-->
끝났습니다. 이제 바로 사용할 수 있어요. `jekyll new jekyll-website` 로 [기본 블로그 테마](https://github.com/jekyll/minima)를 설치하거나 완전 처음부터 하나하나 시작할 수도 있습니다:

<!--
```sh
mkdir jekyll-website
cd jekyll-website

# Create a Gemfile
bundle init

# Add Jekyll
bundle add jekyll

# Install gems
bundle install
```
-->
```sh
mkdir jekyll-website
cd jekyll-website

# Gemfile 생성
bundle init

# Jekyll 추가
bundle add jekyll

# 루비 젬 설치
bundle install
```

<!--
Great, from there you can now either use a [theme](../themes/) or [create your own layouts](../templates/).
-->
좋습니다. 이제 [테마](../themes/)를 사용하거나 [자신만의 레이아웃을 생성](../templates/)할 수 있습니다.

<!--
### Install a newer Ruby version via Homebrew {#homebrew}
-->
### Homebrew 로 상위버전 루비 설치하기 {#homebrew}

<!--
If you wish to install the latest version of Ruby and get faster builds, we recommend to do it via [Homebrew](https://brew.sh) a handy package manager for macOS.
-->
빌드 속도가 더 빠른 최신 버전의 루비를 설치하고자 한다면, 편리한 맥OS 용 패키지 관리자인 [Homebrew](https://brew.sh) 를 사용하길 권합니다.

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install ruby
ruby -v
ruby 2.5.1p57 (2018-03-29 revision 63029) [x86_64-darwin17]
```

<!--
Yay! Now you have a shiny Ruby on your system!
-->
야호! 시스템에 아주 반짝반짝한 루비가 준비되었네요!

<!--
### Install multiple Ruby versions with rbenv {#rbenv}
-->
### rbenv 로 여러 버전의 루비 설치하기 {#rbenv}

<!--
Developers often use [rbenv](https://github.com/rbenv/rbenv) to manage multiple Ruby versions. This can be useful if you want to run the same Ruby version used by [GitHub Pages](https://pages.github.com/versions/) or [Netlify](https://www.netlify.com/docs/#ruby) for instance.
-->
개발자들은 여러 버전의 루비를 관리하기 위해 보통 [rbenv](https://github.com/rbenv/rbenv) 를 사용합니다. 하나 예를 들어보면, [GitHub Pages](https://pages.github.com/versions/) 나 [Netlify](https://www.netlify.com/docs/#ruby) 에서 사용되는 루비와 동일한 버전을 사용하고자 하는 경우 이게 아주 유용합니다.

<!--
```sh
# Install rbenv and ruby-build
brew install rbenv

# Setup rbenv integration to your shell
rbenv init

# Check your install
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```
-->
```sh
# rbenv 와 ruby-build 설치
brew install rbenv

# 자신의 쉘 환경에 rbenv 가 연동되도록 설정
rbenv init

# 설치결과 검사
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```

<!--
Restart your terminal for changes to take effect.
Now we can install the Ruby version of our choice, let's go with Ruby 2.5.1 here:
-->
터미널을 재시작하면 변경사항이 적용됩니다.
이제 원하는 버전의 루비를 설치할 수 있습니다. 아래처럼 루비 2.5.1 로 시작해봅시다:

```sh
rbenv install 2.5.1
rbenv global 2.5.1
ruby -v
ruby 2.5.1p57 (2018-03-29 revision 63029) [x86_64-darwin17]
```

<!--
That's it! Head over [rbenv command references](https://github.com/rbenv/rbenv#command-reference) to learn how to use different versions of Ruby in your projects.
-->
끝입니다! [rbenv 명령어 참고서](https://github.com/rbenv/rbenv#command-reference)를 한 번 잘 읽어보면 다양한 버전의 루비를 어떻게 프로젝트 별로 관리하는지 알 수 있습니다.

<div class="note info" markdown="1">

<!--
##### Problems installing Jekyll?
-->
##### Jekyll 설치에 문제가 발생했나요?

<!--
Check out the [troubleshooting](../troubleshooting/) page or
[ask for help on our forum](https://talk.jekyllrb.com).
-->
[문제해결](../troubleshooting/) 페이지를 읽어보거나
[포럼에 도움을 요청](https://talk.jekyllrb.com)하세요.

</div>

<!--
## Install on Ubuntu Linux {#ubuntu}
-->
## 우분투 리눅스에 설치하기 {#ubuntu}

<!--
Before we install Jekyll, we need to make sure we have all the required
dependencies.
-->
Jekyll 을 설치하기 전에, 의존관계에 있는 요구조건들을 모두 만족하는지
확인해야 합니다.

```sh
sudo apt-get install ruby ruby-dev build-essential
```

<!--
It is best to avoid installing Ruby Gems as the root user. Therefore, we need to
set up a gem installation directory for your user account. The following
commands will add environment variables to your `~/.bashrc` file to configure
the gem installation path. Run them now:
-->
루비 젬은 root 사용자로 설치하지 않는게 좋습니다. 그러므로, 일반
사용자 계정에 루비 젬 설치 디렉토리를 따로 설정해주어야 합니다. 아래
명령어는 루비 젬 설치 경로를 가리키는 환경설정 변수를 `~/.bashrc` 파일에
추가할 것입니다. 실행해보세요:

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME=$HOME/gems' >> ~/.bashrc
echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

<!--
Finally, install Jekyll:
-->
마지막으로, Jekyll 을 설치합니다:

```sh
gem install jekyll bundler
```

<!--
That's it! You're ready to start using Jekyll.
-->
끝났습니다! 당신은 이제 Jekyll 을 사용할 수 있습니다.

<!--
## Upgrade Jekyll
-->
## 업그레이드 하기 {#upgrade-jekyll}

<!--
Before you start developing with Jekyll, you may want to check that you're up to date with the latest version. To find the currently installed version of Jekyll, run one of these commands:
-->
Jekyll 개발에 참여하기 전에, 자신이 현재 최신 버전을 사용하고 있는지 확인하고 싶을 수도 있습니다. 현재 설치된 Jekyll 의 버전을 확인하려면, 이 명령어들 중 하나를 실행하세요:

```sh
jekyll --version
gem list jekyll
```

<!--
You can use RubyGems to find [the current version of Jekyll](https://rubygems.org/gems/jekyll). Another way to check if you have the latest version is to run the command `gem outdated`. This will provide a list of all the gems on your system that need to be updated. If you aren't running the latest version, run this command:
-->
RubyGems 를 사용해서 [Jekyll 의 최신 버전](https://rubygems.org/gems/jekyll)을 확인할 수 있습니다. 다른 방법으로는 `gem outdated` 명령을 실행해볼 수도 있습니다. 이 명령은 당신의 시스템에 설치된 루비 젬들 중 업데이트가 필요한 것들의 목록을 보여줍니다. 가지고 있는 버전이 최신 버전이 아니라면, 이 명령을 실행하세요:

```sh
bundle update jekyll
```

<!--
Alternatively, if you don't have Bundler installed run:
-->
Bundler 가 설치되어있지 않은 경우에는, 대신 다음과 같이 실행하세요:

```sh
gem update jekyll
```

<!--
To upgrade to latest Rubygems, run:
-->
Rubygems 를 최신 버전으로 업그레이드 하려면, 이렇게 실행하세요:

```
gem update --system
```

<!--
Refer to our [upgrading section](../upgrading/) to upgrade from Jekyll 2.x or 1.x.
-->
Jekyll 2.x 나 1.x 에서부터 업그레이드하는 경우에는 [업그레이드 페이지](../upgrading/)를 참고하세요.

<!--
## Pre-releases
-->
## 프리릴리스 버전

<!--
In order to install a pre-release, make sure you have all the requirements
installed properly and run:
-->
프리릴리스 버전을 설치하려면, 모든 준비물이 올바르게 설치되었는지 확인한 후
다음 명령을 실행합니다:

```sh
gem install jekyll --pre
```

<!--
This will install the latest pre-release. If you want a particular pre-release,
use the `-v` switch to indicate the version you'd like to install:
-->
이 명령으로 가장 최신의 프리릴리스 버전이 설치됩니다. 만약 프리릴리스 중에서도
특정 버전이 필요하다면 `-v` 스위치를 사용하여 설치하려는 버전을 지정하세요:

```sh
gem install jekyll -v '2.0.0.alpha.1'
```

<!--
If you'd like to install a development version of Jekyll, the process is a bit
more involved. This gives you the advantage of having the latest and greatest,
but may be unstable.
-->
만약 개발 버전의 Jekyll 을 설치해보고 싶다면, 몇 가지 절차가 좀 더 필요합니다.
이를 통해 가장 뛰어난 최신의 기능들을 사용할 수 있게 됩니다만, 불안정할 수도
있습니다.


```sh
git clone git://github.com/jekyll/jekyll.git
cd jekyll
script/bootstrap
bundle exec rake build
ls pkg/*.gem | head -n 1 | xargs gem install -l
```

<!--
Now that you’ve got everything up-to-date and installed, let’s get to work!
-->
이제 필요한 모든 것들이 최신 버전으로 설치되었군요. 시작해봅시다!
