---
#title: Jekyll on macOS
title: 맥OS 에 Jekyll 설치
permalink: /docs/installation/macos/
---

<!--
## Install Command Line Tools
-->
## Command Line Tools 설치
<!--
First, you need to install the command-line tools to be able to compile native extensions, open a terminal and run:
-->
먼저, Native 확장기능을 컴파일할 수 있게 해주는 명령행 도구를 설치해야 하므로, 터미널을 열어 다음 명령을 실행합니다:

```sh
xcode-select --install
```

<!--
## Install Ruby
-->
## 루비 설치

<!--
Jekyll requires **Ruby > {{ site.data.ruby.min_version }}**.
macOS Catalina 10.15 comes with ruby 2.6.3, so you're fine.
If you're running a previous macOS system, you'll have to install a newer version of Ruby.
-->
Jekyll 은 **루비 > {{ site.data.ruby.min_version }}** 버전을 필요로 합니다.
맥OS 카탈리나 10.15 는 루비 2.6.3 이 기본 포함되어 있으므로 아무런 문제가 없습니다.
이전 버전의 맥OS 시스템을 사용중이라면, 새로운 버전의 루비를 설치해야 합니다.

<!--
### With Homebrew {#brew}
-->
### Homebrew 사용 {#brew}
<!--
To run the latest Ruby version you need to install it through [Homebrew](https://brew.sh).
-->
최신 버전의 루비를 [Homebrew](https://brew.sh) 로 설치할 수 있습니다.

<!--
```sh
# Install Homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install ruby
```
-->
```sh
# Homebrew 설치
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install ruby
```

<!--
Add the brew ruby path to your shell config:
-->
Homebrew 루비의 경로를 쉘 환경설정에 추가합니다:

```bash
echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile
```

<!--
Then relaunch your terminal and check your updated Ruby setup:
-->
이제 터미널을 재시작하여 추가한 루비 설정을 확인합니다:

```sh
which ruby
# /usr/local/opt/ruby/bin/ruby

ruby -v
{{ site.data.ruby.current_version_output }}
```

<!--
Yay, we are now running current stable Ruby!
-->
야호, 안정적인 버전의 루비가 작동하고 있어요!

<!--
### With rbenv {#rbenv}
-->
### rbenv 사용 {#rbenv}

<!--
People often use [rbenv](https://github.com/rbenv/rbenv) to manage multiple
Ruby versions. This is very useful when you need to be able to run a given Ruby version on a project.
-->
많은 사람들이 [rbenv](https://github.com/rbenv/rbenv) 로 여러 버전의 루비를
관리합니다. 각각의 프로젝트마다 다른 버전의 루비를 실행해야 할 때 아주 유용합니다.

<!--
```sh
# Install Homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# Install rbenv and ruby-build
brew install rbenv

# Set up rbenv integration with your shell
rbenv init

# Check your installation
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
```
-->
```sh
# Homebrew 설치
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# rbenv 와 ruby-build 설치
brew install rbenv

# 쉘 환경에 rbenv 가 연동되도록 설정
rbenv init

# 설치상태 검사
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash
```

<!--
Restart your terminal for changes to take effect.
Now you can install the Ruby version of our choice, let's go with current latest stable Ruby:
-->
터미널을 재시작하면 변경사항이 적용됩니다.
이제 원하는 버전의 루비를 설치할 수 있습니다. 최신 버전의 루비를 사용해봅시다:

```sh
rbenv install {{ site.data.ruby.current_version }}
rbenv global {{ site.data.ruby.current_version }}
ruby -v
{{ site.data.ruby.current_version_output }}
```

<!--
That's it! Head over [rbenv command references](https://github.com/rbenv/rbenv#command-reference) to learn how to use different versions of Ruby in your projects.
-->
끝났습니다! [rbenv 명령어 참고서](https://github.com/rbenv/rbenv#command-reference)를 읽어보면 다양한 버전의 루비를 프로젝트별로 관리하는 방법을 배울 수 있습니다.

<!--
## Install Jekyll
-->
## Jekyll 설치

<!--
Now all that is left is installing [Bundler](/docs/ruby-101/#bundler) and Jekyll.
-->
이제 남은 것은 [Bundler](/docs/ruby-101/#bundler) 와 Jekyll 을 설치하는 것 뿐입니다.

<!--
### Local Install
-->
### 로컬 설치

```sh
gem install --user-install bundler jekyll
```

<!--
and then get your Ruby version using
-->
그리고 설치된 루비 버전을 확인하려면

```sh
ruby -v
{{ site.data.ruby.current_version_output }}
```

<!--
Then append your path file with the following, replacing the `X.X` with the first two digits of your Ruby version.
-->
이제 아래 내용을 쉘 환경에 추가하는데, `X.X` 부분에는 설치된 루비 버전의 처음 두 숫자를 넣습니다.

```bash
echo 'export PATH="$HOME/.gem/ruby/X.X.0/bin:$PATH"' >> ~/.bash_profile
```

<!--
To check that your gem paths point to your home directory run:
-->
젬 경로가 홈 디렉토리를 가리키고 있는지 확인하려면 이 명령을 실행합니다:

```sh
gem env
```

<!--
And check that `GEM PATHS:` points to a path in your home directory.
-->
그리고 `GEM PATHS:` 가 홈 디렉토리 내의 경로를 가리키고 있는지 확인합니다.

{: .note .info}
<!--
Every time you update Ruby to a version with a different first two digits, you will need to update your path to match.
-->
루비를 업데이트하여 버전의 처음 두 숫자가 바뀌었다면, 환경설정을 수정하여 올바른 경로를 가리키도록 해야합니다.

<!--
### Global Install
-->
### 글로벌 설치

{: .note .warning}
<!--
We strongly recommend against installing Ruby gems globally to avoid file permissions problems and using `sudo`.
-->
파일 권한 문제와 `sudo` 사용을 피하기 위해서, 루비 젬을 시스템 경로에 설치하는 것은 권장하지 않습니다.

<!--
#### On Mojave (10.14)
-->
#### Mojave 버전 (10.14) 

<!--
Because of SIP Protections in Mojave, you must run:
-->
Mojave 의 시스템 무결성 보호 (SIP) 기능 때문에, 다음과 같이 실행해야 합니다:

```sh
sudo gem install bundler
sudo gem install -n /usr/local/bin/ jekyll
```

<!--
#### Before Mojave (<10.14)
-->
#### Mojave 버전 이전 (<10.14) 

<!--
You only have to run:
-->
다음과 같이 실행하면 됩니다:

```sh
sudo gem install bundler jekyll
```

<!--
## Problems?
-->
## 문제가 발생했나요?

<!--
Check out the [troubleshooting](/docs/troubleshooting/) page or [ask for help on our forum](https://talk.jekyllrb.com).
-->
[문제해결](/docs/troubleshooting/) 페이지를 읽어보거나 [포럼에 도움을 요청](https://talk.jekyllrb.com)하세요.
