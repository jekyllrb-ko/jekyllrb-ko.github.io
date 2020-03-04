---
#title: Assets
title: 에셋
permalink: /docs/assets/
---

<!--
Jekyll provides built-in support for [Sass](https://sass-lang.com/)
and can work with [CoffeeScript](https://coffeescript.org/) via a Ruby gem.
In order to use them, you must first create a file with the proper extension
name (one of `.sass`, `.scss`, or `.coffee`) and
***start the file with two lines of triple dashes***, like this:
-->
Jekyll 은 [Sass](https://sass-lang.com/) 를 기본적으로 지원하고
루비 젬을 통해 [CoffeeScript](https://coffeescript.org/) 와 연동할 수 있습니다.
사용 방법은, 일단 적절한 확장자 (`.sass` 나 `.scss`, `.coffee` 중 하나) 로
파일을 생성하고
***파일의 시작부분에 3 개의 대시문자 두 줄을 입력해야 합니다***. 이렇게 말이죠:

```sass
---
---

// start content
.my-definition
  font-size: 1.2em
```

<!--
Jekyll treats these files the same as a regular page, in that the output file
will be placed in the same directory that it came from. For instance, if you
have a file named `css/styles.scss` in your site's source folder, Jekyll
will process it and put it in your site's destination folder under
`css/styles.css`.
-->
Jekyll 은 이 파일들을 일반 페이지와 동일하게 다루기 때문에, 해당 파일에 대한
결과물은 원본과 동일한 디렉토리에 저장됩니다. 예를 들어, Site Source 폴더에
`css/styles.scss` 라는 파일을 가지고 있는 경우, Jekyll 은 해당 파일에 필요한
작업을 처리한 후 Site Destination 폴더의 `css/styles.css` 에 그 결과물을
저장합니다.

<div class="note info">
<!--
  <h5>Jekyll processes all Liquid filters and tags in asset files</h5>
  <p>If you are using <a href="https://mustache.github.io">Mustache</a>
     or another JavaScript templating language that conflicts with
     the <a href="/docs/templates/">Liquid template syntax</a>, you
     will need to place <code>{&#37; raw &#37;}</code> and
     <code>{&#37; endraw &#37;}</code> tags around your code.</p>
-->
  <h5>Jekyll 은 에셋 파일의 모든 Liquid 필터와 태그를 처리합니다</h5>
  <p>만약 <a href="https://mustache.github.io">Mustache</a> 를 사용하거나
     <a href="/docs/templates/">Liquid 템플릿 문법</a>과 충돌하는 다른
     JavaScript 템플릿 언어를 사용하고 있다면, 해당 코드 앞뒤에
     <code>{&#37; raw &#37;}</code> 와 <code>{&#37; endraw &#37;}</code> 태그를
     사용해야 합니다.</p>
</div>

## Sass/SCSS

<!--
Jekyll allows you to customize your Sass conversion in certain ways.
-->
Jekyll 로 Sass 변환을 당신만의 방법으로 사용자화 할 수 있습니다.

<!--
Place all your partials in your `sass_dir`, which defaults to
`<source>/_sass`. Place your main SCSS or Sass files in the place you want
them to be in the output file, such as `<source>/css`. For an example, take
a look at [this example site using Sass support in Jekyll][example-sass].
-->
관련된 파일을 `sass_dir` (디폴트: `<source>/_sass`) 에 넣습니다. 메인 SCSS 나
Sass 파일은 `<source>/css` 처럼 결과 파일이 생성되어야 하는 위치에 맞춰
넣습니다. 이에 대한 예시로, [Jekyll 의 Sass 기능을 사용한 예제
사이트][example-sass]를 살펴보세요.

<!--
If you are using Sass `@import` statements, you'll need to ensure that your
`sass_dir` is set to the base directory that contains your Sass files:
-->
만약 Sass 의 `@import` 선언을 사용한다면, 환경설정 옵션 `sass_dir` 에 Sass
파일이 들어있는 디렉토리를 지정해야 합니다:

```yaml
sass:
    sass_dir: _sass
```

<!--
The Sass converter will default the `sass_dir` configuration option to
`_sass`.
-->
Sass 변환기가 사용하는 환경설정 옵션 `sass_dir` 의 디폴트 값은 `_sass` 입니다.


[example-sass]: https://github.com/jekyll/jekyll-sass-converter/tree/master/docs

<div class="note info">
<!--
  <h5>The <code>sass_dir</code> is only used by Sass</h5>
  <p>

    Note that the <code>sass_dir</code> becomes the load path for Sass imports,
    nothing more. This means that Jekyll does not know about these files
    directly. Any files here should not contain the empty front matter as
    described above. If they do, they'll not be transformed as described above. This
    folder should only contain imports.

  </p>
-->
  <h5>오직 Sass 만이 <code>sass_dir</code> 을 사용합니다</h5>
  <p>

    <code>sass_dir</code> 은 Sass 의 import 대상 경로 그 이상도 그 이하도
    아닙니다. 이것은 Jekyll 이 이 파일들에 대하여 직접적으로 알지 못한다는
    뜻입니다. 이 안의 모든 파일은 앞서 설명한 것과 같은 빈 머리말을 가지고
    있어서는 안됩니다. 그렇지 않으면 변환 작업을 거치게 되지 않을것입니다. 이
    폴더 안에는 import 로 사용할 파일만 있어야 합니다.

  </p>
</div>

<!--
You may also specify the output style with the `style` option in your
`_config.yml` file:
-->
또, `_config.yml` 파일에 `style` 옵션을 설정하여 출력 스타일을 선택할 수
있습니다:

```yaml
sass:
    style: compressed
```

<!--
These are passed to Sass, so any output style options Sass supports are valid
here, too.
-->
이 설정은 Sass 에 그대로 전달되므로, Sass 가 지원하는 출력 스타일 옵션이라면
무엇이든 여기에 사용할 수 있습니다.


## Coffeescript

<!--
To enable Coffeescript in Jekyll 3.0 and up you must
-->
Jekyll 3.0 과 그 이후 버전에서 Coffeescript 를 활성화하려면

<!--
* Install the `jekyll-coffeescript` gem
* Ensure that your `_config.yml` is up-to-date and includes the following:
-->
* 루비 젬 `jekyll-coffeescript` 를 설치하고
* `_config.yml` 이 최신 상태이고 아래 내용을 포함하고 있어야 합니다:

```yaml
plugins:
  - jekyll-coffeescript
```
