---
layout: docs
title: Windows 에서 Jekyll
prev_section: configuration
next_section: posts
permalink: /docs/windows/
---

Windows 가 공식적으로 지원되는 플랫폼은 아니지만, 몇 가지만 손보면 Jekyll 을
실행할 수 있습니다. 이 페이지의 목적은 Windows 사용자에 의해서 발굴된 정보들을
수집하는 것입니다.

## 설치

Julian Thilo 가 작성한 [Jekyll 을 Windows 에서 실행][windows-installation]하는
방법은 대체적으로 잘 동작하는 것으로 보입니다.

## 인코딩

만약 UTF-8 인코딩을 사용한다면, 문서 안에 `BOM` 헤더를 사용하지 않아야 합니다.
그렇지 않으면 Jekyll 에 아주, 아주 안 좋은 일이 벌어집니다. 이 문제는 Windows
에서 Jekyll 을 실행하는 경우에만 해당됩니다.

그리고, 사이트 생성 단계에서 "Liquid Exception: Incompatible character encoding"
에러가 발생하는 경우엔, 콘솔창의 코드 페이지를 UTF-8 로 바꿔야 할 수도 있습니다.
다음과 같이 입력하면 됩니다:

{% highlight bash %}
$ chcp 65001
{% endhighlight %}

[windows-installation]: http://jekyll-windows.juthilo.com/

## 자동-재생성

Jekyll v1.3.0 부터 `listen` gem 을 사용하여, 생성이나 미리보기 시에 `--watch`
스위치가 설정되면, 변경사항을 감시하게 되었습니다. UNIX 시스템에는 `listen` 이
기본 지원되지만, Windows 에서 호환되려면 더 필요한 gem 이 있습니다. 사이트의
Gemfile 에 다음 내용을 추가합니다:

{% highlight ruby %}
gem 'wdm', '~> 0.1.0' if Gem.win_platform?
{% endhighlight %}
