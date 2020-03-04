---
#title:  Command Line Usage
title: 명령행 사용법
permalink: /docs/usage/
---

<!--
The Jekyll gem makes a `jekyll` executable available to you in your terminal.
-->
루비 젬 Jekyll 은 터미널에서 사용할 수 있는 실행파일 `jekyll` 을 만들어줍니다.

<!--
You can use this command in a number of ways:
-->
이 명령은 다양한 방식으로 사용할 수 있습니다:

<!--
* `jekyll new PATH` - Creates a new Jekyll site with default gem-based theme at specified path. The directories will be created as necessary.
* `jekyll new PATH --blank` - Creates a new blank Jekyll site scaffold at specified path.
* `jekyll build` or `jekyll b` - Performs a one off build your site to `./_site` (by default)
* `jekyll serve` or `jekyll s` - Builds your site any time a source file changes and serves it locally
* `jekyll doctor` - Outputs any deprecation or configuration issues
* `jekyll clean` - Removes all generated files: destination folder, metadata file, Sass and Jekyll caches.
* `jekyll help` - Shows help, optionally for a given subcommand, e.g. `jekyll help build`
* `jekyll new-theme` - Creates a new Jekyll theme scaffold
-->
* `jekyll new PATH` - 지정된 경로에 기본 젬-기반 테마로 새 Jekyll 사이트를 생성한다. 필요한 경우 디렉토리가 생성된다.
* `jekyll new PATH --blank` - 지정된 경로에 새 Jekyll 사이트의 비어있는 틀을 생성한다.
* `jekyll build` 또는 `jekyll b` - `./_site` (기본값) 에 사이트 빌드를 수행한다
* `jekyll serve` 또는 `jekyll s` - 소스 파일이 변경되었을 때 사이트를 빌드하고 로컬 서버를 실행한다
* `jekyll doctor` - 환경설정이나 소스코드에 관련된 문제점을 출력한다
* `jekyll clean` - 빌드 작업으로 생성된 파일을 제거한다: 결과 폴더, 메타 데이터 파일, Sass 와 Jekyll 캐시.
* `jekyll help` - 전체 또는 주어진 하위 명령어의 도움말 출력한다. 예시, `jekyll help build`
* `jekyll new-theme` - 새 Jekyll 테마 틀을 생성한다

<!--
Typically you'll use `jekyll serve` while developing locally and `jekyll build` when you need to generate the site for production.
-->
일반적으로 로컬 환경에서 개발이 진행중일때는 `jekyll serve` 를 사용하고 운영 환경에 사이트를 생성해야할 때는 `jekyll build` 를 사용합니다.

<!--
To change Jekyll's default build behavior have a look through the [configuration options](/docs/configuration/).
-->
Jekyll 의 기본 빌드 방식을 변경하려면 [환경설정 옵션](/docs/configuration/)을 살펴보세요.
