---
layout: step
title: Collections
position: 9
---

각 작성자가 자신의 페이지에 소개글과 자신이 게시한 글이 있도록 작성자를 구체화하는 방법을 살펴봅시다.

이를 위해 컬렉션을 사용합니다. 컬렉션은 게시물과 비슷하지만
콘텐츠를 날짜별로 그룹화할 필요가 없다는 점만 다릅니다.

## 설정

컬렉션을 설정하려면 지킬에게 컬렉션에 대해 알려야 합니다. 지킬 구성
은 `_config.yml` (기본값) 라는 파일에서 이루어집니다.

다음을 참조하여 루트에 `_config.yml`을 생성합니다:

```yaml
collections:
  authors:
```

구성을 (재)로드하려면 jekyll 서버를 재시작해야합니다. 터미널에서 `Ctrl`+`C`를 눌러 서버를 중지한 다음 `jekyll serve`를 눌러 서버를 다시 시작합니다.

## Add authors

문서(컬렉션의 항목)는 사이트 루트의 폴더에 `_*collection_name*`이라는 이름의 폴더에 있습니다. 
이 경우 `_authors`입니다.

각 작성자에 대한 문서:

`_authors/jill.md`:

```markdown
---
short_name: jill
name: Jill Smith
position: Chief Editor
---
Jill is an avid fruit grower based in the south of France.
```

`_authors/ted.md`:

```markdown
---
short_name: ted
name: Ted Doe
position: Writer
---
Ted has been eating fruit since he was baby.
```

## 스태프 페이지

사이트의 모든 작성자를 나열하는 페이지를 추가해 보겠습니다. 지킬은 컬렉션을 `site.authors`에서 사용할 수 있도록 합니다.

`staff.html`을 만들고 `site.authors`를 반복하여 모든 직원을 출력합니다:

{% raw %}
```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

Since the content is markdown, you need to run it through the
`markdownify` filter. This happens automatically when outputting using
{% raw %}`{{ content }}`{% endraw %} in a layout.

콘텐츠가 마크다운되어 있으므로 `markdownify` 필터를 통해 실행해야 합니다. 
이는 레이아웃에서 {% raw %}`{{ content }}`{% endraw %} 사용하여 출력할 때 자동으로 발생합니다.

You also need a way to navigate to this page through the main navigation. Open
`_data/navigation.yml` and add an entry for the staff page:

또한 기본 탐색을 통해 이 페이지로 이동할 수 있는 방법이 필요합니다. 
`_data/navigation.yml` 을 열고 직원 페이지에 대한 항목을 추가합니다:

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
```

## 페이지 출력

기본적으로, 컬렉션은 문서 페이지를 출력하지 않습니다. 이 경우
각 작성자가 고유한 페이지를 갖기를 원하므로 컬렉션의
구성을 조정해 보겠습니다.

`config.yml`을 열고 작성자 컬렉션에 `output: true`를 추가합니다.
구성에 추가합니다.

`config.yml`:

```yaml
collections:
  authors:
    output: true
```

`author.url`을 사용하여 출력 페이지에 링크할 수 있습니다.

`staff.html` 페이지에 링크를 추가합니다:

{% raw %}
```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

글과 마찬가지로 작성자를 위한 레이아웃을 만들어야 합니다.

다음 내용으로 `_layouts/author.html`을 만듭니다:

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}
```
{% endraw %}

## 프론트 기본값

이제 '작성자' 레이아웃을 사용하도록 작성자 문서를 구성해야 합니다. 이전처럼 앞부분에서 이 작업을 수행할 수도 있지만 반복적인 작업이 됩니다.

실제로 원하는 것은 모든 글에 자동으로 글 레이아웃이 적용되고 작성자는 작성자, 그 외 모든 항목이 기본값을 사용하도록 하는 것입니다.

이를 달성하려면 `_config.yml` 파일에서 [앞에서 사용한 기본값](/docs/configuration/front-matter-defaults/)을 사용하면 됩니다.
그리고 기본값이 적용되는 범위를 설정한 다음 원하는 기본값을 설정합니다.

`_config.yml` 에서 원하는 기본값을 추가하세요:

```yaml
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```

이제 모든 페이지와 글의 앞부분에서 레이아웃을 제거할 수 있습니다.
참고로 `_config.yml`을 업데이트시 지킬을 다시 시작해야만 변경 사항을 적용할 수 있습니다.

## List author's posts

작성자가 자신의 페이지에 게시한 글을 나열해 보겠습니다.
이렇게 하려면 작성자 `short_name`을 글 `author`와 일치시켜야 합니다.
필터를 사용하여 작성자별로 글을 필터링합니다.

이 필터링된 목록을 `_layouts/author.html`에서 반복하여 작성자의 글을 출력합니다.

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

## 작성자 페이지로 링크연결

글에 작성자에 대한 참조가 있으므로 작성자의 페이지로 연결해 보겠습니다.
`_layouts/post.html` 에서 유사한 필터링 기법을 사용하여 이 작업을 수행할 수 있습니다:

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}
```
{% endraw %}

<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a> 를 열고
스태프 페이지와 글의 작성자 링크를 확인하여 모든 항목이 올바르게 연결되어 있는지 확인합니다.

이 튜토리얼의 다음이자 마지막 단계에서는 사이트를 다듬고 배포를 준비하겠습니다.
