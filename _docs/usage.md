---
layout: docs
title: 기본 사용법
prev_section: installation
next_section: structure
permalink: /docs/usage/
---

Jekyll gem 은 터미널 창에서 실행파일 `jekyll` 을 사용할 수 있게 해줍니다. 이 명령은 다양한 방식으로 사용할 수 있습니다:

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
    사이트를 생성하면 자동적으로 <code>&lt;destination&gt;</code> 안의 파일들이 지워집니다. 사이트에서 생성하지 않는 파일들은 모두 사라질 것입니다. <code>&lt;destination&gt;</code> 에는 중요한 폴더를 지정하지 마세요; 대신, 웹 서버에 복사하기 전에 임시로 파일을 넣어둘 폴더를 지정하세요.
  </p>
</div>

또한 Jekyll 에 내장된 개발용 서버를 실행하고 자신의 브라우저로 접속하면, 생성된 사이트가 어떻게 보일지 미리보기 할 수 있습니다.

{% highlight bash %}
$ jekyll serve
# => 개발용 서버가 http://localhost:4000/ 에서 구동됩니다

$ jekyll serve --detach
# => 현재 터미널에서 분리된다는 점을 제외하고는 `jekyll serve` 와 동일합니다.
#    서버를 종료하려면, `kill -9 1234` 를 입력하면 됩니다. (PID 가 "1234" 인 경우)
#    PID 를 모른다면, `ps aux | grep jekyll` 를 실행하고, 인스턴스를 종료시킵니다. [자세한 내용](http://unixhelp.ed.ac.uk/shell/jobz5.html).

$ jekyll serve --watch
# => 변경을 감지하고 자동으로 다시 생성한다는 점을 제외하고는 `jekyll serve` 와 동일합니다.
{% endhighlight %}

이것들은 [환경설정 옵션](../configuration/)의 아주 일부일 뿐입니다. 이렇게 명령행 플래그로 다양한 환경설정 옵션들을 지정할 수 있으며, 또 다른 (그리고 더 일반적인) 방법은 최상위 디렉토리의 `_config.yml` 파일에 정의하는 것입니다. Jekyll 이 작동하기 시작하면, 자동적으로 이 파일에 지정한 옵션들을 사용합니다. 예를 들어, `_config.yml` 파일에 다음과 같이 입력한다면:

{% highlight yaml %}
source:      _source
destination: _deploy
{% endhighlight %}

아래 두 명령은 동일합니다:

{% highlight bash %}
$ jekyll build
$ jekyll build --source _source --destination _deploy
{% endhighlight %}

환경설정 옵션에 대한 더 자세한 내용은 [환경설정](../configuration/) 페이지를 참고하세요.
