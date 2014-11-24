---
layout: docs
title: 빠른시작 설명서
prev_section: home
next_section: installation
permalink: /docs/quickstart/
---

빨리 실행해보고자 하는 분들을 위해, 가장 기본적인 형태로 Jekyll 사이트를 구축하고 실행하는 방법을 먼저 알려드립니다.

{% highlight bash %}
~ $ gem install jekyll
~ $ jekyll new myblog
~ $ cd myblog
~/myblog $ jekyll serve
# => Now browse to http://localhost:4000
{% endhighlight %}

현재 디렉토리에 Jekyll 을 구성하려면, 새 디렉토리 이름 대신 `jekyll new .` 을 실행하세요.

여기까진 별로 특별한 것이 없습니다. 하지만, 블로그 포스트를 생성하거나 템플릿과
레이아웃을 다룰 때, 머리말을 사용하거나 Jekyll 의 다양한 환경설정 옵션들을
활용할 때, 진짜 마술같은 일이 벌어집니다.

만약 문제가 발생한다면, [준비물 설치][Installation]가 모두 올바르게 되어 있는지
확인해보세요.

[Installation]: /docs/installation/
