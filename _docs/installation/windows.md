---
#title: Jekyll on Windows
title: 윈도우즈에서의 Jekyll
permalink: /docs/installation/windows/
redirect_from:
  - /docs/windows/
---

<!--
While Windows is not an officially-supported platform, it can be used to run Jekyll with the proper tweaks. This page aims to
collect some of the general knowledge and lessons that have been unearthed by Windows users.
-->
윈도우즈가 공식적으로 지원되는 플랫폼은 아니지만, 몇 가지만 손보면 Jekyll 을 실행할 수 있습니다. 이 페이지의 목적은
윈도우즈 사용자에 의해서 발굴된 정보들을 모아두는 것입니다.

<!--
## Installing Jekyll
-->
## Jekyll 설치하기

<!--
### Installation via RubyInstaller
-->
### RubyInstaller 를 통한 설치

<!--
The easiest way to run Jekyll is by using the [RubyInstaller](https://rubyinstaller.org/) for Windows.
-->
가장 쉬운 방법은 [RubyInstaller](https://rubyinstaller.org/) for Windows 를 사용하는 것입니다.

<!--
RubyInstaller is a self-contained Windows-based installer that includes the Ruby language, an execution environment,
important documentation, and more.
We only cover RubyInstaller-2.4 and newer here, older versions need to
[install the Devkit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit) manually.
-->
RubyInstaller 는 윈도우즈 기반으로 루비 언어와 실행 환경, 중요 문서
등을 포함하고 있습니다.
여기서는 RubyInstaller-2.4 또는 그 이상의 버전을 다루고 있으며, 예전 버전은
따로 [Devkit 설치](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit)를 필요로 합니다.

<!--
1. Download and Install a **Ruby+Devkit** version from [RubyInstaller Downloads](https://rubyinstaller.org/downloads/).
   Use default options for installation.
2. Run the `ridk install` step on the last stage of the installation wizard. This is needed for installing gems with native
   extensions. You can find additional information regarding this in the
   [RubyInstaller Documentation](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system)
3. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective.
   Install Jekyll and Bundler via: `gem install jekyll bundler`
4. Check if Jekyll installed properly: `jekyll -v`
-->
1. [RubyInstaller 다운로드 페이지](https://rubyinstaller.org/downloads/)에서 **Ruby+Devkit** 버전을 다운로드 받아 설치하세요.
   설치 시 기본 옵션을 사용하세요.
2. 설치 마법사의 마지막 단계에서 `ridk install` 절차를 수행하세요. Native 확장기능으로 젬을 설치하기 위해 필요한
   절차입니다. 이에 관련된 추가 정보는
   [RubyInstaller 문서](https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system)에서 찾을 수 있습니다.
3. 시작 메뉴에서 명령 프롬프트 창을 열고, 환경변수 `PATH` 를 적절히 설정하세요.
   Jekyll 과 Bundler 를 설치합니다: `gem install jekyll bundler`
4. Jekyll 이 올바르게 설치되었는지 확인합니다: `jekyll -v`

<!--
That's it, you're ready to use Jekyll!
-->
끝났습니다. 이제 Jekyll 을 사용할 수 있습니다!

<!--
### Installation via Bash on Windows 10
-->
### 윈도우즈 10 에서 Bash 를 통한 설치

<!--
If you are using Windows 10 version 1607 or later, another option to run Jekyll is by
[installing](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide) the Windows Subsystem for Linux.
-->
버전 1607 또는 그 이상의 윈도우즈 10 을 사용중인 상황에서, Jekyll 을 사용하는 또 다른 방법은
Windows Subsystem for Linux 를 [설치](https://msdn.microsoft.com/en-us/commandline/wsl/install_guide)하는 것입니다.

<!--
*Note:* You must have [Windows Subsystem for Linux](https://msdn.microsoft.com/en-us/commandline/wsl/about) enabled.
-->
*중요:* 반드시 [Windows Subsystem for Linux](https://msdn.microsoft.com/en-us/commandline/wsl/about) 가 활성화되어 있어야 합니다.

<!--
First let's make sure all our packages / repositories are up to date. Open a new Command Prompt instance, and type the following:
-->
모든 패키지 / 저장소의 정보가 최신인지 먼저 확인합시다. 새 명령어 프롬프트를 열고, 다음과 같이 입력합니다:

```sh
bash
```
<!--
Your Command Prompt instance should now be a Bash instance. Now we must update our repo lists and packages.
-->
명령어 프롬프트가 Bash 로 바뀌게 됩니다. 이제 저장소 목록과 패키지를 업데이트해야 합니다.

```sh
sudo apt-get update -y && sudo apt-get upgrade -y
```
<!--
Now we can install Ruby. To do this we will use a repository from [BrightBox](https://www.brightbox.com/docs/ruby/ubuntu/),
which hosts optimized versions of Ruby for Ubuntu.
-->
이제 루비를 설치할 수 있습니다. 여기서 우리는 우분투에 최적화된 버전의 루비를 제공하는 [BrightBox](https://www.brightbox.com/docs/ruby/ubuntu/)
의 저장소를 사용할 것입니다.

```sh
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.5 ruby2.5-dev build-essential dh-autoreconf
```

<!--
Next let's update our Ruby gems:
-->
이제 루비 젬들을 업데이트합시다:

```sh
gem update
```

<!--
Now all that is left to do is install Jekyll.
-->
이제 남은것은 Jekyll 을 설치하는 것 뿐입니다.

```sh
gem install jekyll bundler
```

<!--
(*Note: no `sudo` here.*)
-->
(*중요: `sudo` 사용 안함.*)
<!--
Check if Jekyll installed properly by running:
-->
다음 명령으로 Jekyll 이 올바르게 설치되었는지 확인합니다:

```sh
jekyll -v
```

<!--
**And that's it!**
-->
**이제 끝났습니다!**

<!--
You can make sure time management is working properly by inspecting your `_posts` folder. You should see a markdown file
with the current date in the filename.
-->
시간 정보가 올바르게 관리되는지 확인하려면 `_posts` 폴더를 살펴보면 됩니다. 마크다운 파일의 파일명에 현재 날짜가 포함되어
있어야 합니다.

<div class="note info">
<!--
  <h5>Non-superuser account issues</h5>
  <p>If the `jekyll new` command prints the error "Your user account isn't allowed to install to the system RubyGems", see
  the "Running Jekyll as Non-Superuser" instructions in <a href="/docs/troubleshooting/#no-sudo">Troubleshooting</a>.</p>
-->
  <h5>일반 사용자 계정 이슈</h5>
  <p>만약 `jekyll new` 명령으로 "Your user account isn't allowed to install to the system RubyGems" 와 같은 에러가
  발생한다면, <a href="/docs/troubleshooting/#no-sudo">문제해결</a>에서 "관리자 권한 없이 Jekyll 실행하기" 부분을 살펴보세요.</p>
</div>

<!--
**Note:** Bash on Ubuntu on Windows is still under development, so you may run into issues.
-->
**중요:** 윈도우즈에서 사용하는 우분투용 Bash 는 지금도 개발이 진행중인 관계로, 문제가 발생할 가능성이 있습니다.


<!--
## Encoding
-->
## 인코딩

<!--
If you use UTF-8 encoding, make sure that no `BOM` header characters exist in your files or very, very bad things will happen to
Jekyll. This is especially relevant when you're running Jekyll on Windows.
-->
만약 UTF-8 인코딩을 사용한다면, 문서 안에 `BOM` 헤더를 사용하지 않아야 합니다. 그렇지 않으면 Jekyll 에 아주, 아주 안 좋은 일이 벌어집니다.
이는 특히, 윈도우즈에서 Jekyll 을 사용하는 것에 연관된 문제입니다.

<!--
Additionally, you might need to change the code page of the console window to UTF-8 in case you get a
`Liquid Exception: Incompatible character encoding` error during the site generation process. It can be done with the following
command:
-->
그리고, 사이트 생성 단계에서 "Liquid Exception: Incompatible character encoding" 에러가 발생하는 경우엔,
콘솔창의 코드 페이지를 UTF-8 로 바꿔야 할 수도 있습니다.
다음과 같이 입력하면 됩니다:

```sh
chcp 65001
```

<!--
## Time-Zone Management
-->
## 타임존 관리

<!--
Since Windows doesn't have a native source of zoneinfo data, the Ruby Interpreter would not understand IANA Timezones and hence
using them had the `TZ` environment variable default to UTC/GMT 00:00.

Though Windows users could alternatively define their blog's timezone by setting the key to use POSIX format of defining
timezones, it wasn't as user-friendly when it came to having the clock altered to changing DST-rules.
-->
윈도우즈에서는 루비 인터프리터가 IANA 타임존 정보를 처리하는데 필요한 정보 원천이 없기 때문에, 대신 환경변수 `TZ` 를
사용하며 그 기본값은 UTC/GMT 00:00 입니다.
윈도우즈 사용자들도 POSIX 형식의 타임존 설정을 통해 블로그의 타임존을 지정할 수 있었지만, DST 규칙에
따라 시간을 조정해야한다는 부분이 사용자 친화적이지 않았습니다.

<!--
Jekyll now uses a rubygem to internally configure Timezone based on established
[IANA Timezone Database](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
While 'new' blogs created with Jekyll v3.4 and greater, will have the following added to their `Gemfile` by default, existing
sites *will* have to update their `Gemfile` (and installed) to enable development on Windows:
-->
이제 Jekyll 은 공식적으로 인정된 [IANA 타임존 데이터베이스](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)에
근거하여 타임존을 자체적으로 설정하는 루비 젬을 사용합니다.
윈도우즈에서 개발환경을 활성화 하기 위해, Jekyll v3.4 또는 그 이상의 버전에서는 '새로' 블로그를 생성할 때 기본적으로
`Gemfile` 에 다음과 같은 내용이 추가되며, 이전에 생성된 사이트에서는 `Gemfile` 을 수정(하고 설치)*해야 할* 필요가 있습니다:

```ruby
# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

<div class="note warning">
<!--
  <h5>TZInfo 2.0 incompatibility</h5>
-->
  <h5>TZInfo 2.0 비호환</h5>
  <p>
<!--
    <code>v2.0</code> of the TZInfo library has introduced a change in how timezone offsets are calculated.
    This will result in incorrect date and time for your posts when the site is built with Jekyll 3.x on Windows.
-->
    TZInfo 라이브러리 <code>v2.0</code> 에서 타임존 오프셋 계산방법을 변경했습니다.
    이로 인해 윈도우즈에서 Jekyll 3.x 로 사이트를 생성할 때 포스트의 날짜와 시간에 오류가 발생합니다.
  </p>
  <p>
<!--
    We therefore recommend that you lock the Timezone library to <code>v1.2</code> and above by listing
    <code>gem 'tzinfo', '~> 1.2'</code> in your <code>Gemfile</code>.
-->
    따라서 <code>Gemfile</code> 에 <code>gem 'tzinfo', '~>1.2'</code> 를 추가해서
    이 타임존 라이브러리의 버전을 고정시키는 것을 권장합니다.
  </p>
</div>

<!--
## Auto Regeneration
-->
## 자동 재생성

<!--
Jekyll uses the `listen` gem to watch for changes when the `--watch` switch is specified during a build or serve.
While `listen` has built-in support for UNIX systems, it may require an extra gem for compatibility with Windows.
-->
생성이나 미리보기 시에 `--watch` 스위치를 설정하면 Jekyll 은 루비 젬 `listen` 을 사용하여 변경사항을 감지합니다.
유닉스 시스템에는 `listen` 이 기본 지원되지만, 윈도우즈에서도 호환되려면 추가로 다른 루비 젬이 더 필요할 수 있습니다.

<!--
Add the following to the `Gemfile` for your site if you have issues with auto-regeneration on Windows alone:
-->
윈도우즈에서 자동 재생성 기능에 무언가 문제가 있다면, 사이트의 `Gemfile` 에 다음 내용을 추가합니다:

```ruby
gem 'wdm', '~> 0.1.1', :install_if => Gem.win_platform?
```

<!--
You have to use a [Ruby+Devkit](https://rubyinstaller.org/downloads/) version of the RubyInstaller and install
the MSYS2 build tools to successfully install the `wdm` gem.
-->
반드시 [Ruby+Devkit](https://rubyinstaller.org/downloads/) 버전 RubyInstaller 를 사용하고
MSYS2 빌드 도구를 설치해야지만 `wdm` 젬을 정상적으로 설치할 수 있습니다.

```sh
bundle config path vendor/bundle
```

<!--
**And that's it!**
-->
**이제 끝났습니다!**

<!--
To start a new project named `my_blog`, just run:
-->
새 프로젝트 `my_blog` 를 시작하려면, 이렇게 실행합니다:

```sh
jekyll new my_blog
```

<!--
You can make sure time management is working properly by inspecting your `_posts` folder. You should see a markdown file with the current date in the filename.
-->
생성된 `_posts` 폴더를 확인해보면 타임존 관리가 올바르게 작동하고 있는지 확인할 수 있습니다. 파일명에 현재시간이 들어가 있는 마크다운 파일이 있을 것입니다.
