---
#title: Quickstart
title: 빠른 시작
permalink: /docs/
redirect_from:
  - /docs/home/
  - /docs/quickstart/
  - /docs/extras/
---
<!--
Jekyll is a static site generator. You give it text written in your
favorite markup language and it uses layouts to create a static website. You can
tweak how you want the site URLs to look, what data gets displayed on the
site, and more.
-->
Jekyll 은 정적 사이트 생성기입니다. 당신이 즐겨 사용하는 마크업 언어로
작성된 텍스트를 Jekyll 에 넘겨주면 레이아웃을 사용해 정적 웹사이트를 생성합니다.
사이트 URL 의 형식이나 어떤 데이터를 사이트에 표시할 것인지 등, 여러 동작을
조정할 수 있습니다.

<!--
## Prerequisites
-->
## 전제조건 {#prerequisites}

<!--
See [requirements](/docs/installation/#requirements).
-->
[준비물](/docs/installation/#requirements) 섹션을 읽어보세요.

<!--
## Instructions
-->
## 절차 {#instructions}

<!--
1. Install a full [Ruby development environment](/docs/installation/).
2. Install Jekyll and [bundler](/docs/ruby-101/#bundler) [gems](/docs/ruby-101/#gems).
```
gem install jekyll bundler
```
3. Create a new Jekyll site at `./myblog`.
```
jekyll new myblog
```
4. Change into your new directory.
```
cd myblog
```
5. Build the site and make it available on a local server.
```
bundle exec jekyll serve
```
6. Browse to [http://localhost:4000](http://localhost:4000){:target="_blank"}
-->
1. 완전한 [루비 개발환경](/docs/installation/)을 설치합니다.
2. Jekyll 과 [Bundler](/docs/ruby-101/#bundler) [젬](/docs/ruby-101/#gems)을 설치합니다.
```
gem install jekyll bundler
```
3. `./myblog` 에 새 Jekyll 사이트를 생성합니다.
```
jekyll new myblog
```
4. 생성된 디렉토리로 이동합니다.
```
cd myblog
```
5. 사이트를 빌드하고 로컬 서버에 적용합니다.
```
bundle exec jekyll serve
```
6. 이제 브라우저로 [http://localhost:4000](http://localhost:4000){:target="_blank"} 에 접속합니다.

<!--
If you encounter any errors during this process, see the
[troubleshooting](/docs/troubleshooting/#configuration-problems) page. Also,
make sure you've installed the development headers and other prerequisites as
mentioned on the [requirements](/docs/installation/#requirements) page.
-->
만약 위 과정 중 문제가 발생한다면,
[문제해결](/docs/troubleshooting/) 페이지를 살펴보세요. 또한,
[준비물](/docs/installation/#requirements) 페이지에서 설명하는
개발 헤더나 기타 전제 조건이 설치되었는지도 확인해보세요.
