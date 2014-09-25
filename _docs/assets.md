---
layout: docs
title: 자료
prev_section: datafiles
next_section: migrations
permalink: /docs/assets/
---

Jekyll 은 Sass 와 CoffeeScript 에 대한 지원을 기본적으로 내장하고 있습니다. 이를 사용하기 위해서는, 적절한 확장자를 가진 (`.sass` 나 `.scss`, `.coffee` 중 하나) 파일을 생성하고 파일이 3 개의 대쉬문자 두 줄로 시작해야 합니다. 이렇게 말이죠:

{% highlight sass %}
---
---

// 컨텐츠 시작
.my-definition
  font-size: 1.2em
{% endhighlight %}

Jekyll 은 이러한 파일들을 일반 페이지처럼 다루기 때문에, 출력물이 원본과 동일한 디렉토리에 담기게 됩니다. 예를 들어, 사이트 원본 폴더에 `css/styles.scss` 라는 이름의 파일을 가지고 있다면, Jekyll 은 해당 파일을 처리한 후 사이트 결과물 폴더의 `css/styles.css` 에 생성합니다.

<div class="note info">
  <h5>Jekyll 은 자료 파일의 모든 Liquid 필터와 태그를 처리합니다</h5>
  <p>만약 <a href="{{ site.baseurl }}/docs/templates/">Liquid 템플릿 문법</a>과 충돌이 있는 <a href="http://mustache.github.io">Mustache</a> 나 다른 JavaScript 템플릿 언어를 사용하고 있다면, <code>{&#37; raw &#37;}</code> 와 <code>{&#37; endraw &#37;}</code> 태그로 코드 주변을 감싸야 할 것입니다</p>
</div>

## Sass/SCSS

Jekyll 은 Sass 변환을 당신만의 방법으로 사용자화 할 수 있게 허용합니다.

관련된 파일들을 기본값이 `<source>/_sass` 인 `sass_dir` 에 넣습니다. `<source>/css` 같은 곳에 메인 SCSS 나 Sass 파일을 넣습니다. 예를 들면, [이 Jekyll 의 Sass 지원을 사용한 예제 사이트][example-sass]를 살펴보세요.

만약 Sass `@import` 선언을 사용한다면, `sass_dir` 이 Sass 파일의 들어있는 디렉토리로 설정되었는지 확인해야 합니다. 다음과 같이 할 수 있습니다:

{% highlight yaml %}
sass:
    sass_dir: _sass
{% endhighlight %}

Sass 변환기는 `sass_dir` 환경설정 옵션의 기본값을 `_sass` 로 설정합니다.

[example-sass]: https://github.com/jekyll/jekyll-sass-converter/tree/master/example

<div class="note info">
  <h5><code>sass_dir</code> 은 Sass 에 의해서만 사용됩니다</h5>
  <p>

    <code>sass_dir</code> 는 Sass import 의 기본 경로이며, 그 이상도 이하도 아닙니다. 이것은 Jekyll 이 이 파일들에 대하여 직접적으로 알지 못한다는 뜻이며, 따라서 앞서 설명한 것과 같이 이 안의 모든 파일은 YAML 머리말을 가지고 있어서는 안되고, 그렇지 않으면 변환이 되고 말 것입니다. 이 폴더에는 import 로 사용할 파일들만 있어야 합니다.

  </p>
</div>

또한 `_config.yml` 파일에 `style` 옵션으로 출력 스타일을 지정할 수 있습니다:

{% highlight yaml %}
sass:
    style: :compressed
{% endhighlight %}

이 설정은 Sass 에 전달되어, Sass 가 지원하는 어떠한 출력 스타일 옵션도 유효해지는 것이다.
