---
#title: Tags
title: 태그
permalink: /docs/plugins/tags/
---

<!--
If you’d like to include custom liquid tags in your site, you can do so by
hooking into the tagging system. Built-in examples added by Jekyll include the
`highlight` and `include` tags. Below is an example of a custom liquid tag that
will output the time the page was rendered:
-->
사이트에 자신의 Liquid 태그를 사용하고 싶다면,
태그 시스템의 Hook 을 사용하면 됩니다.
Jekyll 에 내장된 `highlight` 와 `include` 가 바로 그 예입니다.
다음 예제는 페이지가 렌더링된 시간을 출력해주는 Liquid 태그입니다:

```ruby
module Jekyll
  class RenderTimeTag < Liquid::Tag

    def initialize(tag_name, text, tokens)
      super
      @text = text
    end

    def render(context)
      "#{@text} #{Time.now}"
    end
  end
end

Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTag)
```

<!--
At a minimum, liquid tags must implement:
-->
Liquid 태그는 최소한 다음 메소드는 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Method</th>
      <th>Description</th>
-->
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>render</code></p>
      </td>
      <td>
<!--
        <p>Outputs the content of the tag.</p>
-->
        <p>태그 컨텐츠를 출력합니다.</p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
You must also register the custom tag with the Liquid template engine as
follows:
-->
그리고 다음과 같이 Liquid 템플릿 엔진에 태그를 등록해야
합니다:

```ruby
Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTag)
```

<!--
In the example above, we can place the following tag anywhere in one of our
pages:
-->
이렇게 하면, 페이지의 어느 곳에서나 다음과 같이 태그를 사용할 수
있습니다:

{% raw %}
```ruby
<p>{% render_time page rendered at: %}</p>
```
{% endraw %}

<!--
And we would get something like this on the page:
-->
그러면 다음과 같은 결과를 얻을 수 있습니다:

```html
<p>page rendered at: Tue June 22 23:38:47 –0500 2010</p>
```

<!--
## Tag Blocks
-->
## 태그 블록

<!--
The `render_time` tag seen above can also be rewritten as a tag block by 
inheriting the `Liquid::Block` class. Look at the example below:
-->
위 예시에 있는 `render_time` 태그는 `Liquid::Block` 클래스를 상속받아
태그 블록으로도 작성할 수 있습니다. 아래 예시를 보세요:

```ruby
module Jekyll
  class RenderTimeTagBlock < Liquid::Block

    def render(context)
      text = super
      "<p>#{text} #{Time.now}</p>"
    end

  end
end

Liquid::Template.register_tag('render_time', Jekyll::RenderTimeTagBlock)
```

<!--
We can now use the tag block anywhere:
-->
이제 어디에서나 이 태그 블록을 사용할 수 있습니다:

{% raw %}
```liquid
{% render_time %}
page rendered at:
{% endrender_time %}
```
{% endraw %}

<!--
And we would still get the same output as above on the page:
-->
그리고 여전히 위 예시와 동일한 내용을 출력합니다:

```html
<p>page rendered at: Tue June 22 23:38:47 –0500 2010</p>
```

<div class="note info">
<!--
  <p>In the above example, the tag block and the tag are both registered with 
  the name <code>render_time</code> but to register a tag and a tag block using 
  the same name in the same project is not recommended as this may lead to 
  conflicts.</p>
-->
  <p>위 예시에서, 태그 블록과 태그 모두가 <code>render_time</code> 라는 이름으로
  정의되었는데, 하나의 프로젝트에서 태그와 태그 블록을 같은 이름으로 정의하는
  것은 충돌을 야기할 수 있으므로 권장하지
  않습니다.</p>
</div>
