---
#title: Basic Usage
title: 기본 사용법
permalink: /docs/usage/
---

<!--
The Jekyll gem makes a `jekyll` executable available to you in your Terminal
window. You can use this command in a number of ways:
-->
루비 젬 Jekyll 은 터미널 창에서 사용할 수 있는 실행파일 `jekyll` 을 만들어줍니다. 이
명령은 다양한 방식으로 사용할 수 있습니다:

<!--
```sh
jekyll build
# => The current folder will be generated into ./_site

jekyll build --destination <destination>
# => The current folder will be generated into <destination>

jekyll build --source <source> --destination <destination>
# => The <source> folder will be generated into <destination>

jekyll build --watch
# => The current folder will be generated into ./_site,
#    watched for changes, and regenerated automatically.
```
-->
```sh
jekyll build
# => 현재 폴더의 컨텐츠를 가지고 ./_site 에 사이트를 생성합니다.

jekyll build --destination <destination>
# => 현재 폴더의 컨텐츠를 가지고 <destination> 에 사이트를 생성합니다.

jekyll build --source <source> --destination <destination>
# => <source> 폴더의 컨텐츠를 가지고 <destination> 에 사이트를 생성합니다.

jekyll build --watch
# => 현재 폴더의 컨텐츠를 가지고 ./_site 에 사이트를 생성합니다.
#    변경사항이 감지되면, 자동으로 다시 생성합니다.
```

<!--
## Override default development settings
-->
## 개발 환경설정 기본값 변경하기

<!--
Default URL is set to `http://localhost:4000` in development environment. {% include docs_version_badge.html version="3.3.0" %}
-->
개발환경의 URL 기본값은 `http://localhost:4000` 으로 설정되어 있습니다. {% include docs_version_badge.html version="3.3.0" %}

<!--
If you want to build for your production environment:
-->
운영환경에 맞춰 생성하고자 하는 경우에는:

<!--
  - Set your production URL in `_config.yml` e.g. `url: https://example.com`.
  - Run `JEKYLL_ENV=production bundle exec jekyll build`.
-->
  - `_config.yml` 에 운영환경 URL 을 설정합니다. 예시, `url: https://example.com`.
  - `JEKYLL_ENV=production bundle exec jekyll build` 를 실행합니다.

<div class="note info">
<!--
  <h5>Changes to <code>_config.yml</code> are not included during automatic regeneration.</h5>
  <p>
    The <code>_config.yml</code> master configuration file contains global configurations
    and variable definitions that are read once at execution time. Changes made to <code>_config.yml</code>
    during automatic regeneration are not loaded until the next execution.
  </p>
  <p>
    Note <a href="../datafiles">Data Files</a> are included and reloaded during automatic regeneration.
  </p>
-->
  <h5>자동으로 다시 생성할 때, <code>_config.yml</code> 의 변경사항은 반영되지 않습니다.</h5>
  <p>
    주 환경설정 파일인 <code>_config.yml</code> 에는 전역 환경설정과 변수들이 정의되어 있으며,
    실행 시점에 한 번만 읽어들입니다. 자동 재생성을 사용하는 중이라도, 완전히 새로 실행하기 전까지는
    <code>_config.yml</code> 의 변경사항을 읽어들이지 않습니다.
  </p>
  <p>
    자동 재생성 과정에서 <a href="../datafiles">데이터 파일</a>은 다시 읽어들입니다.
  </p>
</div>

<div class="note warning">
<!--
  <h5>Destination folders are cleaned on site builds</h5>
  <p>
    The contents of <code>&lt;destination&gt;</code> are automatically
    cleaned, by default, when the site is built. Files or folders that are not
    created by your site will be removed. Files and folders you wish to retain
    in <code>&lt;destination&gt;</code> may be specified within the <code>&lt;keep_files&gt;</code>
    configuration directive.
  </p>
  <p>
    Do not use an important location for <code>&lt;destination&gt;</code>;
    instead, use it as a staging area and copy files from there to your web server.
  </p>
-->
  <h5>Site Destination 폴더는 사이트 빌드 시 초기화됩니다</h5>
  <p>
    사이트 빌드 시에 자동으로 <code>&lt;destination&gt;</code> 안의 파일들을
    지우는 것이 디폴트로 설정되어 있습니다. 사이트에서 생성하지 않는 파일들은
    모두 사라질 것입니다. 환경설정 옵션 <code>&lt;keep_files&gt;</code> 를
    사용해 <code>&lt;destination&gt;</code> 에 그대로 옮길 파일이나 폴더를
    지정할 수 있습니다.
  </p>
  <p>
    중요한 디렉토리는 절대 <code>&lt;destination&gt;</code> 으로 지정하면 안됩니다;
    웹 서버로 옮기기 전에 임시로 파일들을 보관할 경로를 입력하세요.
  </p>
</div>

<!--
Jekyll also comes with a built-in development server that will allow you to
preview what the generated site will look like in your browser locally.
-->
Jekyll 은 개발 서버도 내장하고 있어서, 로컬상에서 브라우저로 접속하여 사이트가
어떻게 생성될지 미리 살펴볼 수 있습니다.

<!--
```sh
jekyll serve
# => A development server will run at http://localhost:4000/
# Auto-regeneration: enabled. Use `--no-watch` to disable.

jekyll serve --livereload
# LiveReload refreshes your browser after a change.

jekyll serve --incremental
# Incremental will perform a partial build in order to reduce regeneration time.

jekyll serve --detach
# => Same as `jekyll serve` but will detach from the current terminal.
#    If you need to kill the server, you can `kill -9 1234` where "1234" is the PID.
#    If you cannot find the PID, then do, `ps aux | grep jekyll` and kill the instance.
```
-->
```sh
jekyll serve
# => 개발서버가 실행됩니다. http://localhost:4000/
# 자동 재생성: 활성화. 비활성화하려면 `--no-watch` 를 사용하세요.

jekyll serve --livereload
# 변경사항이 발생했을 때 LiveReload 기능이 브라우저를 새로고침합니다.

jekyll serve --incremental
# 재생성 소요시간을 줄이기 위해 증분 재생성 기능으로 부분 빌드를 합니다.

jekyll serve --detach
# => `jekyll serve` 와 동일하지만 현재 터미널에 독립적으로 실행됩니다.
#    서버를 종료하려면, `kill -9 1234` 를 실행하세요. "1234" 는 PID 입니다.
#    PID 를 모르겠다면, `ps aux | grep jekyll` 를 실행하고 해당 인스턴스를 종료하세요.
```

<!--
```sh
jekyll serve --no-watch
# => Same as `jekyll serve` but will not watch for changes.
```
-->
```sh
jekyll serve --no-watch
# => `jekyll serve` 와 동일하지만 변경사항을 감시하지 않습니다.
```

<!--
These are just a few of the available [configuration options](../configuration/).
Many configuration options can either be specified as flags on the command line,
or alternatively (and more commonly) they can be specified in a `_config.yml`
file at the root of the source directory. Jekyll will automatically use the
options from this file when run. For example, if you place the following lines
in your `_config.yml` file:
-->
이것들은 [환경설정 옵션](../configuration/)의 극히 일부분만 보여준 것입니다.
다양한 환경설정 옵션들을 위와 같이 명령행에 플래그로 지정할 수 있고 또 다른
(그리고 더 일반적인) 방법으로, 루트 디렉토리의 `_config.yml` 파일에 지정할 수
있습니다. Jekyll 이 작동하기 시작하면, 자동적으로 이 파일에 지정한 옵션들을
사용합니다. 예를 들어, `_config.yml` 파일에 다음과 같이 입력한다면:


```yaml
source:      _source
destination: _deploy
```

<!--
Then the following two commands will be equivalent:
-->
아래 두 명령은 동일합니다:

```sh
jekyll build
jekyll build --source _source --destination _deploy
```

<!--
For more about the possible configuration options, see the
[configuration](../configuration/) page.
-->
환경설정 옵션에 대한 더 자세한 내용은 [환경설정](../configuration/) 페이지를
참고하세요.

<!--
<div class="note info">
  <h5>Call for help</h5>
  <p>
    The <code>help</code> command is always here to remind you of all available options and usage, and also works with the <code>build</code>, <code>serve</code> and <code>new</code> subcommands, e.g <code>jekyll help new</code> or <code>jekyll help build</code>.
  </p>
</div>
-->
<div class="note info">
  <h5>도움을 요청하세요</h5>
  <p>
    사용할 수 있는 모든 옵션과 사용법을 알려주는 <code>help</code> 명령은 언제든지 사용할 수 있으며, 이 명령은 하위 명령어인 <code>build</code>, <code>serve</code>, <code>new</code> 와 함께 사용할 수도 있습니다. 예시, <code>jekyll help new</code> 또는 <code>jekyll help build</code>.
  </p>
</div>

<!--
If you're interested in browsing these docs on-the-go, install the
`jekyll-docs` gem and run `jekyll docs` in your terminal.
-->
만약 이 문서처럼 끊임없이 수정되는 최신 문서에 관심이 많다면, `jekyll-docs` gem
을 설치하고, 터미널에서 `jekyll docs` 를 실행하세요.
