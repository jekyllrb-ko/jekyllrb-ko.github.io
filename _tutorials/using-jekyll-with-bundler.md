---
layout: tutorials
permalink: /tutorials/using-jekyll-with-bundler/
#title: Using Jekyll with Bundler
title: Bundler 로 Jekyll 사용하기
---

<!--
> Bundler provides a consistent environment for Ruby projects by tracking and
> installing the exact gems and versions that are needed.
-->
> Bundler 는 꼭 필요한 버전의 루비 젬을 추적하고 설치하여 루비 프로젝트에
> 필요한 일관된 환경을 제공합니다.

<!--
[Bundler](https://bundler.io) can be a great tool to use with Jekyll. Because it
tracks dependencies on a per-project basis, it is particularly useful if you
need to run different versions of Jekyll in different projects, or if you don't
want to install Jekyll at the system or user level. This tutorial will show you
how to create a new Jekyll project using Bundler and without installing Jekyll
outside the project.
-->
[Bundler](https://bundler.io) 는 Jekyll 과 함께 쓰기에 탁월한 도구입니다. 각
프로젝트별로 의존성을 관리하기 때문에 프로젝트별로 각각 다른 버전의 Jekyll 을
사용해야 하는 경우, 또는 시스템이나 사용자 디렉토리에 Jekyll 을 설치하는 것을
원치않는 경우에 특히 유용합니다. 이 튜토리얼에서는 Bundler 를 사용해서 프로젝트
외부의 디렉토리에 Jekyll 을 설치하지 않고도 새 Jekyll 프로젝트를 생성하는
방법을 설명할 것입니다.

<!--
## Before You Begin
-->
## 시작하기 전에 {#before-you-begin}

<!--
To complete this tutorial, you'll need to have
[Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/)
installed. You can find the installation instructions on their websites.
-->
이 튜토리얼을 끝마치려면,
[루비](https://www.ruby-lang.org/en/)와 [Bundler](https://bundler.io/) 가
설치되어 있어야 합니다. 설치방법은 각 웹사이트에서 찾을 수 있습니다.

<!--
## Initialize Bundler
-->
## Bundler 초기화 {#initialize-bundler}

<!--
The first thing to do is create a new directory for your project and run
`bundle init`. This creates a new Bundler project (by creating an empty
Gemfile).
-->
첫 번째로 해야할 일은 당신의 새 프로젝트 디렉토리를 만들고 `bundle init` 을
실행하는 것입니다. 이 명령은 (빈 Gemfile 을 만들어) 새 Bundler 프로젝트를
생성합니다.

```sh
mkdir my-jekyll-website
cd my-jekyll-website
bundle init
```

<!--
## Configure Bundler
-->
## Bundler 환경설정 {#configure-bundler}

<!--
This step is optional, but encouraged. We're going to configure Bundler to install
gems in the `./vendor/bundle/` project subdirectory. This allows us to install
our dependencies in an isolated environment, ensuring they don't conflict with
other gems on your system. If you skip this step, Bundler will install your
dependencies globally on your system.
-->
이 단계는 필수는 아니지만, 권장합니다. Bundler 가 프로젝트의 하위 디렉토리인
`./vendor/bundle/` 에 루비 젬들을 설치하도록 설정할 것입니다. 이것으로 우리가
필요로 하는 의존요소들을 격리된 환경에 설치할 수 있게 해주어, 당신의 시스템에
설치된 다른 루비 젬들과 충돌하는 일을 방지합니다. 이 단계를 건너뛰면, Bundler 는
의존요소들을 시스템 레벨에 설치할 것입니다.

```sh
bundle install --path vendor/bundle
```

<!--
<div class="note info">
  <h5>Bundler Config is Persistent</h5>
  <p>
    This step is only required once per project. Bundler saves your config in
    <code>./.bundle/config</code>, so future gems will be installed to the same
    location.
  </p>
</div>
-->
<div class="note info">
  <h5>Bundler 환경설정은 영구적입니다</h5>
  <p>
    이 단계는 프로젝트별로 한 번만 수행하면 됩니다. Bundler 는 당신의 환경설정을
    <code>./.bundle/config</code> 에 저장하기 때문에, 이후에 설치하는 루비 젬들은
    모두 동일한 디렉토리에 저장됩니다.
  </p>
</div>

<!--
## Add Jekyll
-->
## Jekyll 추가하기 {#add-jekyll}

<!--
Now, we're going to use Bundler to add Jekyll as a dependency of our new
project. This command will add the Jekyll gem to our Gemfile and install it to
the `./vendor/bundle/` folder.
-->
이제, Bundler 를 사용해 Jekyll 을 새 프로젝트의 의존요소로 추가할 것입니다.
이 명령은 Jekyll 루비 젬을 Gemfile 에 추가하고 `./vendor/bundle/` 폴더에 설치할
것입니다.

```sh
bundle add jekyll
```

<!--
## Create A Jekyll Scaffold
-->
## Jekyll 뼈대 만들기 {#create-a-jekyll-scaffold}

<!--
Now that Jekyll is installed, we can use it to create the scaffolding for our
site. We need the `--force` parameter because our folder isn't empty - it
already has some Bundler files in it. We run the `bundle install` separately
because Jekyll gets confused if the Gemfile already exists.
-->
이제 Jekyll 설치는 끝났고, 설치된 명령을 사용해 우리 사이트의 뼈대를 만들 수
있습니다. 파라메터 `--force` 를 사용해야 하는데, 폴더가 비어있지 않기
때문입니다 - 이미 몇몇 Bundler 관련 파일들이 있습니다. Gemfile 이 이미 존재하면
Jekyll 에 혼란을 주기때문에 따로 `bundle install` 을 실행할 것입니다.

```sh
bundle exec jekyll new --force --skip-bundle .
bundle install
```

<!--
## Serve the Site
-->
## 사이트 실행하기 {#serve-the-site}

<!--
Your new website is ready! You can serve the website with
`bundle exec jekyll serve` and visit it at
[http://127.0.0.1:4000](http://127.0.0.1:4000). From here, you're ready to
continue developing the site on your own. All of the normal Jekyll commands are
available to you, but you should prefix them with `bundle exec` so that Bundler
runs the version of Jekyll that is installed in your project folder.
-->
당신의 새 웹사이트가 준비되었습니다!
`bundle exec jekyll serve` 명령으로 웹사이트를 실행하고
[http://127.0.0.1:4000](http://127.0.0.1:4000) 로 확인할 수 있습니다. 지금부터,
당신만의 사이트를 개발할 준비가 된 것입니다. 모든 일반 Jekyll 명령어를 사용할
수 있습니다만, Bundler 가 당신의 프로젝트 폴더에 설치된 버전의 Jekyll 을 사용하게끔
명령어 앞에 `bundle exec` 를 추가해야 합니다.

<!--
## Commit to Source Control
-->
## 버전 관리 시스템 사용 {#commit-to-source-control}

<!--
If you're storing your new site in version control, you'll want to ignore the
`./vendor/` and `./.bundle/` folders since they contain user- or
platform-specific information. New users will be able to install the correct
dependencies based on `Gemfile` and `Gemfile.lock`, which should both be checked
in. You can use this `.gitignore` to get started, if you want.
-->
당신의 새 사이트를 버전 관리 시스템으로 관리중이라면, `./vendor/` 와 `./.bundle/`
폴더에는 사용자 또는 플랫폼 관련 정보들을 담고 있기 때문에 제외시키는 것이 좋습니다.
`Gemfile` 과 `Gemfile.lock` 은 사이트를 다운로드한 새 사용자가 올바를 의존요소를
설치하는데 필요하므로 버전 관리에 포함되어야 합니다. 원한다면, 시작은 이
`.gitignore` 파일을 사용해보세요.

**.gitignore**

<!--
```
# Ignore folders generated by Bundler
vendor
.bundle

# Ignore folders generated by Jekyll
.sass-cache
_site
```
-->
```
# Bundler 가 생성한 폴더 제외
vendor
.bundle

# Jekyll 이 생성한 폴더 제외
.sass-cache
_site
```

