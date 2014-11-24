---
layout: docs
title: 머리말
prev_section: configuration
next_section: posts
permalink: /docs/frontmatter/
---

Jekyll 의 수 많은 멋진 기능들 중 그 첫 번째는 바로 머리말입니다. Jekyll 은
[YAML](http://yaml.org/) 머리말 블록이 포함된 모든 파일을 특별한 파일로 인식하여
처리합니다. 머리말은 반드시 파일의 맨 처음에, 3 개의 대쉬문자로 감싸서 올바른
YAML 형식으로 작성되어야 합니다.
가장 기본적인 형태를 예로 들면 다음과 같습니다:

{% highlight yaml %}
---
layout: post
title: Blogging Like a Hacker
---
{% endhighlight %}

이 대쉬문자 사이에 사전-정의 변수 (설명은 아래를 참고하세요) 를 사용할 수 있고,
심지어는 자신만의 고유 변수를 정의할 수도 있습니다. 이 변수들은 해당 파일은 물론
해당 페이지 (또는 포스트) 에 연결된 레이아웃이나 include 파일에서 Liquid 태그를
사용하여 접근할 수 있습니다.


<div class="note warning">
  <h5>UTF-8 Character Encoding Warning</h5>
  <p>
    만일 UTF-8 인코딩을 사용한다면, BOM 헤더 문자가 포함되어 있지는 않는지
    확인하세요. 그렇지 않으면 Jekyll 에 아주 아주 안좋은 일이 벌어집니다. 이
    문제는 <a href="../windows/">Jekyll 을 Windows 에서 사용</a>하는 경우에만
    해당됩니다.
  </p>
</div>

<div class="note">
  <h5>ProTip™: 머리말의 변수는 선택사항입니다</h5>
  <p>
    만약 <a href="../variables/">Liquid 태그와 변수</a>를 사용하고 싶은데
    머리말에 아무것도 입력할 필요가 없다면, 빈 칸으로 남겨두세요! 대쉬문자
    내부에 아무 내용이 없어도, Jekyll 은 해당 파일에 대한 처리를 수행할
    것입니다. (이것은 CSS 나 RSS 피드같은 파일에 유용합니다!)
  </p>
</div>

## 사전-정의 전역 변수

페이지 (또는 포스트) 의 머리말에 사용할 수 있는 다양한 사전-정의 전역 변수가
있습니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>layout</code></p>
      </td>
      <td>
        <p>

          사용할 레이아웃 파일을 지정합니다. 파일명에서 확장자를 제외한 나머지
          부분을 사용하세요. 반드시 <code>_layouts</code> 디렉토리에 레이아웃
          파일이 있어야 합니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>permalink</code></p>
      </td>
      <td>
        <p>

          생성된 블로그 포스트의 기본 URL 인
          <code>/year/month/day/title.html</code>을 사용하지 않고 다른 URL 을
          입력하면, 이것이 최종 URL 로 사용됩니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>published</code></p>
      </td>
      <td>
        <p>
          사이트가 생성되었을 때 특정 포스트가 나타나지 않게 하려면 false 로
          지정합니다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p style="margin-bottom: 5px;"><code>category</code></p>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>

          포스트를 특정 폴더에 넣지 않고, 포스트가 속해야 하는 카테고리를 하나
          또는 그 이상 지정할 수 있습니다. 사이트가 생성될 때, 포스트는 그냥
          평범하게 이 카테고리들에 속한 것처럼 동작합니다.
          이 categories (복수형) 은 <a
          href="http://en.wikipedia.org/wiki/YAML#Lists">YAML 리스트</a> 또는 공백으로
          구분된 문자열로 지정할 수 있습니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>tags</code></p>
      </td>
      <td>
        <p>

          카테고리와 유사하게, 하나 이상의 태그를 포스트에 추가할 수 있습니다.
          또한, YAML 리스트 또는 공백문자로 구분하여 여러 태그를 지정할 수
          있습니다.

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>


## 사용자-정의 변수

변환 도중에, 사전-정의된 변수가 아닌 모든 머리말 변수들은 Liquid 템플릿 엔진에
의해 처리됩니다.
예를 들어, title 을 설정하면, 레이아웃에서 페이지 제목이 필요할 때 사용할 수
있습니다:

{% highlight html %}
<!DOCTYPE HTML>
<html>
  <head>
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
  </head>
  <body>
    ...
{% endhighlight %}

## 포스트의 사전-정의 변수

포스트에서 사용할 수 있는 특별한 머리말 변수들입니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p>
          포스트 이름에 지정한 날짜보다 이 변수에 지정한 날짜가 우선시됩니다.
          포스트를 올바르게 정렬하기 위해 사용할 수 있습니다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
  <h5>ProTip™: 같은 일을 반복하지 마세요</h5>
  <p>
    자주 사용하는 머리말 변수를 계속 반복해서 입력하고 싶지 않으면, 해당 변수에
    대한 <a href="../configuration/#front-matter-defaults" title="Front Matter defaults">기본값</a>을
    정의하고, 필요한 곳에서만 다른 값으로 덮어쓰세요.
    사전-정의 변수나 사용자-정의 변수 모두 사용할 수 있습니다.
  </p>
</div>
