---
layout: step
#title: Setup
title: 셋업
#menu_name: Step by Step Tutorial
menu_name: 단계별 튜토리얼
position: 1
---
<!--
Welcome to Jekyll's step-by-step tutorial. The goal of this tutorial is to take
you from having some front end web development experience to building your
first Jekyll site from scratch — not relying on the default gem-based theme. 
Let's get into it!
-->
Jekyll 단계별 튜토리얼에 오신 것을 환영합니다. 이 튜토리얼의 목표는 약간의
프론트엔드 웹 개발 경험을 쌓는 것부터 아무것도 없이 — 기본 젬 기반 테마에
의존하지 않고 — 시작해 당신의 첫 Jekyll 사이트를 생성하는 것입니다.
시작해봅시다!

<!--
## Installation
-->
## 설치

<!--
Jekyll is a Ruby program so you need to install Ruby on your machine to begin
with. Head over to the [install guide](/docs/installation/) and follow the
instructions for your operating system.
-->
Jekyll 은 루비 프로그램이기 때문에 우선 루비를 설치해야 합니다.
[설치 설명서](/docs/installation/)를 열어 자신의 운영체제에 맞는
지시를 따릅니다.

<!--
With Ruby setup you can install Jekyll by running the following in your
terminal:
-->
루비가 준비되었으면 터미널에 다음과 같이 실행하여 Jekyll 을 설치할 수
있습니다:

```
gem install jekyll bundler
```

<!--
To create a new `Gemfile` to list your project's dependencies run:
-->
프로젝트의 의존요소 목록인 `Gemfile` 을 생성하려면 이렇게 실행합니다:

```
bundle init
```

<!--
Now edit the `Gemfile`and add jekyll as a dependency:
-->
이제 `Gemfile` 을 열어 jekyll 을 의존요소로 추가합니다:

```
gem "jekyll"
```

<!--
Finally run `bundle` to install jekyll for your project.
-->
마지막으로 `bundle` 을 실행해 프로젝트에 Jekyll 을 설치합니다.

<!--
You can now prefix all jekyll commands listed in this tutorial with `bundle exec` 
to make sure you use the jekyll version defined in your `Gemfile`.
-->
이제부터 이 튜토리얼에 언급된 모든 Jekyll 명령어 앞에 `bundle exec` 를 붙여
실행하면 항상 `Gemfile` 에 정의된 버전의 Jekyll 을 사용할 수 있습니다.

<!--
## Create a site
-->
## 사이트 생성

<!--
It's time to create a site! Create a new directory for your site, you can name
it whatever you'd like. Through the rest of this tutorial we'll refer to this
directory as “root”.
-->
이제 사이트를 생성할 차례입니다! 사이트를 위한 새 디렉토리를 원하는 이름으로
생성합니다. 이 튜토리얼에서는 이 디렉토리를 “루트” 라고 부를 것입니다.

<!--
If you're feeling adventurous, you can also initialize a Git repository here.
One of the great things about Jekyll is there's no database. All content and
site structure are files which a Git repository can version. Using a repository
is completely optional but it's a great habit to get into. You can learn more
about using Git by reading through the
[Git Handbook](https://guides.github.com/introduction/git-handbook/).
-->
모험을 즐기는 편이라면, 여기에 Git 저장소를 구성할 수도 있습니다.
Jekyll 의 장점 중 하나는 데이터베이스가 없다는 것입니다. 컨텐츠와 사이트 구조는
모두 파일로 되어있어 Git 저장소로 버전관리가 가능합니다. 저장소를 사용하는 것은
전적으로 선택사항이지만 익숙해지면 좋은 습관임에는 틀림이 없습니다. Git 을
사용하는 방법에 대해 더 배우고 싶다면
[Git Handbook](https://guides.github.com/introduction/git-handbook/) 을 읽어보세요.

<!--
Let's add your first file. Create `index.html` in the root with the following
content:
-->
첫 번째 파일을 추가해봅시다. 루트에 다음과 같은 내용을 가진 `index.html` 을
생성합니다:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

<!--
## Build
-->
## 빌드

<!--
Jekyll is a static site generator so we need Jekyll to build the site
before we can view it. There are two commands you can run in the root of your site
to build it:
-->
Jekyll 은 정적 사이트 생성기로서 사이트를 보려면 먼저 Jekyll 로 사이트를
빌드해야 합니다. 사이트 빌드에 사용하는 명령어는 두 가지로 사이트의 루트에서
실행할 수 있습니다:

<!--
* `jekyll build` - Builds the site and outputs a static site to a directory
called `_site`.
* `jekyll serve` - Does the same thing except it rebuilds any time you make
a change and runs a local web server at `http://localhost:4000`.
-->
* `jekyll build` - 사이트를 빌드하고 `_site` 라는 디렉토리에 정적 사이트를
생성합니다.
* `jekyll serve` - 위와 동일한 작업을 하지만 추가로 내용이 변경되면 사이트를
다시 빌드하고 `http://localhost:4000` 주소에 로컬 웹 서버를 구동합니다.

<!--
When you're developing a site you'll use `jekyll serve` as it updates with any
changes you make.
-->
사이트 개발 중에는 `jekyll serve` 를 사용해 사이트를 수정할 때마다 갱신이 되도록
합니다.

<!--
Run `jekyll serve` and go to
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a> in
your browser. You should see "Hello World!".
-->
`jekyll serve` 를 실행하고 브라우저로
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a> 에
접속합니다. "Hello World!" 가 보일 것입니다.

<!--
Well, you might be thinking what's the point in this? Jekyll just copied an
HTML file from one place to another. Well patience young grasshopper, there's
still much to learn!
-->
음.. 이런 생각이 들 수도 있어요.<br/>
이런걸 왜 하고 있지? Jekyll 이 한 일이라곤 HTML 파일을 다른 위치로 그냥 복사한 것 뿐이네.<br/>
자.. 참을성이 필요한 때입니다. 아직 배울게 많아요!
