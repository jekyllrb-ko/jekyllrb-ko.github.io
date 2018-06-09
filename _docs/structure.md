---
#title: Directory structure
title: 디렉토리 구조
permalink: /docs/structure/
---

<!--
Jekyll is, at its core, a text transformation engine. The concept behind the
system is this: you give it text written in your favorite markup language, be
that Markdown, Textile, or just plain HTML, and it churns that through a layout
or a series of layout files. Throughout that process you can tweak how you want
the site URLs to look, what data gets displayed in the layout, and more. This
is all done through editing text files; the static web site is the final
product.
-->
Jekyll 의 핵심 역할은 텍스트 변환 엔진입니다. 시스템의 컨셉은 다음과 같습니다:
당신이 마크다운이나 Textile 또는 일반 HTML 등 자신이 즐겨 사용하는 마크업 언어로
문서를 작성하면, Jekyll 은 이 문서들을 하나 또는 여러 겹의 레이아웃으로 포장합니다.
사이트 URL 구성 방식이나 어떤 데이터를 레이아웃에 표시할 것인지 등, 변환 과정에
포함된 다양한 동작들은 당신이 원하는대로 조정할 수 있습니다. 단지 텍스트 파일을
수정하는 것만으로 이 모든 일들이 가능합니다. 그 결과로 정적 웹 사이트가
만들어집니다.

<!--
A basic Jekyll site usually looks something like this:
-->
가장 기본적인 Jekyll 사이트는 보통 이렇게 생겼습니다:

<!--
```sh
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid YAML Frontmatter
```
-->
```sh
.
├── _config.yml
├── _data
|   └── members.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.md
|   └── on-simplicity-in-technology.md
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
|   ├── _base.scss
|   └── _layout.scss
├── _site
├── .jekyll-metadata
└── index.html # 'index.md' 이어도 되지만 올바른 YAML 머리말이 필요합니다
```

<!--
<div class="note info">
  <h5>Directory structure of Jekyll sites using gem-based themes</h5>
  <p>
    Starting <strong>Jekyll 3.2</strong>, a new Jekyll project bootstrapped with <code>jekyll new</code> uses <a href="../themes/">gem-based themes</a> to define the look of the site. This results in a lighter default directory structure : <code>_layouts</code>, <code>_includes</code> and <code>_sass</code> are stored in the theme-gem, by default.
  </p>
  <br />
  <p>
     <a href="https://github.com/jekyll/minima">minima</a> is the current default theme, and <code>bundle show minima</code> will show you where minima theme's files are stored on your computer.
  </p>
</div>
-->
<div class="note info">
  <h5>루비 젬 기반 테마를 사용하는 Jekyll 사이트의 디렉토리 구조</h5>
  <p>
    <strong>Jekyll 3.2</strong> 버전부터, <code>jekyll new</code> 명령으로 생성된 Jekyll 프로젝트는 <a href="../themes/">루비 젬 기반 테마</a>를 사용하여 사이트의 외관을 구성합니다. 이로 인해, 테마 루비 젬에 기본적으로 포함된 경량 디렉토리 구조 : <code>_layouts</code>, <code>_includes</code>, <code>_sass</code> 를 갖게 됩니다.
  </p>
  <br />
  <p>
     현재의 기본 테마는 <a href="https://github.com/jekyll/minima">minima</a> 이며, <code>bundle show minima</code> 명령으로 Minima 테마의 파일들이 어디에 저장되어 있는지 볼 수 있습니다.
  </p>
</div>

<!--
An overview of what each of these does:
-->
각 파일과 디렉토리가 하는 일의 개요는 다음과 같습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>File / Directory</th>
      <th>Description</th>
-->
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
<!--
        <p>
          Stores <a href="../configuration/">configuration</a> data. Many of
          these options can be specified from the command line executable but
          it’s easier to specify them here so you don’t have to remember them.
        </p>
-->
        <p>
          <a href="../configuration/">환경설정</a> 정보를 보관한다. 명령어를
          실행할 때 여러가지 옵션들을 추가할 수도 있지만, 그렇게 따로 외우는
          것보다 이 파일에 정의해두는게 더 편리하다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_drafts</code></p>
      </td>
      <td>
<!--
        <p>
          Drafts are unpublished posts. The format of these files is without a
          date: <code>title.MARKUP</code>. Learn how to <a href="../drafts/">
          work with drafts</a>.
        </p>
-->
        <p>
          초안이란 아직 게시하지 않은 포스트를 말한다. 파일명 형식에 날짜가
          없다: <code>title.MARKUP</code>. 사용 방법은 <a href="../drafts/">
          초안 활용하기</a>를 참고하라.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_includes</code></p>
      </td>
      <td>
<!--
        <p>
          These are the partials that can be mixed and matched by your layouts
          and posts to facilitate reuse. The liquid tag
          <code>{% raw %}{% include file.ext %}{% endraw %}</code>
          can be used to include the partial in
          <code>_includes/file.ext</code>.
        </p>
-->
        <p>
          재사용하기 위한 파일을 담는 디렉토리로서, 필요에 따라 포스트나
          레이아웃에 쉽게 삽입할 수 있다.
          <code>{% raw %}{% include file.ext %}{% endraw %}</code> 와 같이
          Liquid 태그를 사용하면 <code>_includes/file.ext</code> 파일에 담긴
          코드가 삽입된다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_layouts</code></p>
      </td>
      <td>
<!--
        <p>
          These are the templates that wrap posts. Layouts are chosen on a
          post-by-post basis in the
          <a href="../frontmatter/">YAML Front Matter</a>,
          which is described in the next section. The liquid tag
          <code>{% raw %}{{ content }}{% endraw %}</code>
          is used to inject content into the web page.
        </p>
-->
        <p>
          포스트를 포장할 때 사용하는 템플릿이다. 각 포스트 별로
          레이아웃을 선택하는 기준은
          <a href="../frontmatter/">YAML 머리말</a>이며, 자세한 내용은 다음
          섹션에서 설명한다.
          <code>{% raw %}{{ content }}{% endraw %}</code> 와 같이 Liquid 태그를
          사용하면 페이지에 컨텐츠가 주입된다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_posts</code></p>
      </td>
      <td>
<!--
        <p>
          Your dynamic content, so to speak. The naming convention of these
          files is important, and must follow the format:
          <code>YEAR-MONTH-DAY-title.MARKUP</code>.
          The <a href="../permalinks/">permalinks</a> can be customized for
          each post, but the date and markup language are determined solely by
          the file name.
        </p>
-->
        <p>
          한마디로 말하면, 당신의 컨텐츠다. 중요한 것은 파일들의 명명규칙인데,
          반드시 이 형식을 따라야 한다:
          <code>YEAR-MONTH-DAY-title.MARKUP</code>.
          <a href="../permalinks/">고유주소</a>는 포스트 별로 각각 정의할 수
          있지만, 날짜와 마크업 언어 종류는 오로지 파일명에 의해
          결정된다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_data</code></p>
      </td>
      <td>
<!--
        <p>
          Well-formatted site data should be placed here. The Jekyll engine
          will autoload all data files (using either the <code>.yml</code>,
          <code>.yaml</code>, <code>.json</code> or <code>.csv</code>
          formats and extensions) in this directory, and they will be
          accessible via `site.data`. If there's a file
          <code>members.yml</code> under the directory, then you can access
          contents of the file through <code>site.data.members</code>.
        </p>
-->
        <p>
          사이트에 사용할 데이터를 적절한 포맷으로 정리하여 보관하는 디렉토리.
          Jekyll 엔진은 이 디렉토리에 있는 (확장자와 포맷이 <code>.yml</code>
          또는 <code>.yaml</code>, <code>.json</code>, <code>.csv</code> 인)
          모든 데이터 파일을 자동으로 읽어들여 `site.data` 로 사용할 수 있도록
          만든다. 만약 이 디렉토리에 <code>members.yml</code> 라는 파일이
          있다면, <code>site.data.members</code> 라고 입력하여 그 컨텐츠를
          사용할 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_sass</code></p>
      </td>
      <td>
        <p>
          Sass 조각파일들로, 프로젝트의 <code>main.scss</code> 에 임포트할 수 있으며
          임포트 후에는 다시 하나의 스타일시트(<code>main.scss</code>)로 가공되어
          사이트에 사용되는 스타일들을 정의한다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_site</code></p>
      </td>
      <td>
<!--
        <p>
          This is where the generated site will be placed (by default) once
          Jekyll is done transforming it. It’s probably a good idea to add this
          to your <code>.gitignore</code> file.
        </p>
-->
        <p>
          Jekyll 이 변환 작업을 마친 뒤 생성된 사이트가 저장되는 (디폴트)
          경로이다. 대부분의 경우, 이 경로를 <code>.gitignore</code> 에
          추가하는 것은 괜찮은 생각이다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>.jekyll-metadata</code></p>
      </td>
      <td>
<!--
        <p>
          This helps Jekyll keep track of which files have not been modified
          since the site was last built, and which files will need to be
          regenerated on the next build. This file will not be included in the
          generated site. It’s probably a good idea to add this to your
          <code>.gitignore</code> file.
        </p>
-->
        <p>
          Jekyll 은 이 파일을 참고하여, 마지막으로 빌드한 이후에 한번도 수정되지
          않은 파일은 어떤 것인지, 다음 빌드 때 어떤 파일을 다시 생성해야 하는지
          판단할 수 있다. 생성된 사이트에 이 파일이 복사되지는 않는다. 대부분의
          경우, 이 파일을 <code>.gitignore</code> 에 추가하는 것은 괜찮은
          생각이다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p><code>index.html</code> or <code>index.md</code> and other HTML,
        Markdown, Textile files</p>
-->
        <p><code>index.html</code> 또는 <code>index.md</code> 및 다른 HTML,
        마크다운, Textile 파일</p>
      </td>
      <td>
<!--
        <p>
          Provided that the file has a <a href="../frontmatter/">YAML Front
          Matter</a> section, it will be transformed by Jekyll. The same will
          happen for any <code>.html</code>, <code>.markdown</code>,
          <code>.md</code>, or <code>.textile</code> file in your site’s root
          directory or directories not listed above.
        </p>
-->
        <p>
          Jekyll 은 <a href="../frontmatter/">YAML 머리말</a> 섹션을 가진 모든
          파일을 찾아 변환 작업을 수행한다. 위에서 언급하지 않은 다른 디렉토리나
          사이트의 루트 디렉토리에 있는 모든 <code>.html</code>,
          <code>.markdown</code>, <code>.md</code>, <code>.textile</code> 이
          여기에 해당한다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p>Other Files/Folders</p>
-->
        <p>다른 파일/폴더</p>
      </td>
      <td>
<!--
        <p>
          Every other directory and file except for those listed above—such as
          <code>css</code> and <code>images</code> folders,
          <code>favicon.ico</code> files, and so forth—will be copied verbatim
          to the generated site. There are plenty of <a href="../sites/">sites
          already using Jekyll</a> if you’re curious to see how they’re laid
          out.
        </p>
-->
        <p>
          <code>css</code> 나 <code>images</code> 폴더, <code>favicon.ico</code>
          파일같이 앞서 언급하지 않은 다른 모든 디렉토리와 파일들은 있는 그대로
          생성된 사이트에 복사한다. 다른 사람들이 만든 사이트는 어떤식으로
          생겼는지 궁금하다면, <a href="../sites/">Jekyll 을 사용하는
          사이트들</a>이 이미 많이 있으니 살펴보도록 한다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>
