---
layout: docs
title: 디렉토리 구조
prev_section: usage
next_section: configuration
permalink: /docs/structure/
---

Jekyll 의 핵심 역할은 텍스트 변환 엔진입니다. 이 시스템의 배경 컨셉은 다음과
같습니다: 자신이 즐겨 사용하는 마크업 언어 (Markdown 이나 Textile 또는 일반
HTML) 로 작성된 문서를 Jekyll 에 전달하면, Jekyll 은 이 문서를 다양한
레이아웃으로 포장합니다. 이 과정에 포함된 사이트 URL 구성 방식, 데이터가
레이아웃에 배치되는 방식 등 다양한 작동방식을 원하는대로 조정할 수 있습니다.
텍스트 파일을 작성하는 것만으로 이 모든 일들이 가능하며, 최종적으로 정적 웹
사이트가 생성됩니다.

기본적인 Jekyll 사이트는 보통 이렇게 생겼습니다:

{% highlight bash %}
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
{% endhighlight %}

각각 하는 일의 개요는 다음과 같습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>파일 / 디렉토리</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>_config.yml</code></p>
      </td>
      <td>
        <p>

          <a href="../configuration/">환경설정</a> 정보를 보관합니다. 명령어에
          직접 옵션을 지정하여 실행할 수도 있지만, 그렇게 따로 외워두는 것보다
          이 파일에 정의해두는 편이 더 쉽습니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_drafts</code></p>
      </td>
      <td>
        <p>

          초안은 게시하기 전 상태의 포스트입니다. 파일명 형식에 날짜가 없습니다: <code>title.MARKUP</code>. <a href="../drafts/">초안 활용하기</a>를 읽어보세요.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_includes</code></p>
      </td>
      <td>
        <p>

          필요에 따라 포스트나 레이아웃에 끼워넣을 수 있는 조각들로서,
          쉽게 재사용할 수 있습니다.
          <code>{% raw %}{% include file.ext %}{% endraw %}</code>
          라는 Liquid 태그를 사용하면, 조각 파일 <code>_includes/file.ext</code>
          이 삽입됩니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_layouts</code></p>
      </td>
      <td>
        <p>

          이 템플릿들이 포스트 주위를 감쌉니다. 다음 섹션에서 설명하는
          <a href="../frontmatter/">YAML 머리말</a>에 의하여 각 포스트 별로
          레이아웃이 선택됩니다. 페이지에 컨텐츠를 주입할 때는
          <code>{% raw %}{{ content }}{% endraw %}</code> 라는 Liquid 태그를
          사용합니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_posts</code></p>
      </td>
      <td>
        <p>

          말하자면 동적인, 당신의 컨텐츠입니다. 파일의 명명 규약이 아주
          중요한데, 반드시 다음 규칙을 따라야 합니다:
          <code>YEAR-MONTH-DAY-title.MARKUP</code>.
          <a href="../permalinks/">고유주소</a>는 각 포스트 별로 수정이
          가능하지만, 날짜와 마크업 언어 종류는 오로지 파일명에 의해서
          결정됩니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_data</code></p>
      </td>
      <td>
        <p>

          여기에는 올바르게 형식화된 사이트 데이터를 보관합니다. Jekyll 엔진은
          이 디렉토리에 있는 모든 YAML 파일 (확장자가 <code>.yml</code> 또는 <code>.yaml</code>) 을 자동으로 읽어들입니다.
          만약 이 디렉토리에 <code>members.yml</code> 파일이 있다면,
          <code>site.data.members</code> 라고 입력하여 그 컨텐츠에 접근할 수 있습니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_site</code></p>
      </td>
      <td>
        <p>

          Jekyll 이 변환을 마치고 나서 생성된 사이트가 저장되는 (기본값)
          위치입니다. 아마도 <code>.gitignore</code> 파일에 이 디렉토리를
          추가하는 것이 좋을 것입니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>index.html</code> 과 다른 HTML, Markdown, Textile 파일들</p>
      </td>
      <td>
        <p>

          파일에 <a href="../frontmatter/">YAML 머리말</a> 섹션이 있다면 Jekyll
          에 의해 변환됩니다. 사이트의 루트 디렉토리나 위에 언급된 디렉토리 외에
          다른 모든 디렉토리 안의 <code>.html</code> 이나
          <code>.markdown</code>, <code>.md</code>, <code>.textile</code> 파일도
          해당됩니다.

        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>다른 파일/폴더</p>
      </td>
      <td>
        <p>

          <code>css</code> 나 <code>images</code> 폴더, <code>favicon.ico</code>
          파일 등 위에 언급되지 않은 다른 디렉토리와 파일들은 그대로 복사됩니다.
          다른 사이트들은 어떤식으로 구성되었는지 궁금하다면,
          <a href="../sites/">이미 Jekyll 을 사용하는 사이트들</a>이 많이 있으니
          살펴보세요.

        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>
