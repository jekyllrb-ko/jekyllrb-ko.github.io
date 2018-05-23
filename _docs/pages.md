---
#title: Creating pages
title: 페이지 생성하기
permalink: /docs/pages/
---

<!--
In addition to [writing posts](../posts/), you might also want to add static pages (content that isn't date-based) to your Jekyll site. By taking advantage of the way Jekyll copies files and directories, this is easy to do.
-->
자신의 Jekyll 사이트에 [포스트를 작성](../posts/)하는 것 뿐만 아니라 정적 페이지들 (날짜와 관련없는 내용들) 도 추가하고 싶을 수도 있을 것입니다. 이런 것들은, 디렉토리와 파일을 복사하는 Jekyll 의 동작 방식을 활용하면 너무나도 쉽습니다.

<!--
## Homepage
-->
## 홈페이지

<!--
Just about every web server configuration you come across will look for an HTML
file called `index.html` (by convention) in the site's root folder and display
that as the homepage. Unless the web server you’re using is configured to look
for some different filename as the default, this file will turn into the
homepage of your Jekyll-generated site.
-->
당신이 접하는 거의 모든 웹 서버 환경설정이 사이트의 루트 폴더에서 파일명이
(관례상) `index.html` 인 HTML 파일을 찾아 홈페이지로 보여줍니다. 웹 서버가 다른
파일을 찾도록 설정되어 있지 않는 한, 이 파일이 당신의 Jekyll 사이트 홈페이지가
됩니다.


<div class="note">
<!--
  <h5>ProTip™: Use layouts on your homepage</h5>
  <p>
    Any HTML file on your site can use layouts and/or includes, even the
    homepage. Common content, like headers and footers, make excellent
    candidates for extraction into a layout.
  </p>
-->
  <h5>ProTip™: 홈페이지에 레이아웃을 사용하세요</h5>
  <p>
    <code>_layouts</code> 와/또는 <code>_includes</code> 는 사이트 안에 있는 모든
    HTML 에서 사용할 수 있으며, 홈페이지도 예외는 아닙니다. 레이아웃으로 추출할
    만한 좋은 후보감으로는 헤더나 푸터 같은 공용 컨텐츠가 있습니다.
  </p>
</div>

<!--
## Where additional pages live
-->
## 페이지의 위치

<!--
Where you put HTML or [Markdown](https://daringfireball.net/projects/markdown/)
files for pages depends on how you want the pages to work. There are two main ways of creating pages:
-->
HTML 이나 [Markdown](https://daringfireball.net/projects/markdown/)
파일을 생성하는 위치에 따라 페이지 작동 방식이 달라집니다. 페이지를 생성하는 방법은 두 가지가 있습니다:

<!--
- Place named HTML or [Markdown](https://daringfireball.net/projects/markdown/)
files for each page in your site's root folder.
- Place pages inside folders and subfolders named whatever you want.
-->
- 사이트의 루트 폴더에 각 페이지 별로 HTML 이나 [Markdown](https://daringfireball.net/projects/markdown/)
파일을 만든다.
- 원하는 이름으로 폴더나 그 안에 하위 폴더를 만들고 페이지를 넣는다.

<!--
Both methods work fine (and can be used in conjunction with each other),
with the only real difference being the resulting URLs. By default, pages retain the same folder structure in `_site` as they do in the source directory.
-->
어떤 방법을 사용하든지 (또는 두 방법을 함께 사용해도) 잘 작동합니다. 하지만,
최종 URL 모양이 서로 다릅니다. 기본적으로, 페이지는 원본 디렉토리에서처럼 `_site` 의 폴더 구조를 사용합니다.

<!--
### Named HTML files
-->
### HTML 파일에 이름 쓰기

<!--
The simplest way of adding a page is just to add an HTML file in the root
directory with a suitable name for the page you want to create. For a site with
a homepage, an about page, and a contact page, here’s what the root directory
and associated URLs might look like:
-->
페이지를 추가하는 가장 간단한 방법은 루트 디렉토리에 생성하고자 하는 페이지
이름을 가진 HTML 파일을 추가하는 것입니다. 예를 들어 홈페이지와 about 페이지,
contact 페이지가 있을 때, 루트 디렉토리의 내용과 각각에 해당하는 URL 은 다음과
같습니다:

```sh
.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- about.html    # => http://example.com/about.html
|-- index.html    # => http://example.com/
|-- other.md      # => http://example.com/other.html
└── contact.html  # => http://example.com/contact.html
```

If you have a lot of pages, you can organize those pages into subfolders. The same subfolders that are used to group your pages in our project's source will exist in the `_site` folder when your site builds.

## Flattening pages from subfolders into the root directory

If you have pages organized into subfolders in your source folder and want to flatten them in the root folder on build, you must add the [permalink]({% link _docs/permalinks.md %}) property directly in your page's front matter like this:

```yaml
---
title: My page
permalink: mypageurl.html
---
```

<!--
### Named folders containing index HTML files
-->
### 디렉토리에 이름을 짓고 인덱스 HTML 파일 넣기

If you don't want file extensions (`.html`) to appear in your page URLs (file extensions are the default), you can choose a [permalink style](../permalinks/#builtinpermalinkstyles) that has a trailing slash instead of a file extension.

Note if you want to view your site offline *without the Jekyll preview server*, your browser will need the file extension to display the page, and all assets will need to be relative links that function without the server baseurl.
