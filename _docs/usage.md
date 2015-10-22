---
layout: docs
title: 기본 사용법
permalink: /docs/usage/
---

Jekyll gem 은 터미널 창에서 사용할 수 있는 실행파일 `jekyll` 을 만들어줍니다. 이
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

<div class="note info">
  <h5>자동으로 다시 생성할 때, _config.yml 의 변경사항은 반영되지 않습니다.</h5>
  <p>
    주 환경설정 파일인 <code>_config.yml</code> 에는 전역 환경설정과 변수들이 정의되어 있으며,
    실행 시점에 한 번만 읽어들입니다. 자동 재생성을 사용하는 중이라도, 완전히 새로 실행하기 전까지는
    <code>_config.yml</code> 의 변경사항을 읽어들이지 않습니다.
  </p>
  <p>
    <a href="../datafiles">데이터 파일</a>들은 자동 재생성에 포함됩니다.
  </p>
</div>

<div class="note warning">
  <h5>사이트를 빌드하면 <code>&lt;destination&gt;</code> 폴더가 정리됩니다</h5>
  <p>
    사이트 빌드 시에 자동으로 <code>&lt;destination&gt;</code> 안의 파일들을
    지우는 것이 디폴트로 설정되어 있습니다. 사이트에서 생성하지 않는 파일들은
    모두 사라질 것입니다. 환경설정 옵션 <code>&lt;keep_files&gt;</code> 를
    사용하면 <code>&lt;destination&gt;</code> 에 그대로 유지시키려는 파일이나
    폴더를 선택할 수 있습니다.
  </p>
  <p>
    중요한 디렉토리는 절대 <code>&lt;destination&gt;</code> 으로 지정하면 안됩니다;
    웹 서버로 옮길 파일을 임시로 보관할 경로를 입력하세요.
  </p>
</div>

Jekyll 은 개발 서버도 내장하고 있어서, 로컬상에서 브라우저로 접속하여 사이트가
어떻게 생성될지 미리 살펴볼 수 있습니다.

{% highlight bash %}
$ jekyll serve
# => 개발용 서버가 http://localhost:4000/ 에서 구동됩니다
# 자동-재생성: 활성화됨. 비활성화 하려면 `--no-watch` 를 사용하세요.

$ jekyll serve --detach
# => 현재 터미널에서 분리된다는 점을 제외하고는 `jekyll serve` 와 동일합니다.
#    서버를 종료하려면, `kill -9 1234` 를 입력하면 됩니다. (여기서 "1234" 는 PID 입니다.)
#    PID 를 모른다면, `ps aux | grep jekyll` 라고 입력하세요. 그 다음, 인스턴스를 종료시킵니다. [자세한 내용](http://unixhelp.ed.ac.uk/shell/jobz5.html).
{% endhighlight %}

<div class="note info">
  <h5>디폴트 설정을 알아두세요</h5>
  <p>
    버전 2.4 부터, <code>serve</code> 명령은 자동으로 변경사항을 감시합니다. 기존 방식을 유지하려면, <code>jekyll serve --no-watch</code> 를 사용해서 비활성화 하세요.
  </p>
</div>

{% highlight bash %}
$ jekyll serve --no-watch
# => `jekyll serve` 와 동일하지만 변경사항은 감시하지 않습니다.
{% endhighlight %}

이것들은 [환경설정 옵션](../configuration/)의 극히 일부분만 보여준 것입니다.
다양한 환경설정 옵션들을 위와 같이 명령행에 플래그로 지정할 수 있고 또 다른
(그리고 더 일반적인) 방법으로, 루트 디렉토리의 `_config.yml` 파일에 지정할 수
있습니다. Jekyll 이 작동하기 시작하면, 자동적으로 이 파일에 지정한 옵션들을
사용합니다. 예를 들어, `_config.yml` 파일에 다음과 같이 입력한다면:


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
