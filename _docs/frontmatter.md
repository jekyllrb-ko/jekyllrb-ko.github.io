---
layout: docs
title: 머리말
permalink: /docs/frontmatter/
---

Jekyll 의 수 많은 멋진 기능들 중 그 첫 번째는 바로 머리말입니다. Jekyll 은
[YAML](http://yaml.org/) 머리말 블록을 가진 모든 파일을 특별한 파일로 인식하여
처리합니다. 머리말은 반드시 올바른 YAML 형식으로 작성되어야 하며, 대시문자 3
개로 감싸서 파일의 맨 첫 부분에 위치해야 합니다. 가장 기본적인 형태를 예로 들면
다음과 같습니다:

{% highlight yaml %}
---
layout: post
title: Blogging Like a Hacker
---
{% endhighlight %}

이 대시문자 사이에 사전-정의 변수 (설명은 아래를 참고하세요) 를 사용할 수 있고,
심지어 자신만의 고유 변수를 정의하는 것도 가능합니다. 해당 파일은 물론 해당
페이지 또는 포스트에 연결된 레이아웃이나 include 파일에서도 Liquid 태그를
사용하여 이 변수들에 접근할 수 있습니다.


<div class="note warning">
  <h5>UTF-8 문자 인코딩 주의사항</h5>
  <p>
    만일 UTF-8 인코딩을 사용한다면, BOM 헤더 문자가 포함되어 있지는 않는지
    확인하세요. 그렇지 않으면 Jekyll 에 아주, 아주 안좋은 일이 벌어집니다.
    이것은 <a href="../windows/">Jekyll 을 Windows 에서 사용</a>할 때에만
    발생하는 문제입니다.
  </p>
</div>

<div class="note">
  <h5>ProTip™: 머리말의 변수는 필수가 아닙니다</h5>
  <p>
    만약 <a href="../variables/">Liquid 태그와 변수</a>는 사용하고 싶은데
    머리말에는 넣을만한 내용이 하나도 없다면, 그냥 비워두세요! 3 중 대시 사이에
    아무 내용이 없어도, Jekyll 은 해당 파일을 처리합니다. (CSS 나 RSS 피드같은
    파일에 유용합니다!)
  </p>
</div>

## 사전-정의 전역 변수

페이지 또는 포스트의 머리말에 사용할 수 있는 다양한 사전-정의 전역 변수가
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

          사용할 레이아웃 파일을 지정한다. 레이아웃 파일명에서 확장자를 제외한
          나머지 부분만 입력한다. 레이아웃 파일은 반드시 <code>_layouts</code>
          디렉토리에 존재해야 한다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>permalink</code></p>
      </td>
      <td>
        <p>

          생성된 블로그 포스트 URL 을 사이트 전역 스타일 (디폴트 설정:
          <code>/year/month/day/title.html</code>)이 아닌 다른 스타일로 만드려면, 이
          변수를 사용하여 최종 URL 을 설정하면 된다.

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
          설정하라.
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
          또는 그 이상 지정할 수 있다. 사이트가 생성될 때, 포스트는 그냥
          평범하게 이 카테고리들에 속한 것처럼 동작한다. 두 개 이상의
          카테고리들을 지정할 때에는 <a
          href="http://en.wikipedia.org/wiki/YAML#Lists">YAML 리스트</a> 또는
          쉼표로 구분된 문자열을 사용한다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>tags</code></p>
      </td>
      <td>
        <p>

          카테고리와 유사하게, 하나 이상의 태그를 포스트에 추가할 수 있다. 또
          카테고리와 동일하게, YAML 리스트 또는 쉼표로 구분된 문자열로 지정할
          수도 있다.

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>


## 사용자-정의 변수

변환 작업 중, 사전-정의된 변수가 아닌 모든 머리말 변수들은 데이터로 정리되어
Liquid 템플릿 엔진에 전달됩니다. 예를 들어, title 변수를 설정하면 레이아웃에서
페이지 제목을 입력할 때 사용할 수 있습니다:


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
          여기에 지정한 날짜가 포스트 이름에 있는 날짜보다 더 우선순위가 높다.
          포스트를 올바르게 정렬하기 위해 사용할 수 있는 기능이다. 날짜 형식은
          <code>YYYY-MM-DD HH:MM:SS +/-TTTT</code> 이다; 시간, 분, 초와 타임존
          오프셋은 선택사항이다.
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
    정의하고, 필요한 곳에서만 다른 값으로 덮어쓰세요. 사전-정의 변수와
    사용자-정의 변수 모두 이 방법을 적용할 수 있습니다.
  </p>
</div>
