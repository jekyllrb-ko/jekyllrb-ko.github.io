---
#title: Extras
title: 부가기능
permalink: /docs/extras/
---

<!--
There are a number of (optional) extra features that Jekyll supports that you
may want to install, depending on how you plan to use Jekyll.
-->
Jekyll 이 추가적으로 지원하는 기능 (선택사항) 이 몇 가지 있습니다. 당신이 Jekyll
을 어떻게 사용할 것인지 그 계획에 따라 원하는 기능을 골라 설치하면 됩니다.

<!--
## Web Highlights and Commenting 
-->
## 웹상에서 강조표시와 댓글

<!--
Register your site with [txtpen](https://txtpen.com). Then append 
-->
당신의 사이트를 [txtpen](https://txtpen.com) 에 등록하세요. 다음 아래 내용을

```html
<script src="https://txtpen.com/embed.js?site=<your site name>"></script>
```

<!--
to your template files in `/_layout` folder.
-->
사이트의 `_layout` 폴더에 있는 템플릿 파일에 추가하세요.

<!--
## Math Support
-->
## 수학 지원

<!--
Kramdown comes with optional support for LaTeX to PNG rendering via [MathJax](https://www.mathjax.org) within math blocks. See the Kramdown documentation on [math blocks](http://kramdown.gettalong.org/syntax.html#math-blocks) and [math support](http://kramdown.gettalong.org/converter/html.html#math-support) for more details. MathJax requires you to include JavaScript or CSS to render the LaTeX, e.g.
-->
Kramdown 은 LaTeX 를 지원하기 때문에 수식 블록에 [MathJax](https://www.mathjax.org) 를 사용해서 PNG 렌더링이 가능합니다. 더 자세한 내용은 Kramdown 문서의 [Math Blocks](http://kramdown.gettalong.org/syntax.html#math-blocks) 와 [Math Support](http://kramdown.gettalong.org/converter/html.html#math-support) 를 살펴보세요. MathJax 는 LaTeX 렌더링을 위해 JavaScript 나 CSS 를 필요로 하는데, 아래는 그 예시입니다.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.0/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
```

<!--
For more information about getting started, check out [this excellent blog post](http://gastonsanchez.com/visually-enforced/opinion/2014/02/16/Mathjax-with-jekyll/).
-->
MathJax 입문에 관련된 더 많은 정보를 담고있는 [훌륭한 블로그 게시물](http://gastonsanchez.com/visually-enforced/opinion/2014/02/16/Mathjax-with-jekyll/)이 있으니 참고하세요.

<!--
## Alternative Markdown Processors
-->
## 다른 마크다운 처리기

<!--
See the Markdown section on the [configuration page](/docs/configuration/#markdown-options) for instructions on how to use and configure alternative Markdown processors, as well as how to create [custom processors](/docs/configuration/#custom-markdown-processors).
-->
[환경설정 페이지](/docs/configuration/#markdown-options)의 마크다운 섹션을 참고하세요. 다른 마크다운 처리기의 설정과 사용방법 뿐만 아니라 [커스텀 마크다운 처리기](/docs/configuration/#custom-markdown-processors)를 만드는 방법도 설명되어 있습니다.
