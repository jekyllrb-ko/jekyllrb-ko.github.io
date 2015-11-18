---
layout: docs
title: 재료
permalink: /docs/assets/
---

Jekyll 은 Sass 를 기본적으로 지원하고 Ruby gem 을 통해 CoffeeScript 와 연동할 수 
있습니다. 사용 방법은, 일단 적절한 확장자 (`.sass` 나 `.scss`, `.coffee` 중 
하나) 로 파일을 생성하고 파일의 시작부분에 3 개의 대시문자 두 줄을 입력해야 
합니다. 이렇게 말이죠:

{% highlight sass %}
---
---

// 컨텐츠 시작
.my-definition
  font-size: 1.2em
{% endhighlight %}

Jekyll 은 이런 파일들을 일반 페이지와 동일하게 다루기 때문에, 해당 파일에 대한
결과물은 원본과 동일한 디렉토리에 저장됩니다. 예를 들어, Site Source 폴더에
`css/styles.scss` 라는 파일을 가지고 있는 경우, Jekyll 은 해당 파일에 필요한
작업을 처리한 후 Site Destination 폴더의 `css/styles.css` 에 그 결과물을
저장합니다.

<div class="note info">
  <h5>Jekyll 은 재료 파일의 모든 Liquid 필터와 태그를 처리합니다</h5>
  <p>만약 <a href="http://mustache.github.io">Mustache</a> 를 사용하거나
     <a href="/docs/templates/">Liquid 템플릿 문법</a>과 충돌하는 다른
     JavaScript 템플릿 언어를 사용하고 있다면, 해당 코드 앞뒤에
     <code>{&#37; raw &#37;}</code> 와 <code>{&#37; endraw &#37;}</code> 태그를
     사용해야 합니다.</p>
</div>

## Sass/SCSS

Jekyll 로 Sass 변환을 당신만의 방법으로 사용자화 할 수 있습니다.

관련된 파일들을 `sass_dir` (디폴트: `<source>/_sass`) 에 넣습니다. 메인 SCSS 나
Sass 파일은 `<source>/css` 처럼 결과 파일이 생성되어야 하는 위치에 맞춰
넣습니다. 이에 대한 예시로, [Jekyll 의 Sass 기능을 사용한 예제
사이트][example-sass]를 살펴보세요.

만약 Sass 의 `@import` 선언을 사용한다면, 환경설정 옵션 `sass_dir` 에 Sass
파일이 들어있는 디렉토리를 지정해야 합니다. 그 방법은 다음과 같습니다:


{% highlight yaml %}
sass:
    sass_dir: _sass
{% endhighlight %}

Sass 변환기가 사용하는 환경설정 옵션 `sass_dir` 의 디폴트 값은 `_sass` 입니다.


[example-sass]: https://github.com/jekyll/jekyll-sass-converter/tree/master/example

<div class="note info">
  <h5>오직 Sass 만이 <code>sass_dir</code> 을 사용합니다</h5>
  <p>

    <code>sass_dir</code> 은 오로지 Sass 의 import 대상 경로일 뿐이며, 그 이상도
    이하도 아닙니다. 이것은 Jekyll 이 이 파일들에 대하여 직접적으로 알지
    못한다는 뜻이며, 따라서 이 안의 모든 파일은 YAML 머리말을 가지고 있어서는
    안되고, 그렇지 않으면 앞서 설명한 것과 같이 변환 작업을 거치게 될 것입니다.
    이 폴더에는 import 로 사용할 파일들만 있어야 합니다.

  </p>
</div>

또, `_config.yml` 파일에 `style` 옵션을 설정하여 출력 스타일을 선택할 수
있습니다:

{% highlight yaml %}
sass:
    style: compressed
{% endhighlight %}

이 설정은 Sass 에 그대로 전달되므로, Sass 가 지원하는 출력 스타일 옵션이라면
무엇이든 여기에 사용할 수 있습니다.


## Coffeescript

Jekyll 3.0 과 그 이후 버전에서 Coffeescript 를 활성화하려면 
 * `jekyll-coffeescript` gem 을 설치하고
 * `_config.yml` 이 최신 상태이고 아래 내용을 포함하고 있는지 확인해야 합니다.

{% highlight yaml %}
gems:
 - jekyll-coffeescript
{% endhighlight %}
