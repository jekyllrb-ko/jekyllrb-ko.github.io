---
layout: docs
title: 포스트 작성하기
prev_section: frontmatter
next_section: drafts
permalink: /docs/posts/
---

Jekyll 의 가장 큰 특징 중 하나는 "블로그 지향적" 이라는 것입니다. 이게 정확히
무슨 뜻일까요? 간단히 말하면, 블로그가 Jekyll 의 기본 기능에 녹아들어 있다는
뜻입니다. 글을 작성하고 온라인에 게시하는 것을 생각해봅시다. 자신의 컴퓨터에서
텍스트 파일과 폴더를 관리하는 것만으로 블로그를 운영할 수 있습니다. 번거로운
데이터베이스 설정/관리나 웹 기반의 CMS 시스템과 비교해보면 정말 반가운
특징입니다!

## 포스트 폴더

앞서 [디렉토리 구조](../structure/) 페이지에서 설명했듯이, 블로그 포스트는
`_posts` 폴더에 들어갑니다.
[Markdown](http://daringfireball.net/projects/markdown/) 이나
[Textile](http://redcloth.org/textile) 형식의 텍스트 파일이며, [YAML
머리말](../frontmatter/)이 들어있기만 하면 HTML 페이지로 변환되어 사이트에
포함됩니다.

### 포스트 파일 생성하기

새 포스트를 생성하려면, `_posts` 디렉토리에 새 파일을 생성하기만 하면 됩니다.
이때 중요한 것은 생성할 파일 이름인데, 다음 형식에 맞춰서 생성해야 Jekyll 이
블로그 포스트로 인식하게 됩니다:

{% highlight bash %}
YEAR-MONTH-DAY-title.MARKUP
{% endhighlight %}

여기서 `YEAR` 는 네 자리 숫자, `MONTH` 와 `DAY` 는 두 자리 숫자이고, 확장자
부분의 `MARKUP` 은 파일에 사용된 마크다운 포맷입니다. 올바른 포스트 파일 이름을
예로 들면 다음과 같습니다:

{% highlight bash %}
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.textile
{% endhighlight %}

<div class="note">
  <h5>ProTip™: 다른 포스트로 링크하기</h5>
  <p>
    <a href="../templates#post-url"><code>post_url</code></a> 태그를 사용하면
    사이트 고유주소 스타일이 바뀌는 경우에도 URL 이 잘못될 걱정을 할 필요가
    없습니다.
  </p>
</div>

### 컨텐츠 포맷

모든 블로그 포스트 파일 첫 부분에는 [YAML 머리말](../frontmatter/)을 작성해야
합니다. 다음 할 일은 내용 작성에 사용할 포맷을 선택하는 것 입니다.
Jekyll 은
[Markdown](http://daringfireball.net/projects/markdown/) 과
[Textile](http://redcloth.org/textile) 이라는 두 가지의 인기 컨텐츠 마크업
문법을 지원합니다.
이 두 형식은 서로 다른 고유한 특징을 가지고 있으므로, 자신에게 익숙하고 필요에
맞는 문법을 선택해야 합니다.

<div class="note info">
  <h5>캐릭터 세트를 주의하세요</h5>
  <p>
    컨텐츠 처리기는 결과물이 더 좋게 보이게끔 특정 문자들을 변경하는 것이
    가능합니다. 예를 들어, Redcarpet 변환 표준의 <code>smart</code> 확장기능은
    ASCII 인용 부호를 유니코드 문자로 바꿉니다. 따라서, 이러한 문자들이
    브라우저에 올바르게 표시되게 하려면, 레이아웃 파일의 <code>&lt;head&gt;</code> 에
    <code>&lt;meta charset=&quot;utf-8&quot;&gt;</code> 라고 입력하여 캐릭터
    세트 메타 정보를 정의해야 합니다.
  </p>
</div>

## 이미지와 자원 삽입하기

때때로 글 중간에 이미지, 다운로드 또는 그 밖에 다른 종류의 자원을 삽입해야할
때가 있습니다.
Markdown 과 Textile 에서 자원을 링크시키는 문법이 서로 다르지만, 파일을 어디에
저장할 것인지 결정하는 것은 공통된 문제입니다.

Jekyll 은 유연하기 때문에, 여러가지 방법으로 이를 해결할 수 있습니다.
가장 일반적인 방법 중 하나는 프로젝트의 루트 디렉토리에 `assets` 또는
`downloads` 라는 이름의 디렉토리를 만들어, 이미지와 다운로드 파일, 그 밖의 다른
자료들을 보관하는 것입니다. 그 다음, 어느 포스트에서든지 자원의 경로에 사이트의
루트 URL 을 포함시켜 링크할 수 있습니다.
다시 한 번 말하자면, 이것은 사이트의 (서브)도메인과 경로 설정에 따라 달라집니다.
포스트에서 `site.url` 변수를 사용하여 이 작업을 수행하는 (Markdown) 예시는
다음과 같습니다.

포스트에 이미지를 삽입하려면:

{% highlight text %}
… 는 아래 스크린샷을 보세요:
![친절한 스크린샷]({% raw %}{{ site.url }}{% endraw %}/assets/screenshot.jpg)
{% endhighlight %}

PDF 다운로드 링크를 삽입하려면:

{% highlight text %}
… PDF 를 직접 [다운로드]({% raw %}{{ site.url }}{% endraw %}/assets/mydoc.pdf)할 수 있습니다.
{% endhighlight %}

<div class="note">
  <h5>ProTip™: 사이트 루트 URL 을 사용한 링크</h5>
  <p>
    만약 자신의 사이트가 오직 도메인의 루트 URL 을 통해서만 접근된다고 정확히
    <strong>인지하고</strong> 있다면, <code>{% raw %}{{ site.url }}{% endraw %}</code>
    변수를 제외시켜도 됩니다. 이런 경우에는 단순히 <code>/path/file.jpg</code>
    로 자원을 직접 참조할 수 있습니다.
  </p>
</div>

## 포스트 목록 표시하기

포스트를 폴더로 관리하는 것은 아주 좋은 방법이고 아무런 문제가 없지만, 어딘가에
포스트 목록을 두지 않는다면 아무런 쓸모 없는 블로그가 될 것입니다. 다른 페이지
(또는 [템플릿](../templates/)) 에 포스트 목록을 생성하는 것은 아주 쉽습니다.
[Liquid 템플릿 언어](http://wiki.shopify.com/Liquid)와 그 태그 기능 덕분입니다.
블로그 포스트 링크 목록을 생성하는 기본적인 예제가 여기 있습니다:

{% highlight html %}
<ul>
  {% raw %}{% for post in site.posts %}{% endraw %}
    <li>
      <a href="{% raw %}{{ post.url }}{% endraw %}">{% raw %}{{ post.title }}{% endraw %}</a>
    </li>
  {% raw %}{% endfor %}{% endraw %}
</ul>
{% endhighlight %}

물론, 자신의 포스트를 어디에 (그리고 어떻게) 표시할 것인지, 사이트를 어떻게
구성할 것인지는 당신 마음에 달렸습니다. 더 자세한 내용을 알고 싶다면, Jekyll
에서 [템플릿이 작동하는 방법](../templates/)을 읽어보세요.

위 예제에서 `post` 변수는 오직 `for` 루프 안에서만 존재한다는 것에 주의하세요.
만약 현재-작업중인 페이지/포스트의 변수 (`for` 루프를 포함하고 있는
포스트/페이지의 변수) 에 접근하고자 한다면, `post` 대신 `page` 변수를
사용하세요.

## 포스트 발췌

모든 포스트의 첫 블록 - 컨텐츠 시작부분부터 `excerpt_separator` 가 처음 나오는
부분까지 - 은 `post.excerpt` 로 설정됩니다.
위 포스트 목록 예제를 다시 살펴봅시다.
포스트 내용에 대한 작은 힌트를 주기 위해 각 포스트의 첫 문단을 목록에 추가하는
것이 가능합니다:

{% highlight html %}
<ul>
  {% raw %}{% for post in site.posts %}{% endraw %}
    <li>
      <a href="{% raw %}{{ post.url }}{% endraw %}">{% raw %}{{ post.title }}{% endraw %}</a>
      {% raw %}{{ post.excerpt }}{% endraw %}
    </li>
  {% raw %}{% endfor %}{% endraw %}
</ul>
{% endhighlight %}

발췌된 부분을 일부러 `p` 태그로 감쌀 필요가 없습니다. Jekyll 이 첫 문단을
잡아내어 대신 해주기 때문이죠. 원한다면 다음과 같이 입력하여 태그를 제거할 수도 있습니다:

{% highlight html %}
{% raw %}{{ post.excerpt | remove: '<p>' | remove: '</p>' }}{% endraw %}
{% endhighlight %}

자동으로 생성되는 포스트 발췌가 맘에 들지 않는다면, 포스트의 YAML 머리말에
`excerpt` 를 추가하여 원하는 값으로 덮어쓸 수 있습니다. 완전히 비활성화 하려면
`excerpt_separator` 를 `""` 로 설정합니다.

또한, Liquid 태그에 의하여 생성된 결과에는 `| strip_html` 플래그를 사용하여 HTML 태그들을 제거할 수 있습니다. 이는 포스트 발췌부분을 포스트 `head` 의 `meta="description"` 태그에 사용하는 경우나 컨텐츠에 HTML 태그가 필요없는 특별한 상황에 유용합니다.

## 코드 구문 강조

Jekyll 은 코드 삽입과 Pygments 나 Rouge 를 사용한 코드 구문 강조도
기본 기능으로 포함하고 있습니다. 간단히 다음과 같이 전용 Liquid 태그를
사용하면 됩니다:

{% highlight text %}
{% raw %}{% highlight ruby %}{% endraw %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% raw %}{% endhighlight %}{% endraw %}
{% endhighlight %}

결과는 이렇게 보일 것입니다:

{% highlight ruby %}
def show
  @widget = Widget(params[:id])
  respond_to do |format|
    format.html # show.html.erb
    format.json { render json: @widget }
  end
end
{% endhighlight %}

<div class="note">
  <h5>ProTip™: 줄 번호 표시하기</h5>
  <p>
    다음과 같이 강조 시작 태그의 끝에 <code>linenos</code> 를 추가하여 코드에 줄
    번호를 표시할 수 있습니다:
    <code>{% raw %}{% highlight ruby linenos %}{% endraw %}</code>
  </p>
</div>

이로써 포스트를 작성하는데에 필요한 기초지식은 충분히 살펴보았습니다. 이 밖에 또
무엇이 가능한지 좀 더 파고들 준비가 되었다면, [포스트 고유주소
수정하기](../permalinks/)나 사이트에 [사용자 변수](../variables/)를 사용하는 것
등을 살펴보세요.
