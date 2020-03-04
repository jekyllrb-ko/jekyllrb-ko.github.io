---
#title: Troubleshooting
title: 문제해결
permalink: /docs/troubleshooting/
---

<!--
If you ever run into problems installing or using Jekyll, here are a few tips
that might be of help. If the problem you’re experiencing isn’t covered below,
**please [check out our other help resources](/help/)** as well.
-->
여기 Jekyll 설치나 사용에 문제가 생겼을 때 도움이 될 만한 팁이 몇 가지 있습니다.
이 팁들로도 해결되지 않는 문제가 있다면, **[도움말 자료](/help/)**도
확인해보시기 바랍니다.

<!--
- [Installation Problems](#installation-problems)
- [Problems running Jekyll](#problems-running-jekyll)
- [Base-URL Problems](#base-url-problems)
- [Configuration problems](#configuration-problems)
- [Markup Problems](#markup-problems)
- [Production Problems](#production-problems)
-->
- [설치 관련 문제점](#installation-problems)
- [Jekyll 실행 관련 문제점](#problems-running-jekyll)
- [Base-URL 관련 문제점](#base-url-problems)
- [환경설정 관련 문제점](#configuration-problems)
- [마크업 관련 문제점](#markup-problems)
- [운영상 문제점](#production-problems)

<!--
## Installation Problems
-->
## 설치 관련 문제점 {#installation-problems}

<!--
If you encounter errors during gem installation, you may need to install
the header files for compiling extension modules for Ruby 2.x This
can be done on Ubuntu or Debian by running:
-->
만약 루비 젬을 설치하는 도중에 에러가 발생한다면, 루비 2.x 확장 모듈의
컴파일링에 필요한 헤더파일들이 설치되어있지 않기 때문일 수 있습니다.
우분투 또는 데비안 계열에서의 설치 명령은 다음과 같습니다:

```sh
sudo apt-get install ruby2.6-dev
```

<!--
On Red Hat, CentOS, and Fedora systems you can do this by running:
-->
레드햇이나 CentOS, 페도라에서는 다음과 같습니다:

```sh
sudo yum install ruby-devel
```

<!--
If you installed the above - specifically on Fedora 23 - but the extensions would still not compile, you are probably running a Fedora image that misses the `redhat-rpm-config` package. To solve this, run:
-->
위 내용대로 모두 설치했지만 - 특히 페도라 23 에서 - 확장기능이 여전히 컴파일되지 않는다면, 아마도 `redhat-rpm-config` 패키지가 포함되지 않은 페도라 이미지를 사용하고 있는 것일 수 있습니다. 이를 해결하려면, 아래와 같이 실행하세요:

```sh
sudo dnf install redhat-rpm-config
```

<!--
On Arch Linux you need to run:
-->
아치 리눅스에서는 이렇게 실행해야 합니다:

```sh
sudo pacman -S ruby-ffi
```

<!--
On Ubuntu if you get stuck after `bundle exec jekyll serve` and see error
messages like `Could not locate Gemfile` or `.bundle/ directory`, it's likely
because all requirements have not been fully met. Recent stock Ubuntu
distributions require the installation of both the `ruby` and `ruby-all-dev`
packages:
-->
우분투에서 `bundle exec jekyll serve` 를 실행한 후
`Could not locate Gemfile or .bundle/ directory` 라는 에러 메시지가 나온다면,
모든 필요조건이 만족되지 않았을 가능성이 높습니다.
최근의 우분투 배포판들은 `ruby` 와 `ruby-all-dev` 패키지를 모두
필요로 합니다:

```sh
sudo apt-get install ruby ruby-all-dev
```

<!--
On [NearlyFreeSpeech](https://www.nearlyfreespeech.net/) you need to run the
following commands before installing Jekyll:
-->
[NearlyFreeSpeech](https://www.nearlyfreespeech.net/) 에서는
Jekyll 을 설치하기 전에 다음 명령어를 실행해야 합니다:

```sh
export GEM_HOME=/home/private/gems
export GEM_PATH=/home/private/gems:/usr/local/lib/ruby/gems/1.8/
export PATH=$PATH:/home/private/gems/bin
export RB_USER_INSTALL='true'
```

<!--
To install RubyGems on Gentoo:
-->
젠투에 RubyGems 를 설치하려면 다음 명령을 실행합니다:

```sh
sudo emerge -av dev-ruby/rubygems
```

<!--
On Windows, you may need to install [RubyInstaller
DevKit](https://wiki.github.com/oneclick/rubyinstaller/development-kit).
-->
윈도우즈에서는, [RubyInstaller
DevKit](https://wiki.github.com/oneclick/rubyinstaller/development-kit) 를 설치해야할 수도 있습니다.

<!--
On Android (with Termux) you can install all requirements by running:
-->
안드로이드(의 Termux 환경)에서는 다음 명령으로 필요한 모든 것을 설치할 수 있습니다:

```sh
apt update && apt install libffi-dev clang ruby-dev make
```

<!--
On macOS, you may need to update RubyGems (using `sudo` only if necessary):
-->
맥OS 에서는, RubyGems 를 업데이트해야 할 수도 있습니다 (반드시 필요한 경우에만 `sudo` 와 함께 실행함):

```sh
gem update --system
```

<!--
If you still have issues, you can download and install new Command Line
Tools (such as `gcc`) using the following command:
-->
여전히 문제가 해결되지 않는다면, (`gcc` 같은) 새 명령행 도구를 설치하기 위해
다음 명령을 실행합니다:

```sh
xcode-select --install
```

<!--
which may allow you to install native gems using this command (again, using
`sudo` only if necessary):
-->
그 다음, 이 명령으로 Native 루비 젬을 설치할 수 있게 됩니다
(반드시 필요한 경우에만 `sudo` 와 함께 실행함):

```sh
gem install jekyll
```

<!--
Note that upgrading macOS does not automatically upgrade Xcode itself
(that can be done separately via the App Store), and having an out-of-date
Xcode.app can interfere with the command line tools downloaded above. If
you run into this issue, upgrade Xcode and install the upgraded Command
Line Tools.
-->
맥OS 을 업그레이드 한다고 해서 Xcode 까지 자동으로 업그레이드 되지는 않는다는
것과 (Xcode 업그레이드는 App Store 에서 별도로 수행합니다), 최신 버전이 아닌
Xcode.app 은 앞서 설명한 명령행 도구와 충돌을 일으킬 수 있다는 점에 주의하기
바랍니다. 이런 문제가 발생한다면, Xcode 를 업그레이드 하고 최신 명령행 도구를
설치하세요.

<!--
### Running Jekyll as Non-Superuser (no sudo!)
-->
### 관리자 권한 없이 Jekyll 실행하기 (No sudo!)
{: #no-sudo}

<!--
On most flavors of Linux, macOS, and Bash on Ubuntu on Windows, it is
possible to run Jekyll as a non-superuser and without having to install
gems to system-wide locations by adding the following lines to the end
of your `.bashrc` file:
-->
우분투와 윈도우즈의 Bash 환경과 리눅스, 맥OS 에서 가장 매력적인 점을
꼽아보면, `.bashrc` 파일에 다음 내용을 추가하면 시스템 관련 디렉토리에
루비 젬을 설치하지 않고 관리자가 아닌 일반 계정으로 Jekyll 을 실행할 수
있다는 사실입니다:

```
<!--
# Ruby exports
-->
# 루비 export 환경설정

export GEM_HOME=$HOME/gems
export PATH=$HOME/gems/bin:$PATH
```

<!--
This tells `gem` to place its gems within the user's home folder,
not in a system-wide location, and adds the local `jekyll` command to the
user's `PATH` ahead of any system-wide paths.
-->
이 설정으로 인해 `gem` 명령어는 시스템 관련 디렉토리가 아닌 사용자의 홈 폴더
내에 루비 젬을 설치하게 되고, 시스템 전역이 아닌 로컬의 실행파일
`jekyll` 이 우선적으로 선택되도록 사용자 `PATH` 를 구성합니다.

<!--
This is also useful for many shared webhosting services, where user accounts
have only limited privileges. Adding these exports to `.bashrc` before running
`gem install jekyll bundler` allows a complete non-`sudo` install of Jekyll.
-->
많은 공개 웹호스팅에서도, 그들이 제공하는 사용자 계정은 제한된 권한만을 가지고
있기 때문에, 이 설정이 유용하게 쓰입니다. 이 내용을 `.bashrc` 에 추가한 후
`gem install jekyll bundler` 를 실행하면 완전 `sudo` 없이 Jekyll 을 설치할 수 있습니다.

<!--
To activate the new exports, either close and restart Bash, logout and
log back into your shell account, or run `. .bashrc` in the
currently-running shell.
-->
이 설정을 적용하려면, Bash 를 종료하고 다시 실행하거나
자신의 쉘 계정으로 다시 로그인하거나
아니면 현재 실행중인 쉘 환경에서 `. .bashrc` 를 실행하세요.

<!--
If you see the following error when running the `jekyll new` command,
you can solve it by using the above-described procedure:
-->
만약 `jekyll new` 명령을 실행할 때 다음과 같은 에러가 발생한다면,
위에 설명한 내용으로 해결할 수 있습니다:

```sh
jekyll new test

Running bundle install in /home/user/test...

Your user account is not allowed to install to the system RubyGems.
You can cancel this installation and run:

    bundle install --path vendor/bundle

to install the gems into ./vendor/bundle/, or you can enter your password
and install the bundled gems to RubyGems using sudo.

Password:
```

<!--
Once this is done, the `jekyll new` command should work properly for
your user account.
-->
모든 절차를 끝마쳤다면, `jekyll new` 명령은 사용자 계정에서도 올바르게
작동할 것입니다.

<!--
### Jekyll &amp; macOS
-->
### Jekyll &amp; 맥OS

<!--
With the introduction of System Integrity Protection in v10.11, several directories
that were previously writable are now considered system locations and are no
longer available. Given these changes, there are a couple of simple ways to get
up and running. One option is to change the location where the gem will be
installed (again, using `sudo` only if necessary):
-->
맥OS 10.11 버전부터 시스템 무결성 보호 (System Integrity Protection) 기능이 도입되어, 쓰기
권한이 있었던 몇몇 디렉토리들이 이제부터는 시스템 디렉토리로 인식되어 더 이상
사용할 수 없게 되었습니다. 이를 고려했을 때, 간편한 Jekyll 설치방법은 딱 두
가지로 정리됩니다. 첫 번째는 루비 젬이 설치되는 위치를 변경하는 것입니다 (반드시
필요한 경우에만 `sudo` 와 함께 실행함):

```sh
gem install -n /usr/local/bin jekyll
```

<!--
Alternatively, Homebrew can be installed and used to set up Ruby. This can be
done as follows:
-->
다른 방법은, Homebrew 를 설치해서 루비를 관리하는 것입니다. Homebrew 설치
명령은 다음과 같습니다:

```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

<!--
Once Homebrew is installed, the second step is to run:
-->
Homebrew 설치가 끝났으면, 다음과 같이 실행합니다:

```sh
brew install ruby
```

<!--
Advanced users (with more complex needs) may find it helpful to choose one of a
number of Ruby version managers ([RVM][], [rbenv][], [chruby][], [etc][].) in
which to install Jekyll.
-->
(더 많은 기능을 원하는) 고급 사용자들에게 도움이 될 만한 Jekyll 설치
방법은 루비 버전 관리자 ([RVM][], [rbenv][], [chruby][] 및 [기타][etc])
를 하나 선택해 사용하는 것입니다.

[RVM]: https://rvm.io
[rbenv]: http://rbenv.org
[chruby]: https://github.com/postmodern/chruby
[etc]: https://github.com/rvm/rvm/blob/master/docs/alt.md

<!--
If you elect to use one of the above methods to install Ruby, it might be
necessary to modify your `$PATH` variable using the following command:
-->
이 방법으로 루비를 설치했다면, 다음과 같이 `$PATH` 변수를 수정하는 작업이
필요할 수도 있습니다:

```sh
export PATH=/usr/local/bin:$PATH
```

<!--
GUI apps can modify the `$PATH` as follows:
-->
GUI 앱에서 `$PATH` 를 수정하는 방법은 다음과 같습니다:

```sh
launchctl setenv PATH "/usr/local/bin:$PATH"
```

<!--
Either of these approaches are useful because `/usr/local` is considered a
"safe" location on systems which have SIP enabled, they avoid potential
conflicts with the version of Ruby included by Apple, and it keeps Jekyll and
its dependencies in a sandboxed environment. This also has the added
benefit of not requiring `sudo` when you want to add or remove a gem.
-->
이 방법들은 `/usr/local` 을 SIP 가 활성화 된 "안전한" 위치로 인식하여,
Apple 에 내장된 루비 버전과의 충돌을 피하고,
Jekyll 과 그 의존요소들을 샌드박스 환경에서 사용할 수 있게 해줍니다.
또 하나의 장점은 루비 젬을 추가하거나 삭제할 때 `sudo` 를 입력할 필요가
없다는 것입니다.

### Could not find a JavaScript runtime. (ExecJS::RuntimeUnavailable)

<!--
This error can occur during the installation of `jekyll-coffeescript` when
you don't have a proper JavaScript runtime. To solve this, either install
`execjs` and `therubyracer` gems, or install `nodejs`. Check out
[issue #2327](https://github.com/jekyll/jekyll/issues/2327) for more info.
-->
적절한 자바스크립트 런타임이 없으면 `jekyll-coffeescript` 설치 단계에서
이와 같은 에러 메시지가 발생할 수 있습니다. 이를 해결하기 위해서는,
루비 젬 `execjs` 와 `therubyracer` 를 설치하거나 `nodejs` 를 설치해야 합니다.
더 자세한 내용은 [2327번 이슈](https://github.com/jekyll/jekyll/issues/2327)를 확인해보세요.

<!--
## Problems running Jekyll
-->
## Jekyll 실행 관련 문제점 {#problems-running-jekyll}

<!--
On Debian or Ubuntu, you may need to add `/var/lib/gems/1.8/bin/` to your path
in order to have the `jekyll` executable be available in your Terminal.
-->
데비안 계열이나 우분투에서는, 터미널에서 `jekyll` 실행파일을 사용하기 위해
`/var/lib/gems/1.8/bin/` 을 `$PATH` 에 추가해야 할 수도 있습니다.

<!--
## Base-URL Problems
-->
## Base-URL 관련 문제점 {#base-url-problems}

<!--
If you are using base-url option like:
-->
다음과 같이 base-url 옵션을 사용할 경우:

```sh
jekyll serve --baseurl '/blog'
```

<!--
… then make sure that you access the site at:
-->
… 아래 주소로 접속하고 있는지 확인하세요:

```
http://localhost:4000/blog/index.html
```

<!--
It won’t work to just access:
-->
아래 주소로는 접근할 수 없을 것입니다:

```
http://localhost:4000/blog
```

<!--
## Configuration problems
-->
## 환경설정 관련 문제점 {#configuration-problems}

<!--
The order of precedence for conflicting [configuration settings](/docs/configuration/)
is as follows:
-->
[환경설정](/docs/configuration/)이 충돌하는 경우의 우선순위는 다음과
같습니다:

<!--
1. Command-line flags
2. Configuration file settings
3. Defaults
-->
1. 명령행 플래그
2. 환경설정 파일
3. 디폴트값

<!--
That is: defaults are overridden by options specified in `_config.yml`,
and flags specified at the command-line will override all other settings
specified elsewhere.
-->
한 마디로 정리하면 이런 뜻입니다: 환경설정 파일 `_config.yml` 에 설정된 옵션이
디폴트값 대신 사용되고, 명령행에 사용된 플래그들은 다른 모든 설정들보다
우선순위가 높습니다.

<!--
**Note: From v3.3.0 onward, Jekyll does not process `node_modules` and certain subdirectories within `vendor`, by default. But, by having an `exclude:` array defined explicitly in the config file overrides this default setting, which results in some users to encounter an error in building the site, with the following error message:**
-->
**메모: 버전 v3.3.0 부터는, `node_modules` 와 `vendor` 안의 몇몇 하위 디렉토리들은 처리하지 않는 것이 Jekyll 의 기본 동작방식입니다. 하지만 환경설정 파일에 `exclude:` 배열을 명시적으로 설정하여 이 기본 동작방식을 조정할 수 있는데, 이로 인해 몇몇 사용자들에게는 사이트 생성 시 다음과 같은 내용의 에러가 발생할 수도 있습니다:**

```sh
    ERROR: YOUR SITE COULD NOT BE BUILT:
    ------------------------------------
    Invalid date '<%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>':
    Document 'vendor/bundle/gems/jekyll-3.4.3/lib/site_template/_posts/0000-00-00-welcome-to-jekyll.markdown.erb'
    does not have a valid date in front matter.
```

<!--
Adding `vendor/bundle` to the `exclude:` list will solve this problem but will lead to having other sub-directories under `/vendor/` (and also `/node_modules/`, if present) be processed to the destination folder `_site`.
-->
그저 `vendor/bundle` 을 `exclude:` 목록에 추가하는 것만으로 이 문제를 해결할 수 있지만, `/vendor/` 의 하위 디렉토리들(존재하는 경우, `/node_modules/` 포함)도 최종 결과물 경로인 `_site` 안에 생성됩니다.


<!--
The proper solution is to incorporate the default setting for `exclude:` rather than override it completely:
-->
자신의 설정에 기본 `exclude:` 설정을 포함시키는 쪽이 완전히 덮어쓰는 방법보다 더 낫습니다:

<!--
For versions up to `v3.4.3`, the `exclude:` setting must look like following:
-->
버전 `v3.4.3` 까지, `exclude:` 설정은 다음과 같습니다:

```yaml
exclude:
  - Gemfile
  - Gemfile.lock
  - node_modules
  - vendor/bundle/
  - vendor/cache/
  - vendor/gems/
  - vendor/ruby/
  - any_additional_item # any user-specific listing goes at the end
```

<!--
From `v3.5` onward, `Gemfile` and `Gemfile.lock` are also excluded by default. So, in most cases there is no need to define another `exclude:` array in the config file. So an existing definition can either be modified as above, or removed completely, or commented out to enable easy edits in future.
-->
버전 `v3.5` 부터, 기본 설정으로 `Gemfile` 과 `Gemfile.lock` 도 제외됩니다. 따라서, 특별한 경우가 아닌 이상 환경설정 파일에 추가로 `exclude:` 배열을 정의할 필요가 없습니다. 또한 기본 설정에 이미 정의된 내용도 위와 같이 수정하거나, 아니면 완전히 제거하거나, 나중을 위해 주석 처리할 수 있습니다.


<!--
## Markup Problems
-->
## 마크업 관련 문제점 {#markup-problems}

<!--
The various markup engines that Jekyll uses may have some issues. This
page will document them to help others who may run into the same
problems.
-->
Jekyll 에 사용된 마크업 엔진들의 종류는 다양하고, 각 엔진에는 저마다의
특이사항이 있을 수 있습니다. 동일한 문제를 겪고 있는 이들에게 도움이 될 만한
정보를 여기에 모아두었습니다.

### Liquid

<!--
Liquid version 2.0 seems to break the use of `{{ "{{" }}` in templates.
Unlike previous versions, using `{{ "{{" }}` in 2.0 triggers the following error:
-->
Liquid 2.0 은 템플릿에 사용하는 `{{ "{{" }}` 가 고장난 것 같습니다.
이전 버전과는 다르게, 2.0 에서 `{{ "{{" }}` 를 사용하면 다음과 같은 에러가 발생합니다:

```sh
'{{ "{{" }}' was not properly terminated with regexp: /\}\}/  (Liquid::SyntaxError)
```

<!--
### Excerpts
-->
### 발췌

<!--
Since v1.0.0, Jekyll has had automatically-generated post excerpts. Since
v1.1.0, Jekyll also passes these excerpts through Liquid, which can cause
strange errors where references don't exist or a tag hasn't been closed. If you
run into these errors, try setting `excerpt_separator: ""` in your
`_config.yml`, or set it to some nonsense string.
-->
v1.0.0 이후부터, Jekyll 에 자동으로 생성된 포스트 발췌 기능이 있었습니다. v1.1.0
이후부터는, Jekyll 이 이 발췌를 Liquid 에 전달하게 되어 레퍼런스가 존재하지
않는다거나 태그가 올바르게 닫히지 않았다는 이상한 에러를 발생시킵니다. 이런
문제가 발생하면, `_config.yml` 에 `excerpt_separator: ""` 설정을 추가하거나
이상한 문자열로 설정해보세요.

<!--
## Production Problems
-->
## 운영상 문제점 {#production-problems}

<!--
If you run into an issue that a static file can't be found in your
production environment during build since v3.2.0 you should set your
[environment to `production`](/docs/configuration/environments/).
The issue is caused by trying to copy a non-existing symlink.
-->
버전 v3.2.0 이상에서 운영 환경을 구성할 때 파일이 제대로 생성되지
않는 이슈를 겪는다면
[환경설정을 `production`](/docs/configuration/environments/) 으로 지정해야 합니다.
이것은 존재하지 않는 심볼릭 링크를 복사하려하기 때문에 발생하는 이슈입니다.

<div class="note">
<!--
  <h5>Please report issues you encounter!</h5>
  <p>
  If you come across a bug, please <a href="{{ site.repository }}/issues/new">create an issue</a>
  on GitHub describing the problem and any work-arounds you find so we can
  document it here for others.
  </p>
-->
  <h5>문제를 발견하면 알려주세요!</h5>
  <p>
  만약 버그를 발견했다면, GitHub 에
  <a href="{{ site.repository }}/issues/new">이슈를 생성</a>해서 문제 상황과
  대처법을 설명해주세요. 다른 이들이 볼 수 있도록 이 문서에 포함하겠습니다.
  </p>
</div>
