---
layout: docs
title: 부가기능
permalink: /docs/extras/
---

Jekyll 이 추가적으로 지원하는 기능 (선택사항) 이 몇 가지 있습니다. 당신이 Jekyll
을 어떻게 사용할 것인지 그 계획에 따라 원하는 기능을 골라 설치하면 됩니다.

## 수학 지원

Kramdown 은 LaTeX 를 지원하기 때문에 수식 블록에 [MathJax](http://www.mathjax.org/) 를 사용해서 PNG 렌더링이 가능합니다. 더 자세한 내용은 Kramdown 문서의 [Math Blocks](http://kramdown.gettalong.org/syntax.html#math-blocks) 와 [Math Support](http://kramdown.gettalong.org/converter/html.html#math-support) 를 살펴보세요. MathJax 는 LaTeX 렌더링을 위해 JavaScript 나 CSS 를 필요로 하는데, 아래는 그 예시입니다.

{% highlight html %}
<script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
{% endhighlight %}

MathJax 입문에 관련된 더 많은 정보를 담고있는 [훌륭한 블로그 게시물](http://gastonsanchez.com/blog/opinion/2014/02/16/Mathjax-with-jekyll.html)이 있으니 참고하세요.

## 다른 마크다운 처리기

[환경설정 페이지](/docs/configuration/#markdown-options)의 마크다운 섹션을 참고하세요. 다른 마크다운 처리기의 설정과 사용방법 뿐만 아니라 [사용자 고유의 마크다운 처리기](/docs/configuration/#custom-markdown-processors)를 만드는 방법도 설명되어 있습니다.
