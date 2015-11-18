---
layout: docs
title: 템플릿
permalink: /docs/templates/
---

Jekyll 은 템플릿 처리 작업을 위해 [Liquid](https://github.com/Shopify/liquid/wiki) 템플릿
언어를 사용합니다. 표준 Liquid [태그](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#tags)와
[필터](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers#standard-filters)를
모두 지원합니다. 게다가 Jekyll 에만 추가된 필터와 태그도 있어서, 빈도가 높은
작업을 더 쉽게 처리할 수 있습니다.

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
        <p>날짜를 XML 스키마 (ISO 8601) 형식으로 변환한다.</p>
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
        <p>날짜를 RSS 피드에 사용하는 RFC-822 형식으로 변환한다.</p>
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
        <p>날짜를 짧은 형식으로 변환한다.</p>
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
        <p>날짜를 긴 형식으로 변환한다.</p>
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
        <p>배열 안에서 특정 키와 값을 가진 객체들을 선택한다.</p>
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
        <p>배열 안의 항목들을 특정 속성으로 그룹 짓는다.</p>
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
        <p>XML 에 사용되는 몇몇 텍스트를 이스케이프 한다.</p>
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
          로 변환한다.
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
        <p>배열을 한 문장으로 변환한다. 태그를 나열할 때 유용하다.</p>
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
        <p class="name"><strong>Markdownify</strong></p>
        <p>Markdown 포맷 문자열을 HTML 로 변환한다.</p>
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
        <p>Sass 또는 SCSS 형식 문자열을 CSS 로 변환한다.</p>
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
        <p>문자열을 소문자 URL "슬러그"로 변환한다. 자세한 옵션은 아래를 참고하시오.</p>
      </td>
      <td class="align-center">
        <p>
         <code class="filter">{% raw %}{{ "The _config.yml file" | slugify }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-config-yml-file</code>
        </p>
        <p>
         <code class="filter">{% raw %}{{ "The _config.yml file" | slugify: 'pretty' }}{% endraw %}</code>
        </p>
        <p>
          <code class="output">the-_config.yml-file</code>
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p class="name"><strong>Data To JSON</strong></p>
        <p>해시나 배열을 JSON 으로 변환한다.</p>
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
        <p>배열을 정렬한다. 해시에 사용하는 선택적 전달인자: 1.&nbsp;속성 이름 2.&nbsp;nils 순서 (<em>first</em> 또는 <em>last</em>).</p>
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

### `slugify` 필터의 옵션들

`slugify` 필터에는 옵션이 있어서, 무엇을 필터링할 것인지 선택할 수 있습니다.
디폴트값은 `default` 입니다. 옵션값(과 그에 대한 필터링 대상)은 다음과 같습니다:

- `none`: 필터링 안함
- `raw`: 공백문자
- `default`: 알파벳, 숫자가 아닌 문자 또는 공백문자
- `pretty`: 알파벳, 숫자가 아닌 문자 (`._~!$&'()+,;=@` 제외) 또는 공백문자

## 태그

### Includes

사이트의 여기저기에 삽입시키고자 하는 작은 페이지 조각들이 있다면, `include`
태그를 사용하세요.

{% highlight ruby %}
{% raw %}{% include footer.html %}{% endraw %}
{% endhighlight %}

삽입할 파일은 프로젝트 Site Source 디렉토리 안의 `_includes` 디렉토리에 넣어야
합니다. 위 코드를 포함하고 있는 파일에는 `<source>/_includes/footer.html` 의
내용이 삽입됩니다.

<div class="note">
  <h5>ProTip™: 파일명에 변수를 사용하세요</h5>
  <p>

    삽입하고자 하는 파일의 이름은 (위 예제처럼) 실제 파일명을 사용할 수도 있고,
    <code>{% raw %}{% include {{my_variable}} %}{% endraw %}</code> 처럼 Liquid
    스타일의 변수 문법을 사용할 수도 있습니다.

  </p>
</div>

삽입할 파일에 파라메터를 전달할 수도 있습니다. 변수의 값을 전달하려면 따옴표를 사용하지 마십시오. 여기에는 Liquid 의 중괄호를 사용하면 안됩니다:

{% highlight ruby %}
{% raw %}{% include footer.html param="value" variable-param=page.variable %}{% endraw %}
{% endhighlight %}

페이지 조각 안에서 Liquid 로 이 파라메터들을 사용할 수 있습니다:

{% highlight ruby %}
{% raw %}{{ include.param }}{% endraw %}
{% endhighlight %}

#### 상대 경로 사용하기

현재 파일을 기준으로 상대경로를 사용하여 삽입할 조각 파일을 선택할 수 있습니다:

{% highlight ruby %}
{% raw %}{% include_relative somedir/footer.html %}{% endraw %}
{% endhighlight %}

삽입할 컨텐츠를 꼭 `_includes` 디렉토리에 넣어야만 하는것은 아닙니다. 태그가
사용된 파일에서의 상대경로로도 삽입할 수 있습니다. 예를 들어,
`_posts/2014-09-03-my-file.markdown` 파일 안에서 `include_relative` 태그를
사용한다면, 삽입될 파일은 반드시 `_posts` 디렉토리나 그 하위 디렉토리에 있어야
합니다. 그 밖에 다른 위치의 파일은 삽입할 수 없습니다.

변수를 사용하는 것처럼, `include_relative` 태그에서도 `include` 태그의 다른 모든
기능을 사용할 수 있습니다.

### 코드 구문 강조

[Pygments](http://pygments.org/) 덕분에 Jekyll 은 [100 개 이상의
언어](http://pygments.org/languages/)에 대한 구문 강조 기능을 내장하고 있습니다.
Pygments 를 사용하려면, 시스템에 Python 이 설치되어 있어야 하고 사이트 환경설정
파일에 `highlighter` 를 `pygments` 로 설정해야 합니다.


그 밖에도, [Rouge](https://github.com/jayferd/rouge) 를 사용해서 구문 강조를
하는 방법도 있습니다. Pygments 만큼 많은 언어를 지원하는 것은 아니지만, 대부분의
상황에 충분할 것입니다. 또한, [Rouge](https://github.com/jayferd/rouge) 는
순수하게 Ruby 로 작성되었기 때문에, Python 이 필요하지 않습니다!

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

`highlight` 태그에 전달한 인자 (위 예시에서는 `ruby`) 는 언어 식별자입니다.
각 언어에 해당하는 구문 강조용 식별자를 찾으려면, [Pygments 의 Lexer
페이지](http://pygments.org/docs/lexers/) 또는 [Rouge
위키](https://github.com/jayferd/rouge/wiki/List-of-supported-languages-and-lexers)에서
“short name” 을 살펴보세요.

#### 줄 번호

`highlight` 의 두 번째 전달인자인 `linenos` 는 선택사항입니다.
전달인자 `linenos` 를 추가하면 구문 강조된 코드에 줄 번호를 표시합니다.
예를 들어, 다음 코드 블록에는 각 줄에 줄 번호가 표시됩니다:


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

강조 부분을 눈에 띄게 만들려면, 구문 강조용 스타일시트를 추가해야 합니다.
참고해볼만한 스타일시트로는
[syntax.css](https://github.com/mojombo/tpw/tree/master/css/syntax.css) 가
있습니다. 이 스타일은 GitHub 에서 사용하는 것과 동일하며 당신의 사이트에도
자유롭게 사용할 수 있습니다. `linenos` 를 사용하는 경우에는, `syntax.css` 에
`.lineno` 라는 CSS 클래스 선언을 추가해서 줄 번호와 구문 강조된 코드를 구분할 수
있습니다.

### 포스트 URL

사이트 안의 다른 포스트에 대한 링크를 사용해야 하는 경우, `post_url` 태그를
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

`gist` 태그를 사용하면 사이트에 GitHub Gist 를 쉽게 삽입할 수 있습니다.
Gist 의 공개/비공개 상태에 상관없이 사용할 수 있습니다:

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 %}
{% endraw %}
{% endhighlight %}

원한다면 파일명을 표시할 수도 있습니다:

{% highlight text %}
{% raw %}
{% gist parkr/931c1c8d465a04042403 jekyll-private-gist.markdown %}
{% endraw %}
{% endhighlight %}

`gist` 태그를 사용하기 위해서는, [jekyll-gist](https://github.com/jekyll/jekyll-gist) Gem 을 프로젝트에 추가해야 합니다.
