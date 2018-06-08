---
#title: Permalinks
title: 고유주소
permalink: /docs/permalinks/
---

<!--
Permalinks refer to the URLs (excluding the domain name or directory folder) for your pages, posts, or collections.
Jekyll supports a flexible way to build permalinks, allowing you to leverage various template variables or choose built-in permalink styles (such as `date`) that automatically use a template-variable pattern.
-->
고유주소는 (도메인명이나 디렉토리를 제외한) 페이지나 포스트, 콜렉션의 URL 을 나타냅니다.
Jekyll 이 지원하는 고유주소 생성 방식은 유연합니다. 다양한 템플릿 변수들을 활용하거나 자동으로 템플릿-변수 패턴을 사용하는 (`date` 와 같은) 내장된 고유주소 스타일을 사용할 수 있게 해줍니다.

<!--
You construct permalinks by creating a template URL where dynamic elements are represented by colon-prefixed keywords. The default template permalink is `/:categories/:year/:month/:day/:title:output_ext`. Each of the colon-prefixed keywords is a template variable.
-->
고유주소를 만들기 위해서는 키워드 앞에 콜론을 붙여 나타내는 동적 요소들을 사용하여 템플릿 URL 을 생성합니다. 고유주소의 템플릿 기본값은 `/:categories/:year/:month/:day/:title:output_ext` 입니다. 콜론으로 시작하는 키워드들은 템플릿 변수입니다.

<!--
## Where to configure permalinks
-->
## 고유주소를 설정하는 위치

<!--
You can configure your site's permalinks through the [Configuration]({% link _docs/configuration.md %}) file or in the [Front Matter]({% link _docs/frontmatter.md %}) for each post, page, or collection.
-->
[환경설정]({% link _docs/configuration.md %}) 파일 또는 각각의 포스트나 페이지, 콜렉션의 [머리말]({% link _docs/frontmatter.md %})에 고유주소를 설정할 수 있습니다.

<!--
Setting permalink styles in your configuration file applies the setting globally in your project. You configure permalinks in your `_config.yml` file like this:
-->
환경설정 파일에 고유주소 스타일을 설정하면 프로젝트 전체에 영향을 미칩니다. `_config.yml` 파일에 고유주소를 설정하는 것은 다음과 같습니다:

```yaml
permalink: /:categories/:year/:month/:day/:title:output_ext
```

<!--
If you don't specify any permalink setting, Jekyll uses the above pattern as the default.
-->
아무런 고유주소 설정이 없다면, Jekyll 은 이 패턴을 기본값으로 사용합니다.

<!--
The permalink can also be set using a built-in permalink style:
-->
내장된 고유주소 스타일을 사용할 수도 있습니다:

```yaml
permalink: date
```

<!--
`date` is the same as `:categories/:year/:month/:day/:title:output_ext`, the default. See [Built-in Permalink Styles](#builtinpermalinkstyles) below for more options.
-->
`date` 는 `:categories/:year/:month/:day/:title:output_ext` 와 동일하게 기본으로 설정되어 있습니다. 더 많은 옵션에 관해서는 [내장된 고유주소 스타일](#builtinpermalinkstyles)을 참고하세요.

<!--
Setting the permalink in your post, page, or collection's front matter overrides any global settings. Here's an example:
-->
포스트나 페이지, 콜렉션의 머리말에 설정된 고유주소는 전역 설정보다 우선시됩니다. 여기 그 예시가 있습니다:

```yaml
---
title: My page title
permalink: /mypageurl/
---
```

<!--
Even if your configuration file specifies the `date` style, the URL for this page would be `http://somedomain.com/mypageurl/`.
-->
환경설정파일에 `date` 스타일을 사용하도록 설정했더라도, 이 페이지의 URL 은 `http://somedomain.com/mypageurl/` 이 됩니다.

<!--
When you use permalinks that omit the `.html` file extension (called "pretty URLs") Jekyll builds the file as index.html placed inside a folder with the page's name. For example:
-->
만약 `.html` 파일 확장자를 제거한 고유주소("Pretty URL" 이라고 함)를 사용하면 Jekyll 은 페이지의 이름으로 폴더를 만들고 그 안에 파일을 index.html 이라는 이름으로 저장합니다. 예시:

```
├── mypageurl
│   └── index.html
```

<!--
With a URL such as `/mypageurl/`, servers automatically load the index.html file inside the folder, so users can simply navigate to `http://somedomain.com/mypageurl/` to get to `mypageurl/index.html`.
-->
`/mypageurl/` 과 같은 URL 에서는, 서버가 자동으로 해당 폴더에 있는 index.html 파일을 읽으므로, 사용자는 그냥 `http://somedomain.com/mypageurl/` 에 접근해서 `mypageurl/index.html` 을 볼 수 있습니다.

<!--
## Template variables for permalinks {#template-variables}
-->
## 고유주소 관련 템플릿 변수 {#template-variables}

<!--
The following table lists the template variables available for permalinks. You can use these variables in the `permalink` property in your config file.
-->
다음 테이블에 고유주소에 사용할 수 있는 템플릿 변수가 나열되어 있습니다. 환경설정 파일의 `permalink` 속성에 이 변수들을 사용할 수 있습니다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Variable</th>
      <th>Description</th>
-->
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>year</code></p>
      </td>
      <td>
<!--
        <p>
          Year from the post's filename. May be overridden via the document’s
          <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 연도. YAML 머리말의
          <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>month</code></p>
      </td>
      <td>
<!--
        <p>
          Month from the post's filename. May be overridden via the document’s
          <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 월. YAML 머리말의
          <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_month</code></p>
      </td>
      <td>
<!--
        <p>
          Month without leading zeros from the post's filename. May be
          overridden via the document’s <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 월 (한 자리일 경우 앞에 0 이 없음).
          YAML 머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>day</code></p>
      </td>
      <td>
<!--
        <p>
          Day from the post's filename. May be overridden via the document’s
          <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 일. YAML 머리말의
          <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_day</code></p>
      </td>
      <td>
<!--
        <p>
          Day without leading zeros from the post's filename. May be overridden
          via the document’s <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 일 (한 자리일 경우 앞에 0 이 없음).
          YAML 머리말의 <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>y_day</code></p>
      </td>_
      <td>
<!--
        <p>Day of the year from the post's filename, with leading zeros.</p>
-->
        <p>파일명에 명시된 포스트 게시일시의 일 (한 자리일 경우 앞에 0 이 있음).</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_year</code></p>
      </td>
      <td>
<!--
        <p>
          Year without the century from the post's filename. May be overridden
          via the document’s <code>date</code> YAML front matter
        </p>
-->
        <p>
          파일명에 명시된 포스트 게시일시의 연도 (두 자리). YAML 머리말의
          <code>date</code> 를 통해 값을 덮어쓸 수 있다
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>hour</code></p>
      </td>
      <td>
<!--
        <p>
          Hour of the day, 24-hour clock, zero-padded from the post's
          <code>date</code> front matter. (00..23)
        </p>
-->
        <p>
          24 시간제, 두 자리 형식으로 된
          포스트의 머리말 <code>date</code> 의 시간값. (00..23)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>minute</code></p>
      </td>
      <td>
<!--
        <p>
          Minute of the hour from the post's <code>date</code> front matter. (00..59)
        </p>
-->
        <p>
          포스트의 머리말 <code>date</code> 의 분값. (00..59)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>second</code></p>
      </td>
      <td>
<!--
        <p>
          Second of the minute from the post's <code>date</code> front matter. (00..59)
        </p>
-->
        <p>
          포스트의 머리말 <code>date</code> 의 초값. (00..59)
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
<!--
        <p>
            Title from the document’s filename. May be overridden via
            the document’s <code>slug</code> YAML front matter.
        </p>
-->
        <p>
            파일명에 명시된 문서의 제목. YAML 머리말의 <code>slug</code>
            를 통해 값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>slug</code></p>
      </td>
      <td>
<!--
        <p>
            Slugified title from the document’s filename (any character
            except numbers and letters is replaced as hyphen). May be
            overridden via the document’s <code>slug</code> YAML front matter.
        </p>
-->
        <p>
            파일명에 명시된 문서 제목의 슬러그화 결과 (숫자와 글자가 아닌
            모든 문자를 하이픈으로 변경함). YAML 머리말의 <code>slug</code> 로
            값을 덮어쓸 수 있다.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>categories</code></p>
      </td>
      <td>
<!--
        <p>
          The specified categories for this post. If a post has multiple
          categories, Jekyll will create a hierarchy (e.g. <code>/category1/category2</code>).
          Also Jekyll automatically parses out double slashes in the URLs,
          so if no categories are present, it will ignore this.
        </p>
-->
        <p>
          해당 포스트에 지정된 카테고리들. 만약 포스트가 여러 카테고리에
          속해있다면, 계층 구조로 URL 이 생성된다 (예시. <code>/category1/category2</code>).
          또한, Jekyll 은 URL 을 분석해서 연속된 슬래시를 자동으로 제거하기
          때문에, 카테고리가 하나도 없으면, Jekyll 은 이 변수를 무시한다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
Note that all template variables relating to time or categories are available to posts only.
-->
시간이나 카테고리와 관련된 템플릿 변수들은 포스트에서만 사용할 수 있습니다.

<!--
## Built-in permalink styles {#builtinpermalinkstyles}
-->
## 내장된 고유주소 스타일 {#builtinpermalinkstyles}

<!--
Although you can specify a custom permalink pattern using [template variables](#template-variables), Jekyll also provides the following built-in styles for convenience.
-->
[템플릿 변수](#template-variables)를 사용하여 고유주소 패턴을 지정할 수 있지만, 편의를 위해 Jekyll 에서 기본으로 제공하는 고유주소 스타일도 있다.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Permalink Style</th>
      <th>URL Template</th>
-->
      <th>고유주소 스타일</th>
      <th>URL 템플릿</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title:output_ext</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>pretty</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title/</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>ordinal</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:y_day/:title:output_ext</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>none</code></p>
      </td>
      <td>
        <p><code>/:categories/:title:output_ext</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
Rather than typing `permalink: /:categories/:year/:month/:day/:title/`, you can just type `permalink: pretty`.
-->
`permalink: /:categories/:year/:month/:day/:title/` 가 아니라, 그냥 `permalink: pretty` 라고 입력해도 된다.

<div class="note info">
<!--
<h5>Specifying permalinks through the YAML Front Matter</h5>
<p>Built-in permalink styles are not recognized in YAML Front Matter. As a result, <code>permalink: pretty</code> will not work.</p>
-->
<h5>YAML 머리말에서 고유주소 사용</h5>
<p>내장된 고유주소 스타일은 YAML 머리말에서는 인식되지 않습니다. 따라서, <code>permalink: pretty</code> 는 작동하지 않을 것입니다.</p>
</div>

<!--
## Permalink style examples with posts {#permalink-style-examples}
-->
## 포스트의 고유주소 스타일 예시 {#permalink-style-examples}

<!--
Here are a few examples to clarify how permalink styles get applied with posts.
-->
여기 고유주소 스타일이 포스트에 어떤식으로 적용되는지를 명확하게 보여주는 예제들이 있습니다.

<!--
Given a post named: `/2009-04-29-slap-chop.md`
-->
포스트 이름: `/2009-04-29-slap-chop.md`

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>URL Template</th>
      <th>Resulting Permalink URL</th>
-->
      <th>URL 템플릿</th>
      <th>고유주소 URL 결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
<!--
        <p>None specified, or <code>permalink: date</code></p>
-->
        <p>설정하지 않음, 또는 <code>permalink: date</code></p>
      </td>
      <td>
        <p><code>/2009/04/29/slap-chop.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>pretty</code></p>
      </td>
      <td>
        <p><code>/2009/04/29/slap-chop/</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>/:month-:day-:year/:title:output_ext</code></p>
      </td>
      <td>
        <p><code>/04-29-2009/slap-chop.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>/blog/:year/:month/:day/:title/</code></p>
      </td>
      <td>
        <p><code>/blog/2009/04/29/slap-chop/</code></p>
      </td>
    </tr>
    <tr>
      <td>
<!--
        <p><code>/:year/:month/:title</code></p>
        <p>See <a href="#extensionless-permalinks">Extensionless permalinks with no trailing slashes</a> for details.</p>
-->
        <p><code>/:year/:month/:title</code></p>
        <p>자세한 사항은 <a href="#extensionless-permalinks">끝에 슬래시가 붙지 않은 확장자 없는 고유주소</a>를 참고하시오.</p>
      </td>
      <td>
        <p><code>/2009/04/slap-chop</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<!--
## Permalink settings for pages and collections {#pages-and-collections}
-->
## 페이지와 콜렉션 관련 고유주소 설정 {#pages-and-collections}

<!--
The permalink setting in your configuration file specifies the permalink style used for posts, pages, and collections. However, because pages and collections don't have time or categories, these aspects of the permalink style are ignored with pages and collections.
-->
환경설정 파일의 고유주소 설정은 포스트, 페이지, 콜렉션의 고유주소 스타일을 결정합니다.  하지만, 페이지와 콜렉션에는 시간이나 카테고리 정보가 없는 관계로, 페이지와 콜렉션에서는 이러한 고유주소 스타일이 무시됩니다.

<!--
For example:
-->
예를 들어:

<!--
* A permalink style of `/:categories/:year/:month/:day/:title:output_ext` for posts becomes `/:title.html` for pages and collections.
* A permalink style of `pretty` (or `/:categories/:year/:month/:day/:title/`), which omits the file extension and contains a trailing slash, will update page and collection permalinks to also omit the file extension and contain a trailing slash: `/:title/`.
* A permalink style of `date`, which contains a trailing file extension, will update page permalinks to also contain a trailing file extension: `/:title.html`. But no time or category information will be included.
-->
* 고유주소 스타일 `/:categories/:year/:month/:day/:title:output_ext` 은 페이지나 콜렉션에 적용되면 `/:title.html` 입니다.
* 고유주소 스타일 `pretty` (또는 `/:categories/:year/:month/:day/:title/`) 는, 확장자는 없고 끝에 슬래쉬가 붙으므로, 페이지나 콜렉션의 고유주소도 확장자는 없고 끝에 슬래시가 붙습니다: `/:title/`.
* 고유주소 스타일 `date` 는, 확장자를 포함하고 있으므로, 페이지의 고유주소도 확장자를 포함합니다: `/:title.html`. 하지만 카테고리나 시간정보는 포함되지 않습니다.

<!--
## Permalinks and default paths
-->
## 고유주소와 경로 기본값

<!--
The path to the post or page in the built site differs for posts, pages, and collections:
-->
사이트가 생성되고 난 후 포스트나 페이지, 콜렉션의 경로는 각각의 경우에 따라 다릅니다:

<!--
### Posts
-->
### 포스트

<!--
The subfolders into which you may have organized your posts inside the `_posts` directory will not be part of the permalink.
-->
포스트를 `_posts` 디렉토리의 하위 폴더에 정리한 경우 이 하위 폴더들은 고유주소에 포함되지 않습니다.

<!--
If you use a permalink style that omits the `.html` file extension, each post is rendered as an `index.html` file inside a folder with the post's name (for example, `categoryname/2016/12/01/mypostname/index.html`).
-->
만약 `.html` 파일 확장자가 없는 고유주소 스타일을 사용하면, 각 포스트는 `index.html` 파일로 생성되고 포스트의 이름으로 된 폴더에 저장됩니다 (예시, `categoryname/2016/12/01/mypostname/index.html`).

<!--
### Pages
-->
### 페이지

<!--
Unlike posts, pages by default mimic the source directory structure exactly. (The only exception is if your page has a `permalink` declared its front matter &mdash; in that case, the structure honors the permalink setting instead of the source folder structure.)
-->
포스트와는 다르게, 페이지는 기본적으로 소스 디렉토리 구조를 그대로 따르게 되어 있습니다. (한 가지 예외는 페이지의 머리말에 `permalink` 를 정의한 경우입니다 &mdash; 이 경우에는, 소스 폴더 구조 대신에 고유주소 설정에 따라 구조가 결정됩니다.)

<!--
As with posts, if you use a permalink style that omits the `.html` file extension, each page is rendered as an `index.html` file inserted inside a folder with the page's name (for example, `mypage/index.html`).
-->
포스트와 마찬가지로, `.html` 파일 확장자가 없는 고유주소 스타일을 사용하면, 페이지는 `index.html` 파일로 생성되고 페이지의 이름으로 된 폴더 안에 저장됩니다 (예시, `mypage/index.html`).

<!--
### Collections
-->
### 콜렉션

<!--
By default, collections follow a similar structure in the `_site` folder as pages, except that the path is prefaced by the collection name. For example: `collectionname/mypage.html`. For permalink settings that omit the file extension, the path would be `collection_name/mypage/index.html`.
-->
경로 맨 앞에 콜렉션의 이름이 추가된다는 점을 제외하면, 콜렉션은 페이지처럼 `_site` 폴더의 구조를 따르도록 기본 설정되어 있습니다. 예시: `collectionname/mypage.html`. 파일 확장자를 포함하지 않는 고유주소 설정이면, 경로는 `collection_name/mypage/index.html` 이 됩니다.

<!--
Collections have their own way of setting permalinks. Additionally, collections have unique template variables available (such as `path` and `output_ext`). See the [Configuring permalinks for collections](../collections/#permalinks) in Collections for more information.
-->
콜렉션은 콜렉션만의 고유주소 설정법이 따로 있습니다. 또, 콜렉션에서만 사용할 수 있는 템플릿 변수들도 있습니다 (예, `path` 와 `output_ext`). 더 자세한 정보는 콜렉션 페이지의 [콜렉션에 고유주소 설정하기](../collections/#permalinks)를 참고하세요.

<!--
## Flattening pages in \_site on build
-->
## 빌드 시 \_site 에 페이지 생성하기

<!--
If you want to flatten your pages (pull them out of subfolders) in the `_site` directory when your site builds (similar to posts), add the `permalink` property to the front matter of each page, with no path specified:
-->
페이지들을 (포스트처럼) 하위 폴더를 무시하고 `_site` 디렉토리에 생성하고 싶다면, 각 페이지의 머리말에 `permalink` 속성을 추가하고, 디렉토리 경로를 제거하세요:

```yaml
---
title: My page
permalink: mypageurl.html
---
```

<!--
## Extensionless permalinks with no trailing slashes {#extensionless-permalinks}
-->
## 끝에 슬래시가 붙지 않은 확장자 없는 고유주소 {#extensionless-permalinks}

<!--
Jekyll supports permalinks that contain neither a trailing slash nor a file extension, but this requires additional support from the web server to properly serve. When using these types of permalinks, output files written to disk will still have the proper file extension (typically `.html`), so the web server must be able to map requests without file extensions to these files.
-->
Jekyll 은 끝부분에 슬래시나 파일 확장자를 포함하지 않는 고유주소를 지원하지만, 올바르게 작동하려면 추가적으로 웹 서버의 지원을 필요로 합니다. 이런 종류의 고유주소를 사용할 때, 생성되는 사이트 파일은 여전히 파일 확장자를 가지고 있기 때문에 (일반적으로 `.html`), 확장자가 없는 요청을 이 파일들에 연결하는 작업을 웹 서버가 해줘야만 합니다.

<!--
Both [GitHub Pages](../github-pages/) and the Jekyll's built-in WEBrick server handle these requests properly without any additional work.
-->
[Github Pages](../github-pages/) 와 Jekyll 에 내장되어 있는 WEBrick 서버는 추가 작업 없이 이러한 요청을 처리할 수 있습니다.

### Apache

<!--
The Apache web server has extensive support for content negotiation and can handle extensionless URLs by setting the [multiviews](https://httpd.apache.org/docs/current/content-negotiation.html#multiviews) option in your `httpd.conf` or `.htaccess` file:
-->
Apache 웹 서버는 컨텐츠 선택에 관련된 지원을 광범위하게 제공하며, `httpd.conf` 또는 `.htaccess` 파일에 [multiviews](https://httpd.apache.org/docs/current/content-negotiation.html#multiviews) 옵션을 설정해서 확장자 없는 URL 을 처리할 수 있습니다:

{% highlight apache %}
Options +MultiViews
{% endhighlight %}

### Nginx

<!--
The [try_files](http://nginx.org/en/docs/http/ngx_http_core_module.html#try_files) directive allows you to specify a list of files to search for to process a request. The following configuration will instruct nginx to search for a file with an `.html` extension if an exact match for the requested URI is not found.
-->
[try_files](http://nginx.org/en/docs/http/ngx_http_core_module.html#try_files) 설정을 사용하면 요청을 처리할 때 검색할 파일들의 목록을 정의할 수 있습니다. 다음과 같이 환경설정을 하면, 요청받은 URI 에 해당하는 파일을 찾을 수 없는 경우 `.html` 확장자를 가진 파일을 검색합니다.

{% highlight nginx %}
try_files $uri $uri.html $uri/ =404;
{% endhighlight %}

<!--
## Linking without regard to permalink styles
-->
## 고유주소 스타일에 관계없이 링크 생성하기

<!--
You can create links in your topics to other posts, pages, or collection items in a way that is valid no matter what permalink configuration you choose. By using the `link` tag, if you change your permalinks, your links won't break. See [Linking to pages](../templates#link) in Templates for more details.
-->
포스트나 페이지, 콜렉션 항목에 대한 링크를 고유주소 환경설정에 영향을 받지 않고 항상 올바르게 생성하는 방법이 있습니다. `link` 태그를 사용하면, 당신이 고유주소를 변경하는 경우에도, 링크가 깨지지 않습니다. 더 자세한 정보는 템플릿 페이지의 [페이지에 연결하기](../templates#link)를 참고하세요.
