---
layout: docs
title: 업그레이드
prev_section: resources
next_section: contributing
permalink: /docs/upgrading/
---

Jekyll 을 업그레이드 하려구요? 먼저, 1.0 에서 바뀐 점 몇 가지를 알아두어야
합니다.

변경내용을 살펴보기 전에, 먼저 Jekyll 을 최신 버전으로 업그레이드 하세요:

{% highlight bash %}
$ gem update jekyll
{% endhighlight %}

<div class="note feature">
  <h5 markdown="1">시작하기</h5>
  <p markdown="1">빨리 Jekyll 사이트를 만들어보고 싶다구요? 간단하게
    <code>jekyll new 사이트이름</code> 을 실행해보세요. Jekyll 사이트의 골격이
    담긴 새 디렉토리가 만들어집니다.</p>
</div>

### Jekyll 명령어

모호함을 피하기 위해, Jekyll 은 이제 `build` 와 `serve` 명령을 제공합니다.
이전까지는 `jekyll` 로 사이트를 생성하고 `jekyll --server` 로 미리보기를
실행했었지만, 이제는 동일한 작업에 `jekyll build` 와 `jekyll serve` 명령을
사용합니다. 또, 파일이 변경되었을 때마다 자동으로 사이트를 다시 생성하고 싶다면,
명령 끝에 `--watch` 플래그만 추가하세요.

<div class="note info">
  <h5>미리보기와 감시</h5>
  <p markdown="1">새로운 명령어로 인하여, 사이트를 미리보기하는 방식이
    변경되었습니다. 사이트의 환경설정 파일에 `server: true` 를 추가하는 대신,
    `jekyll serve` 를 사용하세요.
    `watch: true` 설정도 동일합니다.
    `jekyll serve` 나 `jekyll build` 명령에 `--watch` 플래그를 사용하세요.</p>
</div>

### 절대적 고유주소

Jekyll v1.0 에서 하위 디렉토리의 페이지에 대한 절대적 고유주소가
소개되었었습니다. 이 기능은 v2.0 전까지는 **옵트-인**이었습니다. 하지만, v2.0
부터는 **옵트-아웃**으로 변경되었습니다. 다시 말해, Jekyll 은 상대적 고유주소
대신 절대적 고유주소를 기본값으로 사용한다는 뜻입니다.

* 절대적인 고유주소를 사용하려면, 환경설정 파일에 `relative_permalinks: false` 로 설정하세요
* 계속해서 상대적인 고유주소를 사용하려면, 환경설정 파일에 `relative_permalinks: true` 로 설정하세요

<div class="note warning" id="absolute-permalinks-warning">
  <h5 markdown="1">v2.0 이후부터는 절대적 고유주소가 기본값입니다</h5>
  <p markdown="1">
    Jekyll v2.0 부터, `relative_permalinks` 의 기본값이 `false` 로
    변경되었습니다. 이것은 모든 페이지가 절대적 고유주소 방식으로 생성된다는
    의미입니다. 현재 버전인 v2.0 까지도 이 변경사항이 유지되고 있습니다.
  </p>
</div>

### 초안

이제 Jekyll 에서 초안을 작성할 수 있으며, 게시 전에 미리보기하는 것이 아주
쉽습니다. 초안을 사용하려면, 사이트 소스 디렉토리에 (예, `_posts` 와 나란히)
`_drafts` 라는 이름의 디렉토리를 만들어 마크다운 파일을 넣으면 됩니다. 작성한
초안을 미리보기 하려면 `jekyll serve` 명령을 `--drafts` 플래그와 함께
실행하세요.

<div class="note info">
  <h5 markdown="1">초안에는 날짜가 없습니다</h5>
  <p markdown="1">
    포스트와는 다르게, 초안에는 날짜가 없습니다.
    아직 게시하지 않는 글이기 때문입니다.
    초안의 파일명은 `2013-07-01-my-draft-post.md` 가 아니라,
    `my-draft-post.md` 와 같이 원하는 제목으로만 생성하세요.</p>
</div>

### 사용자 환경설정 파일

명령어에 각각의 플래그를 지정하는 대신, 별도로 만든 Jekyll 환경설정 파일을
사용할 수 있습니다. 전체 환경을 구분지어 사용하거나 프로그램 상에서 기본값을
덮어쓰는데 유용합니다. 간단히 `jekyll` 명령에 `--config` 플래그를 추가하고, 그
뒤에 하나 또는 그 이상의 환경설정 파일 경로를 지정하세요 (공백 없이, 쉼표로
구분).

#### 따라서, 다음 플래그들은 더 이상 사용하지 않는 것을 권장합니다:

* `--no-server`
* `--no-auto`
* `--auto` (이제부터는 `--watch`)
* `--server`
* `--url=`
* `--maruku` 와 `--rdiscount`, `--redcarpet`
* `--pygments`
* `--permalink=`
* `--paginate`

<div class="note info">
  <h5>config 플래그는 환경설정 파일(들)을 명시적으로 지정합니다</h5>
  <p markdown="1">`--config` 플래그를 사용하면, `_config.yml` 파일은 자동적으로
    사용되지 않습니다.
    별도로 만든 환경설정 파일과 기본 환경설정 파일을 함께 사용하고 싶다구요?
    문제 없습니다. 하나 이상의 환경설정 파일을 Jekyll 에 전달할 수 있습니다.
    전달된 환경설정 파일은 오른쪽에서 왼쪽으로 중첩됩니다.
    파일에 동일한 키가 들어있을 경우 오른쪽의 환경설정 파일 (`_config-dev.yml`)
    이 왼쪽의 설정파일 (`_config.yml`) 값을 덮어쓰게 됩니다.</p>
</div>

### 새로운 환경설정 파일 옵션

Jekyll 1.0 에서 몇 가지 새 환경설정 파일 옵션이 소개되었었습니다. 업그레이드를
하기 전에, 1.0 이전 버전의 환경설정 파일에 아래 옵션들을 사용하고 있는지
확인해야 합니다. 만약 사용중이라면, 올바르게 사용하고 있는지도 확인하세요:

* `excerpt_separator`
* `host`
* `include`
* `keep_files`
* `layouts`
* `show_drafts`
* `timezone`
* `url`

### Baseurl

종종 여러가지 환경에서 Jekyll 을 사용해야 할 경우가 있습니다. 예를 들면, GitHub
Pages 에 푸쉬 하기 전에 로컬에서 미리보기 하는 경우입니다. 이를 쉽게 만들기
위하여 Jekyll 1.0 에서 `--baseurl` 플래그가 추가되었습니다. 이 기능을
활용하려면, 먼저 운영환경의 `baseurl` 을 `_config.yml` 파일에 추가합니다. 그
다음, 글 안에서는 상대경로 앞에 `{{ site.baseurl }}` 를 사용합니다. 미리보기를
해야하는 경우에는 `jekyll serve` 명령에 `--baseurl` 플래그와 함께 로컬의
`baseurl` (대부분의 경우 `/`) 을 지정합니다. Jekyll 은 전달된 값을 baseurl 로
사용할 것입니다. 이렇게 하면 모든 링크가 양쪽 환경 모두에서 원하는대로 작동할
것입니다.


<div class="note warning">
  <h5 markdown="1">페이지와 포스트 URL 은 모두 슬래쉬로 시작합니다</h5>
  <p markdown="1">위에 설명된 방법을 사용할 경우, 모든 포스트와 페이지의 URL
    앞에는 슬래쉬가 붙어있다는 것을 기억하시기 바랍니다.
    `site.baseurl = /` 와 `post.url = /2013/06/05/my-fun-post/` 를 예로 들면,
    두 URL 이 합쳐져서 두 개의 슬래쉬로 시작하는 URL 이 만들어집니다.
    이는 올바르지 않은 URL 입니다.
    따라서 `baseurl` 이 기본값인 `/` 가 아닐 경우에만 `site.baseurl` 을 사용할
    것을 권장합니다.</p>
</div>
