---
layout: docs
title: 템플릿
prev_section: migrations
next_section: permalinks
permalink: /docs/templates/
---

Jekyll 은 템플릿 처리에 [Liquid](https://github.com/Shopify/liquid/wiki) 템플릿
언어를 사용합니다. 표준 Liquid [태그](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#tags)와
[필터](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#standard-filters)가
모두 지원됩니다. 뿐만 아니라, 일부 작업을 더 쉽게 할 수 있도록 도와주는 유용한
태그와 필터가 더 추가되어 있습니다.

## 필터

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>설명</th>
      <th><span class="filter">필터</span>와 <span class="output">결과</span></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p class="name"><strong>Date to XML Schema</strong></p>
        <p>날짜를 XML 스키마 (ISO 8601) 형식으로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_xmlschema }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">2008-11-07T13:07:54-08:00</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Date to RFC-822 Format</strong></p>
        <p>날짜를 RSS 피드에 사용하는 RFC-822 형식으로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_rfc822 }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">Mon, 07 Nov 2008 13:07:54 -0800</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Date to String</strong></p>
        <p>날짜를 짧은 형식으로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">07 Nov 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Date to Long String</strong></p>
        <p>날짜를 긴 형식으로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.time | date_to_long_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">07 November 2008</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Where</strong></p>
        <p>배열 안에서 특정 키와 값을 가진 객체들을 선택합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | where:"graduation_year","2014" }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Group By</strong></p>
        <p>배열 안의 항목들을 특정 속성으로 그룹 짓습니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.members | group_by:"graduation_year" }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">[{"name"=>"2013", "items"=>[...]},
{"name"=>"2014", "items"=>[...]}]</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>XML Escape</strong></p>
        <p>XML 에 사용되는 몇몇 텍스트를 이스케이프 합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.content | xml_escape }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>CGI Escape</strong></p>
        <p>
          URL 에 사용되는 CGI 이스케이프 문자열. 모든 특수문자를 그에 맞는 %XX
          로 변환합니다.
        </p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "foo,bar;baz?" | cgi_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo%2Cbar%3Bbaz%3F</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>URI Escape</strong></p>
        <p>
          URI 이스케이프 문자열.
        </p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "foo, bar \baz?" | uri_escape }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo,%20bar%20%5Cbaz?</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Number of Words</strong></p>
        <p>텍스트 안의 단어 수.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.content | number_of_words }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">1337</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Array to Sentence</strong></p>
        <p>배열을 한 문장으로 변환합니다. 태그를 나열할 때 유용합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.tags | array_to_sentence_string }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">foo, bar, and baz</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Textilize</strong></p>
        <p>Textile 포맷 문자열을 RedCloth 포맷의 HTML 로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.excerpt | textilize }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Markdownify</strong></p>
        <p>Markdown 포맷 문자열을 HTML 로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.excerpt | markdownify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Converting Sass/SCSS</strong></p>
        <p>Sass 또는 SCSS 형식 문자열을 CSS 로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
          <code class="filter">{% raw %}{{ some_scss | scssify }}{% endraw %}</code>
          <code class="filter">{% raw %}{{ some_sass | sassify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Slugify</strong></p>
        <p>알파벳과 숫자가 아닌 문자와 공백 문자를 하이픈으로 교체하여, 문자열을 소문자 URL 슬러그로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.title | slugify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Data To JSON</strong></p>
        <p>해시나 배열을 JSON 으로 변환합니다.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ site.data.projects | jsonify }}{% endraw %}</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Sort</strong></p>
        <p>배열을 정렬합니다. 해시에 사용하는 선택 전달인자: 1.&nbsp;속성 이름 2.&nbsp;nils 순서 (<em>first</em> 또는 <em>last</em>).</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ page.tags | sort }}{% endraw %}</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ site.posts | sort: 'author' }}{% endraw %}</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ site.pages | sort: 'title', 'last' }}{% endraw %}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 태그

### Includes

만약 사이트 안의 여러 곳에 삽입해야 하는 작은 조각 페이지가 있다면, `include`
태그를 사용하세요.

{% highlight ruby %}
{% raw %}{% include footer.html %}{% endraw %}
{% endhighlight %}

삽입할 파일은 프로젝트의 루트 디렉토리 밑의 `_includes` 디렉토리에 넣어야
합니다. 위 코드는 `<source>/_includes/footer.html` 파일의 내용을 삽입할
것입니다.

<div class="note">
  <h5>ProTip™: 파일 이름에 변수를 사용하세요</h5>
  <p>

    삽입하고자 하는 파일의 이름은 (위 예제처럼) 실제 파일명을 사용할 수도 있고,
    <code>{% raw %}{% include {{my_variable}} %}{% endraw %}</code> 처럼 Liquid
    스타일의 변수 문법을 사용할 수도 있습니다.

  </p>
</div>

삽입할 파일에 파라메터를 전달할 수도 있습니다:

{% highlight ruby %}
{% raw %}{% include footer.html param="value" %}{% endraw %}
{% endhighlight %}

전달된 파라메터는 Liquid 를 통해 사용할 수 있습니다:

{% highlight ruby %}
{% raw %}{{ include.param }}{% endraw %}
{% endhighlight %}

#### 상대 경로 사용하기

현재 파일을 기준으로 상대경로를 사용하여 삽입할 조각 파일을 선택할 수 있습니다:

{% highlight ruby %}
{% raw %}{% include_relative somedir/footer.html %}{% endraw %}
{% endhighlight %}

삽입할 컨텐츠를 꼭 `_includes` 디렉토리에 넣을 필요가 없습니다. 대신 태그가
사용된 파일에서의 상대경로로 삽입이 가능합니다. 예를 들어,
`_posts/2014-09-03-my-file.markdown` 파일 안에서 `include_relative` 태그를
사용했다면, 삽입될 파일은 반드시 `_posts` 디렉토리나 그 하위 디렉토리에 있어야
합니다. 그 밖에 다른 위치의 파일은 삽입할 수 없습니다.

변수 사용처럼 `include` 태그의 다른 모든 기능도 `include_relative` 태그에서
사용할 수 있습니다.

### 코드 구문 강조

[Pygments](http://pygments.org/) 덕분에 Jekyll 은 [100 개 이상의
언어](http://pygments.org/languages/)에 대한 구문 강조 기능이 내장되어 있습니다.
Pygments 를 사용하려면 시스템에 Python 이 설치되어 있어야 하며, 사이트 환경설정
파일에 `highlighter` 를 `pygments` 로 설정해야 합니다.


그 밖에도, [Rouge](https://github.com/jayferd/rouge) 를 사용해서 구문 강조를 할
수 있습니다.
Pygments 만큼 많은 언어를 지원하지는 않지만 대부분의 경우에 사용할 수 있으며
순수하게 Ruby 로 작성되었습니다 ; Python 이 필요하지 않습니다!

구문 강조가 적용된 코드 블럭을 출력하려면, 코드 앞뒤에 다음과 같이 작성합니다:

{% highlight text %}
{% raw %}
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}
{% endraw %}
{% endhighlight %}

`highlight` 태그에 전달한 인자 (위 예시에서는 `ruby`) 는 언어 식별자입니다. 구문
강조를 사용하려고 하는 언어의 식별자를 찾으려면, [Pygments 의 Lexers
페이지](http://pygments.org/docs/lexers/) 또는 [Rouge
위키](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers)에서
"short name" 을 살펴보세요.

#### 줄 번호

`highlight` 의 두 번째 전달인자 `linenos` 는 선택사항입니다.
`linenos` 를 사용하면 코드 블록에 줄 번호가 표시됩니다.
예를 들면, 다음 코드 블록에는 각 줄에 줄 번호가 표시됩니다:


{% highlight text %}
{% raw %}
{% highlight ruby linenos %}
def foo
  puts 'foo'
end
{% endhighlight %}
{% endraw %}
{% endhighlight %}

#### 구문 강조용 스타일시트

강조 부분을 눈에 띄게 만들려면, 구문 강조용 스타일시트를 포함시켜야 합니다.
예를 들면 [syntax.css](https://github.com/mojombo/tpw/tree/master/css/syntax.css)
가 있습니다.
이 파일은 GitHub 에서 사용하는 것과 동일한 스타일이며 당신의 사이트에 마음대로
사용해도 됩니다.
`linenos` 를 사용할 경우, 코드와 줄 번호를 구분하기 위해 `syntax.css` 에
`.lineno` 라는 CSS 클래스를 추가할 수도 있을 것입니다.

### 포스트 URL

만약 사이트 안의 다른 포스트에 대한 링크를 사용해야 할 경우, `post_url` 태그를
사용하면 해당 포스트에 대한 고유주소 URL 이 생성됩니다.

{% highlight text %}
{% raw %}
{% post_url 2010-07-21-name-of-post %}
{% endraw %}
{% endhighlight %}

만약 포스트를 하위 디렉토리에 넣고 관리한다면, 하위 디렉토리 경로도 포함시켜야
합니다:

{% highlight text %}
{% raw %}
{% post_url /subdir/2010-07-21-name-of-post %}
{% endraw %}
{% endhighlight %}

`post_url` 태그를 사용할 때는 파일 확장자를 지정할 필요가 없습니다.

다음과 같이 Markdown 에서도 이 태그를 사용하여 포스트 링크를 생성할 수 있습니다:

{% highlight text %}
{% raw %}
[Name of Link]({% post_url 2010-07-21-name-of-post %})
{% endraw %}
{% endhighlight %}

### Gist

`gist` 태그를 사용하면 사이트에 GitHub Gist 를 쉽게 삽입할 수 있습니다. 공개/비공개 gist 에 모두 사용할 수 있습니다:

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 %}
{% endraw %}
{% endhighlight %}

표시할 파일 이름을 입력할 수도 있습니다:

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 jekyll-private-gist.markdown %}
{% endraw %}
{% endhighlight %}
