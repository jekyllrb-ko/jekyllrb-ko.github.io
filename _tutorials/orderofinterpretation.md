---
layout: tutorials
permalink: /tutorials/orderofinterpretation/
#title: Order of interpretation
title: 인터프리터 작업 순서
---

<!--
Jekyll's main job is to convert your raw text files into a static website. It does this by rendering Liquid, Markdown, and other transforms as it generates the static HTML output.
-->
Jekyll 의 주된 역할은 당신의 일반 텍스트 파일을 정적 웹사이트로 변환하는 것입니다. 이 작업은 Liquid, 마크다운 렌더링과 다른 변환 과정을 통해 정적인 HTML 을 출력하는 작업입니다.

<!--
In this conversion process, it's important to understand Jekyll's order of interpretation. By "order of interpretation," we mean what gets rendered, in what order, and what rules get applied in converting content.
-->
이 변환 작업에서, Jekyll 인터프리터의 작업 순서를 이해하는 것이 중요합니다. "인터프리터 작업 순서" 란, 변환 작업에서 어디에, 어떤 순서로, 어떤 규칙을 적용하여 렌더링하는가를 의미합니다.

<!--
If an element isn't converting, you can troubleshoot the problem by analyzing the order of interpretation.
-->
변환되지 않는 요소가 있다면, 이 인터프리터 작업 순서를 분석하여 문제를 해결할 수 있을 것입니다.

<!--
## Order of interpretations
-->
## 인터프리터 작업 순서 {#order-of-interpretations}

<!--
Jekyll converts your site in the following order:
-->
Jekyll 은 다음 순서대로 당신의 사이트를 변환합니다:

<!--
1. **Site variables**. Jekyll looks across your files and populates [site variables]({% link _docs/variables.md %}), such as `site`, `page`, `post`, and collection objects. (From these objects, Jekyll determines the values for permalinks, tags, categories, and other details.)

2. **Liquid**. Jekyll processes any [Liquid](https://github.com/Shopify/liquid) formatting in pages that contain [front matter]({% link _docs/frontmatter.md %}). You can identify Liquid as follows:
   * **Liquid tags** start with `{% raw %}{%{% endraw %}` and end with a `{% raw %}%}{% endraw %}`. For example: `{% raw %}{% highlight %}{% endraw %}` or `{% raw %}{% seo %}{% endraw %}`. Tags can define blocks or be inline. Block-defining tags will also come with a corresponding end tag &mdash; for example, `{% raw %}{% endhighlight %}{% endraw %}`.
   * **Liquid variables** start and end with double curly braces. For example: `{% raw %}{{ site.myvariable }}{% endraw %}` or `{% raw %}{{ content }}{% endraw %}`.
   * **Liquid filters** start with a pipe character (`|`) and can only be used within **Liquid variables** after the variable string. For example: the `relative_url` filter in `{% raw %}{{ "css/main.css" | relative_url }}{% endraw %}`.

3. **Markdown**. Jekyll converts Markdown to HTML using the Markdown filter specified in your config file. Files must have a Markdown file extension and front matter in order for Jekyll to convert them.

4. **Layout**. Jekyll pushes content into the layouts specified by the page's front matter (or as specified in the config file). The content from each page gets pushed into the `{% raw %}{{ content }}{% endraw %}` tags within the layouts.

5. **Files**. Jekyll writes the generated content into files in the [directory structure]({% link _docs/structure.md %}) in `_site`. Pages, posts, and collections get structured based on their [permalink]({% link _docs/permalinks.md %}) setting. Directories that begin with `_` (such as `_includes` and `_data`) are usually hidden in the output.
-->
1. **사이트 변수**. Jekyll 은 당신의 파일을 훑어본 후 `site`, `page`, `post`, 콜렉션 객체 등의 [사이트 변수]({% link _docs/variables.md %})에 값을 채워 넣습니다. (Jekyll 은 이 객체들로부터 고유주소와 태그, 카테고리, 그 밖의 다른 값들을 결정합니다.)

2. **Liquid**. Jekyll 은 [머리말]({% link _docs/frontmatter.md %})이 있는 페이지의 모든 [Liquid](https://github.com/Shopify/liquid) 서식을 처리합니다. You can identify Liquid as follows:
   * **Liquid 태그**는 `{% raw %}{%{% endraw %}` 로 시작하여 `{% raw %}%}{% endraw %}` 로 끝납니다. 예시: `{% raw %}{% highlight %}{% endraw %}` 나 `{% raw %}{% seo %}{% endraw %}` 처럼요. 태그는 블록으로도 인라인으로도 정의될 수 있습니다. 블록으로 정의된 태그는 그에 상응하는 종료 태그가 있어야 합니다 &mdash; 예시, `{% raw %}{% endhighlight %}{% endraw %}`.
   * **Liquid 변수**는 이중 중괄호로 시작하고 종료됩니다. 예시: `{% raw %}{{ site.myvariable }}{% endraw %}` 나 `{% raw %}{{ content }}{% endraw %}`.
   * **Liquid 필터**는 파이프 문자 (`|`) 로 시작하고 오직 **Liquid 변수** 안에서 변수 문자열 뒤에 사용될 수 있습니다. 예시: `{% raw %}{{ "css/main.css" | relative_url }}{% endraw %}` 의 `relative_url` 필터.

3. **마크다운**. Jekyll 은 당신의 환경설정 파일에 정의된 마크다운 필터를 사용하여 마크다운을 HTML 로 변환합니다. Jekyll 이 변환하게 하려면 파일이 마크다운 파일 확장자를 가지고 머리말이 있어야 합니다.

4. **레이아웃**. Jekyll 은 페이지의 머리말(이나 환경설정 파일)에 지정된 레이아웃에 컨텐츠를 집어 넣습니다. 레이아웃 안의 `{% raw %}{{ content }}{% endraw %}` 태그에 페이지의 컨텐츠가 삽입됩니다.

5. **파일**. Jekyll 은 생성된 컨텐츠를 `_site` 의 [디렉토리 구조]({% link _docs/structure.md %})에 맞게 파일로 저장합니다. 페이지와 포스트, 콜렉션은 각 파일의 [고유주소]({% link _docs/permalinks.md %}) 설정에 맞추어 위치가 결정됩니다. 일반적으로 문자 `_` 로 시작하는 디렉토리 (`_includes` 와 `_data`) 는 생성된 사이트에서 보이지 않습니다.

<!--
## Scenarios where incorrect configurations create problems
-->
## 잘못된 설정으로 발생하는 문제점에 대한 시나리오 {#scenarios-where-incorrect-configurations-create-problems}

<!--
For the most part, you don't have to think about the order of interpretation when building your Jekyll site. These details only become important to know when something isn't rendering.
-->
보통은, Jekyll 사이트를 빌드하기 위해 반드시 인터프리터 작업 순서를 생각해보아야하는 것은 아닙니다. 무언가 렌더링 작업이 올바르지 않을 때에만 지금 설명하는 것들에 대해 생각해보세요.

<!--
The following scenarios highlight potential problems you might encounter. These problems come from misunderstanding the order of interpretation and can be easily fixed.
-->
아래는 당신이 마주칠지도 모를 문제점을 부각시킨 시나리오들입니다. 인터프리터 작업 순서를 제대로 이해하지 못했을 때 발생하는 이러한 문제점들은 쉽게 고칠 수 있습니다.

<!--
### Variable on page not rendered because variable is assigned in layout
-->
### 레이아웃에 사용된 변수가 렌더링되지 않음

<!--
In your layout file (`_layouts/default.html`), suppose you have a variable assigned:
-->
레이아웃 파일 (`_layouts/default.html`) 에, 변수를 할당했다고 가정합시다:

{% raw %}
```liquid
{% assign myvar = "joe" %}
```
{% endraw %}

<!--
On a page that uses the layout, you reference that variable:
-->
이 레이아웃을 사용하는 페이지에서, 해당 변수를 참조합니다:

{% raw %}
```liquid
{{ myvar }}
```
{% endraw %}

<!--
The variable won't render because the page's order of interpretation is to render Liquid first and later process the Layout. When the Liquid rendering happens, the variable assignment isn't available.
-->
인터프리터 작업 순서에 따라 Liquid 렌더링을 먼저 한 뒤에 레이아웃을 처리하기 때문에 그 변수는 렌더링되지 않습니다. Liquid 렌더링 시점에, 해당 변수에 값이 할당되어있지 않습니다.

<!--
To make the code work, you could put the variable assignment into the page's front matter.
-->
이 코드를 작동시키려면, 페이지의 머리말에서 변수를 할당하는 방법이 있습니다.

<!--
### Markdown in include file not processed
-->
### 조각파일에서 마크다운이 처리되지 않음

<!--
Suppose you have a Markdown file at `_includes/mycontent.md`. In the Markdown file, you have some Markdown formatting:
-->
마크다운 파일 `_includes/mycontent.md` 를 가지고 있다고 가정합시다. 이 파일에는, 마크다운 형식으로 작성된 내용이 들어있습니다:

<!--
```markdown
This is a list:
* first item
* second item
```
-->
```markdown
이것은 목록입니다:
* 첫 번째 항목
* 두 번째 항목
```

<!--
You include the file into an HTML file as follows:
-->
다음과 같이 해당 파일을 HTML 파일에 삽입합니다:

{% raw %}
```liquid
{% include mycontent.md %}
```
{% endraw %}

<!--
The Markdown is not processed because first the Liquid (`include` tag) gets processed, inserting `mycontent.md` into the HTML file. *Then* the Markdown would get processed.
-->
이 마크다운이 처리되지 않는 이유는, HTML 파일에 `mycontent.md` 를 삽입하는 Liquid (`include` 태그) 가 먼저 처리되기 때문입니다. *그 다음* 마크다운 처리작업이 수행됩니다.

<!--
But because the content is included into an *HTML* page, the Markdown isn't rendered. The Markdown filter processes content only in Markdown files.
-->
그러나 *HTML* 페이지에 삽입되었기 때문에, 마크다운이 렌더링되지 않은 것도 있습니다. 마크다운 필터는 오직 마크다운 파일의 내용만 처리합니다.

<!--
To make the code work, use HTML formatting in includes that are inserted into HTML files.
-->
이 코드를 작동시키려면, HTML 파일에 삽입되는 조각파일에는 HTML 문법을 사용하세요.

<!--
Note that `highlight` tags don't require Markdown to process. Suppose your include contains the following:
-->
`highlight` 태그를 처리하는데에 마크다운은 필요하지 않다는 점을 기억하세요. 다음과 같은 내용을 삽입한다고 가정해봅시다:

{% raw %}
```liquid
{% highlight javascript %}
console.log('alert');
{% endhighlight %}
```
{% endraw %}

<!--
The `highlight` tag *is* Liquid. (Liquid passes the content to Rouge or Pygments for syntax highlighting.) As a result, this code will actually convert to HTML with syntax highlighting. Jekyll does not need the Markdown filter to process `highlight` tags.
-->
`highlight` 태그는 Liquid 가 *맞습니다*. (구문 강조를 위해 Rouge 나 Pyments 에 내용을 전달하는 것은 Liquid 입니다.) 그 결과로, 이 코드는 실제로 구문 강조 처리가 된 HTML 로 변환될 것입니다.

<!--
### Liquid mixed with JavaScript isn't rendered
-->
### JavaScript 와 함께 있을 때 Liquid 가 렌더링 되지 않음

<!--
Suppose you try to mix Liquid's `assign` tag with JavaScript, like this:
-->
Liquid 의 `assign` 태그를 JavaScript 와 함께 사용하려 한다고 가정해봅시다, 이렇게 말이죠:

{% raw %}
```javascript
<button onclick="someFunction()">Click me</button>

<p id="intro"></p>

<script>
{% assign someContent = "This is some content" %}
function someFunction() {
    document.getElementById("intro").innerHTML = someContent;
}
</script>
```
{% endraw %}

<!--
This won't work because the `assign` tag is only available during the Liquid rendering phase of the site. In this JavaScript example, the script executes when a user clicks a button ("Click me") on the HTML page. At that time, the Liquid logic is no longer available, so the `assign` tag wouldn't return anything.
-->
`assign` 태그는 오직 Liquid 렌더링 단계에서만 사용되기 때문에 위 코드는 동작하지 않습니다. 이 JavaScript 예제에서는, HTML 페이지의 ("클릭하세요") 버튼을 사용자가 클릭했을 때 스크립트가 실행됩니다. 그 실행 시점에, Liquid 로직은 사용되지 않기 때문에, `assign` 태그는 어떤 값도 출력하지 않습니다.

<!--
However, you can use Jekyll's site variables or Liquid to *populate* a script that is executed at a later time. For example, suppose you have the following property in your front matter: `someContent: "This is some content"`. You could do this:
-->
하지만, 이와 같이 나중에 실행될 스크립트를 Jekyll 의 사이트 변수나 Liquid 를 사용해서 *만들어낼* 수 있습니다. 예를 들어, 머리말에 이와 같은 속성을 가지고 있다고 생각해봅시다: `someContent: "This is some content"`. 아래 코드를 보세요:

{% raw %}
```js
<button onclick="someFunction()">Click me</button>

<p id="intro"></p>

<script>

function someFunction() {
    document.getElementById("intro").innerHTML = "{{ page.someContent }}";
}
</script>
```
{% endraw %}

<!--
When Jekyll builds the site, this `someContent` property populates the script's values, converting `{% raw %}{{ page.someContent }}{% endraw %}` to `"This is some content"`.
-->
Jekyll 이 사이트를 빌드할 때, 이 `someContent` 속성은 `{% raw %}{{ page.someContent }}{% endraw %}` 를 `"This is some content"` 로 변환해서 스크립트에 사용되는 값으로 만듭니다.

<!--
The key to remember is that Liquid renders when Jekyll builds your site. Liquid is not available at run-time in the browser when a user executes an event.
-->
기억해야할 것은 Jekyll 이 사이트를 빌드할 때 Liquid 렌더링이 수행된다는 것입니다. 사용자가 브라우저로 이벤트를 발생시키는 런타임 시점에는 Liquid 가 사용되지 않습니다.

<!--
## Note about using Liquid in YAML
-->
## YAML 에 Liquid 사용에 대한 주의사항 {#note-about-using-liquid-in-yaml}

<!--
There's one more detail to remember: Liquid does not render when embedded in YAML files or front matter. (This isn't related to order of interpretation, but it's worth mentioning because it's a common question about element rendering.)
-->
기억해야할 것이 하나 더 있습니다: YAML 파일이나 머리말 안에 있는 Liquid 는 렌더링되지 않습니다. (인터프리터 작업 순서과 관계 없는 내용이지만, 렌더링 관련으로 자주 질문받는 내용이기 때문에 여기서 언급합니다.)

<!--
For example, suppose you have a `highlight` tag in your `_data/mydata.yml` file:
-->
예를 들어, `_data/mydata.yml` 이라는 파일을 가지고 있고 `highlight` 태그를 사용했다고 가정해봅시다:

{% raw %}
```liquid
myvalue: >
  {% highlight javascript %}
  console.log('alert');
  {% endhighlight %}
```
{% endraw %}

<!--
On a page, you try to insert the value:
-->
페이지에서, 당신을 이 값을 삽입하려고 합니다:

{% raw %}
```liquid
{{ site.data.mydata.myvalue }}
```
{% endraw %}

<!--
This would render only as a string rather than a code sample with syntax highlighting. To make the code render, consider using an include instead.
-->
이렇게 하면 구문 강조된 코드 샘플이 아닌 단순한 문자열이 출력됩니다. 코드가 렌더링되게 하려면, 조각파일을 사용하는 것을 고려해보세요.
