---
#title: Jekyll on Windows
title: Windows 에서 Jekyll
permalink: /docs/windows/
---

<!--
While Windows is not an officially-supported platform, it can be used to run Jekyll with the proper tweaks. This page aims to collect some of the general knowledge and lessons that have been unearthed by Windows users.
-->
Windows 가 공식적으로 지원되는 플랫폼은 아니지만, 몇 가지만 손보면 Jekyll 을 실행할 수 있습니다. 이 페이지의 목적은 Windows 사용자에 의해서 발굴된 정보들을 수집하는 것입니다.


## Installing Jekyll
The easiest way to run Jekyll is by using the [RubyInstaller][] for Windows.

### Installation via RubyInstaller

[RubyInstaller][] is a self-contained Windows-based installer that includes the Ruby language, an execution environment, important documentation, and more.
We only cover RubyInstaller-2.4 and newer here, older versions need to [install the Devkit][Devkit-install] manually.

1. Download and Install a **Ruby+Devkit** version from [RubyInstaller Downloads][RubyInstaller-downloads].
   Use default options for installation.
2. Open a new command prompt window from the start menu, so that changes to the `PATH` environment variable becomes effective.
   Install Jekyll and Bundler via: `gem install jekyll bundler`
3. Check if Jekyll installed properly: `jekyll -v`

That's it, you're ready to install our [default minimal blog theme](https://github.com/jekyll/minima) with `jekyll new jekyll-website`.

[RubyInstaller]: https://rubyinstaller.org/
[RubyInstaller-downloads]: https://rubyinstaller.org/downloads/
[Devkit-install]: https://github.com/oneclick/rubyinstaller/wiki/Development-Kit


<!--
### Encoding
-->
### 인코딩

<!--
If you use UTF-8 encoding, make sure that no `BOM` header characters exist in your files or very, very bad things will happen to
Jekyll. This is especially relevant when you're running Jekyll on Windows.
-->
만약 UTF-8 인코딩을 사용한다면, 문서 안에 `BOM` 헤더를 사용하지 않아야 합니다. 그렇지 않으면 Jekyll 에 아주, 아주 안 좋은 일이 벌어집니다.
이 문제는 Windows 에서 Jekyll 을 실행하는 경우에만 해당됩니다.

<!--
Additionally, you might need to change the code page of the console window to UTF-8 in case you get a "Liquid Exception: Incompatible character encoding" error during the site generation process. It can be done with the following command:
-->
그리고, 사이트 생성 단계에서 "Liquid Exception: Incompatible character encoding" 에러가 발생하는 경우엔, 콘솔창의 코드 페이지를 UTF-8 로 바꿔야 할 수도 있습니다.  다음과 같이 입력하면 됩니다:

```sh
chcp 65001
```


### Time-Zone Management

Since Windows doesn't have a native source of zoneinfo data, the Ruby Interpreter would not understand IANA Timezones and hence using them had the `TZ` environment variable default to UTC/GMT 00:00.
Though Windows users could alternatively define their blog's timezone by setting the key to use POSIX format of defining timezones, it wasn't as user-friendly when it came to having the clock altered to changing DST-rules.

Jekyll now uses a rubygem to internally configure Timezone based on established [IANA Timezone Database][IANA-database].
While 'new' blogs created with Jekyll v3.4 and greater, will have the following added to their 'Gemfile' by default, existing sites *will* have to update their 'Gemfile' (and installed) to enable development on Windows:

```ruby
# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```

[IANA-database]: https://en.wikipedia.org/wiki/List_of_tz_database_time_zones

<!--
### Auto Regeneration
-->
## 자동 재생성

<!--
Jekyll uses the `listen` gem to watch for changes when the `--watch` switch is specified during a build or serve. While `listen` has built-in support for UNIX systems, it may require an extra gem for compatibility with Windows.
-->
Jekyll 은 `listen` gem 을 사용하여, 생성이나 미리보기 시에 `--watch` 스위치가 설정되면, 변경사항을 감시하게 되었습니다. UNIX 시스템에는 `listen` 이 기본 지원되지만, Windows 에서 호환되려면 다른 gem 이 더 필요할 수도 있습니다.

<!--
Add the following to the Gemfile for your site if you have issues with auto-regeneration on Windows alone:
-->
Windows 에서 자동 재생성 기능에 무언가 문제가 있다면, 사이트의 Gemfile 에 다음 내용을 추가합니다:

```ruby
gem 'wdm', '~> 0.1.1' if Gem.win_platform?
```

You have to use a [Ruby+Devkit](https://rubyinstaller.org/downloads/) version of the RubyInstaller.


## Installation via Bash on Windows 10

If you are using Windows 10 version 1607 or later, another option to run Jekyll is by [installing][WSL-Guide] the Windows Subsystem for Linux.


*Note:* You must have [Windows Subsystem for Linux][BASH-WSL] enabled.

First let's make sure all our packages / repositories are up to date. Open a new Command Prompt instance, and type the following:

```sh
bash
```
Your Command Prompt instance should now be a Bash instance. Now we must update our repo lists and packages.

```sh
sudo apt-get update -y && sudo apt-get upgrade -y
```
Now we can install Ruby. To do this we will use a repository from [BrightBox](https://www.brightbox.com/docs/ruby/ubuntu/), which hosts optimized versions of Ruby for Ubuntu.

```sh
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.3 ruby2.3-dev build-essential dh-autoreconf
```

Next let's update our Ruby gems:

```sh
sudo gem update
```

Now all that is left to do is install Jekyll.

```sh
sudo gem install jekyll bundler
```

Check if Jekyll installed properly by running:

```sh
jekyll -v
```

Configure the bundler/gem path so bundle doesn't prompt for sudo

```sh
bundle config path vendor/bundle
```

**And that's it!**

To start a new project named `my_blog`, just run:

```sh
jekyll new my_blog
```

You can make sure time management is working properly by inspecting your `_posts` folder. You should see a markdown file with the current date in the filename.

<div class="note info">
  <h5>Non-superuser account issues</h5>
  <p>If the `jekyll new` command prints the error "Your user account isn't allowed to install to the system RubyGems", see the "Running Jekyll as Non-Superuser" instructions in <a href="/docs/troubleshooting/#no-sudo">Troubleshooting</a>.</p>
</div>

**Note:** Bash on Ubuntu on Windows is still under development, so you may run into issues.

[WSL-Guide]: https://msdn.microsoft.com/en-us/commandline/wsl/install_guide
[BASH-WSL]: https://msdn.microsoft.com/en-us/commandline/wsl/about

