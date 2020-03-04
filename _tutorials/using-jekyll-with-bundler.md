---
layout: tutorials
permalink: /tutorials/using-jekyll-with-bundler/
#title: Using Jekyll with Bundler
title: Jekyll 에 Bundler 사용하기
---

<!--
> Bundler provides a consistent environment for Ruby projects by tracking and
> installing the exact gems and versions that are needed.
-->
> Bundler 는 루비 프로젝트에 필요한 젬들의 올바른 버전을 추적하고 설치해서
> 일관된 환경을 제공합니다.

<!--
[Bundler](https://bundler.io) can be a great tool to use with Jekyll. Because it
tracks dependencies on a per-project basis, it is particularly useful if you
need to run different versions of Jekyll in different projects, or if you don't
want to install Jekyll at the system or user level. This tutorial will show you
how to create a new Jekyll project using Bundler and without installing Jekyll
outside the project.
-->
[Bundler](https://bundler.io) 는 Jekyll 과 함께 사용하기에 탁월한 도구입니다.
프로젝트별로 의존요소들을 추적하기 때문에, 프로젝트에 따라 다른 버전의
Jekyll 을 사용해야 하거나 Jekyll 을 시스템 레벨이나 사용자 레벨에
설치하고 싶지 않을때 특히 유용합니다. 이 튜토리얼은 Bundler 를 사용해서
Jekyll 을 프로젝트 밖에 설치하지 않고 새 Jekyll 프로젝트를 생성하는 방법을
설명합니다.

<!--
## Before You Begin
-->
## 시작하기 전

<!--
To complete this tutorial, you'll need to have
[Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/)
installed. You can find the installation instructions on their websites.
-->
이 튜토리얼을 끝마치려면,
[루비](https://www.ruby-lang.org/en/)와 [Bundler](https://bundler.io/) 가
설치되어 있어야 합니다. 각 웹사이트에서 설치 방법을 찾을 수 있습니다.

<!--
## Initialize Bundler
-->
## Bundler 초기화

<!--
The first thing to do is create a new directory for your project and run
`bundle init`. This creates a new Bundler project (by creating an empty
Gemfile).
-->
가장 먼저 해야할 일은 프로젝트를 위한 새 디렉토리를 생성하고 `bundle init` 을
실행하는 것입니다. 이 명령은 (빈 Gemgile 을 생성해서) 새 Bundler 프로젝트를
생성합니다.

```sh
mkdir my-jekyll-website
cd my-jekyll-website
bundle init
```

<!--
## Configure Bundler
-->
## Bundler 환경설정

<!--
This step is optional, but encouraged. We're going to configure Bundler to install
gems in the `./vendor/bundle/` project subdirectory. This allows us to install
our dependencies in an isolated environment, ensuring they don't conflict with
other gems on your system. If you skip this step, Bundler will install your
dependencies globally on your system.
-->
이 단계는 선택사항이지만, 권장하고 있습니다. 여기서 우리는 프로젝트 하위 디렉토리
`./vendor/bundle/` 에 젬을 설치하도록 Bundler 를 설정할 것입니다. 이는
의존요소들을 고립된 환경에 설치해서, 시스템에 설치된 다른 젬들과 충돌이
발생하지 않도록 보장해줍니다. 이 단계를 건너뛰면, Bundler 는 시스템 레벨에
의존요소들을 설치할 것입니다.

```sh
bundle install --path vendor/bundle
```

<div class="note info">
<!--
  <h5>Bundler Config is Persistent</h5>
-->
  <h5>Bundler 설정은 유지됩니다</h5>
  <p>
<!--
    This step is only required once per project. Bundler saves your config in
    <code>./.bundle/config</code>, so future gems will be installed to the same
    location.
-->
    이 작업은 프로젝트별로 한 번만 하면 됩니다. Bundler 는
    <code>./.bundle/config</code> 에 환경설정을 저장해서, 이후의 젬들도 동일한
    위치에 설치됩니다.
  </p>
</div>

<!--
## Add Jekyll
-->
## Jekyll 추가

<!--
Now, we're going to use Bundler to add Jekyll as a dependency of our new
project. This command will add the Jekyll gem to our Gemfile and install it to
the `./vendor/bundle/` folder.
-->
이제, Bundler 를 사용해서 우리의 새 프로젝트에 Jekyll 을 의존요소로서 추가할
것입니다. 이 명령은 Jekyll 젬을 Gemfile 에 추가하고 `./vendor/bundle/` 폴더에
설치합니다.

```sh
bundle add jekyll
```

<!--
## Create A Jekyll Scaffold
-->
## Jekyll 뼈대 생성하기

<!--
Now that Jekyll is installed, we can use it to create the scaffolding for our
site. We need the `--force` parameter because our folder isn't empty - it
already has some Bundler files in it. We run the `bundle install` separately
because Jekyll gets confused if the Gemfile already exists.
-->
이제 Jekyll 이 설치되었으므로, 이를 이용해 우리의 사이트를 위한 뼈대를 생성할
수 있습니다. 폴더가 비어있지 않으므로 - 이미 Bundler 관련 파일들이 좀 들어
있습니다 - `--force` 파라메터를 사용해야 합니다. Gemfile 이 이미 존재하는 경우
Jekyll 작업에 혼란을 가져올 수 있으므로 `bundle install` 은 따로 실행합니다.

```sh
bundle exec jekyll new --force --skip-bundle .
bundle install
```

<!--
## Serve the Site
-->
## 서버 작동

<!--
Your new website is ready! You can serve the website with
`bundle exec jekyll serve` and visit it at
[http://127.0.0.1:4000](http://127.0.0.1:4000). From here, you're ready to
continue developing the site on your own. All of the normal Jekyll commands are
available to you, but you should prefix them with `bundle exec` so that Bundler
runs the version of Jekyll that is installed in your project folder.
-->
당신의 새 웹사이트가 준비되었습니다! `bundle exec jekyll serve` 명령으로
웹사이트를 서버에 올리고
[http://127.0.0.1:4000](http://127.0.0.1:4000) 로 접속할 수 있습니다. 이제부터,
당신만의 사이트를 개발할 준비가 되었습니다. 모든 Jekyll 명령어를 사용할 수
있지만, 명령어 앞에 `bundle exec` 를 붙여 Bundler 가 당신의 프로젝트 폴더에
설치된 버전의 Jekyll 을 실행하도록 해야합니다.

<!--
## Commit to Source Control
-->
## 소스 코드 관리

<!--
If you're storing your new site in version control, you'll want to ignore the
`./vendor/` and `./.bundle/` folders since they contain user- or
platform-specific information. New users will be able to install the correct
dependencies based on `Gemfile` and `Gemfile.lock`, which should both be checked
in. You can use this `.gitignore` to get started, if you want.
-->
버전 관리 시스템으로 당신의 새 사이트를 관리하고 있다면, `./vendor/` 와 `./.bundle/`
폴더는 사용자 또는 플랫폼 관련 정보를 담고 있기 때문에 ignore 목록에
추가합니다. 다른 사용자들은 `Gemfile` 과 `Gemfile.lock` 에 기반하여 올바른
의존요소들을 설치할 수 있을 것입니다. 따라서 이 두 파일은 버전 관리 시스템에 등록되어야
합니다. 원한다면, 아래 `.gitignore` 파일을 사용해 시작해보세요.

**.gitignore**

<!--
```
# Ignore metadata generated by Jekyll
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata

# Ignore folders generated by Bundler
.bundle/
vendor/
```
-->
```
# Jekyll 이 생성한 메타 데이터 무시
_site/
.sass-cache/
.jekyll-cache/
.jekyll-metadata

# Bundler 가 생성한 폴더 무시
.bundle/
vendor/
```
