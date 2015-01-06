---
layout: docs
title: 기본 사용법
prev_section: installation
next_section: structure
permalink: /docs/usage/
---

Jekyll gem 은 터미널 창에서 실행파일 `jekyll` 을 사용할 수 있게 해줍니다. 이
명령은 다양한 방식으로 사용할 수 있습니다:

{% highlight bash %}
$ jekyll build
# => ./_site 에 현재 폴더의 내용으로 사이트를 생성합니다

$ jekyll build --destination <destination>
# => <destination> 에 현재 폴더의 내용으로 사이트를 생성합니다

$ jekyll build --source <source> --destination <destination>
# => <destination> 에 <source> 폴더의 내용으로 사이트를 생성합니다

$ jekyll build --watch
# => ./_site 에 현재 폴더의 내용으로 사이트를 생성하고,
#    변경사항을 감지하면 자동으로 다시 생성합니다.
{% endhighlight %}

<div class="note warning">
  <h5>사이트 생성 시 <code>&lt;destination&gt;</code> 폴더가 정리됩니다</h5>
  <p>
    사이트를 생성하면 자동적으로 <code>&lt;destination&gt;</code> 안의 파일들이
    지워집니다.
    사이트에서 생성하지 않는 파일들은 모두 사라질 것입니다.
    중요한 폴더를 <code>&lt;destination&gt;</code> 으로 지정하면 안됩니다;
    그 대신, 파일을 웹 서버에 복사하기 전에 임시로 보관할 폴더를 지정하세요.
  </p>
</div>

또한 Jekyll 에 내장된 개발용 서버를 실행하고 자신의 브라우저로 접속하면, 생성된
사이트가 어떻게 보일지 미리보기 할 수 있습니다.

{% highlight bash %}
$ jekyll serve
# => 개발용 서버가 http://localhost:4000/ 에서 구동됩니다
# 자동-재생성: 활성화됨. 비활성화 하려면 `--no-watch` 를 사용하세요.

$ jekyll serve --detach
# => 현재 터미널에서 분리된다는 점을 제외하고는 `jekyll serve` 와 동일합니다.
#    서버를 종료하려면, `kill -9 1234` 를 입력하면 됩니다. (PID 가 "1234" 인 경우)
#    PID 를 모른다면, `ps aux | grep jekyll` 를 실행하고, 인스턴스를 종료시킵니다. [자세한 내용](http://unixhelp.ed.ac.uk/shell/jobz5.html).
{% endhighlight %}

<div class="note info">
  <h5>기본 작동방식을 염두해두세요</h5>
  <p>
    버전 2.4 부터, <code>serve</code> 명령은 자동으로 변경사항을 감시합니다. 기존 방식을 유지하려면, <code>jekyll serve --no-watch</code> 를 사용해서 비활성화하세요.
  </p>
</div>

{% highlight bash %}
$ jekyll serve --no-watch
# => `jekyll serve` 와 동일하지만 변경사항을 감시하지 않습니다.
{% endhighlight %}

이 옵션들은 [환경설정 옵션](../configuration/)의 아주 일부분일 뿐입니다.
다양한 환경설정 옵션들을 위와 같이 명령행 플래그로 지정할 수도 있고,
또 다른 (그리고 더 일반적인) 방법으로는 루트 디렉토리의 `_config.yml` 파일에
정의하는 방법이 있습니다. Jekyll 이 작동하기 시작하면, 자동적으로 이 파일에
지정한 옵션들을 사용합니다.
예를 들어, `_config.yml` 파일에 다음과 같이 입력한다면:

{% highlight yaml %}
source:      _source
destination: _deploy
{% endhighlight %}

아래 두 명령은 동일합니다:

{% highlight bash %}
$ jekyll build
$ jekyll build --source _source --destination _deploy
{% endhighlight %}

환경설정 옵션에 대한 더 자세한 내용은 [환경설정](../configuration/) 페이지를
참고하세요.

만약 이 문서처럼 끊임없이 수정되는 최신 문서에 관심이 많다면, `jekyll-docs` gem
을 설치하고, 터미널에서 `jekyll docs` 를 실행하세요.
