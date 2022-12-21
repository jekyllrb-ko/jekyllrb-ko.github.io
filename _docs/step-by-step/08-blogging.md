---
layout: step
# title: Blogging
title: 블로깅
position: 8
---
<!-- You might be wondering how you can have a blog without a database. In true
Jekyll style, blogging is powered by text files only. -->
어떻게 데이터베이스 없이 블로그를 가질 수 있는지 궁금할 것입니다.
진정한 의미의 Jekyll 스타일 블로그는 텍스트 파일로만 작동합니다.

<!-- ## Posts -->
## 포스트

<!-- Blog posts live in a folder called `_posts`. The filename for posts have a
special format: the publish date, then a title, followed by an extension. -->
블로그 포스트은 `_post`라고 불리는 폴더에 저장됩니다.
포스트의 파일이름은 게시 날짜-제목-확장자 순의 특별한 형식을 가지고 있습니다.

<!-- Create your first post at `_posts/2018-08-20-bananas.md` with the
following content: -->
다음 내용을 포함해 `_posts/2018-08-20-bananas.md`이라는 첫 포스트을 만들어보세요:

```markdown
---
layout: post
author: jill
---
A banana is an edible fruit – botanically a berry – produced by several kinds
of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size, color,
and firmness, but is usually elongated and curved, with soft flesh rich in
starch covered with a rind, which may be green, yellow, red, purple, or brown
when ripe.
```
<!-- 
This is like the `about.md` you created before except it has an author and
a different layout. `author` is a custom variable, it's not required and could
have been named something like `creator`. -->
저자와 레이아웃이 다르다는 것을 제외하면 이전에 만든 `about.md` 파일과 같습니다.
`저자`는 사용자 지정 변수이며, 필수적이지 않고 `제작자`와 같은 이름으로 지정될 수 있습니다.

<!-- ## Layout -->
## 레이아웃

<!-- The `post` layout doesn't exist so you'll need to create it at
`_layouts/post.html` with the following content: -->
이 `포스트` 레이아웃은 존재하지 않기 때문에 `_layouts/post.html`을 다음과 같이 만들어야 합니다:

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}
```
{% endraw %}

<!-- This is an example of layout inheritance. The post layout outputs the title,
date, author and content body which is wrapped by the default layout. -->
이것은 레이아웃의 상속에 대한 예제입니다. 이 포스트 레이아웃은 기본 레이아웃으로 감싼 제목과,
날짜 그리고 저자의 내용을 출력합니다.

<!-- Also note the `date_to_string` filter, this formats a date into a nicer format. -->
또한 `date_to_string` 필터를 주목하세요. 이 필터는 더 나은 서식을 만들어줍니다.

<!-- ## List posts -->
## 포스트 리스트

<!-- There's currently no way to navigate to the blog post. Typically a blog has a
page which lists all the posts, let's do that next. -->
현재로서는 블로그 포스트로 이동할 방법이 없습니다.
일반적인 블로그는 포스트가 나열된 페이지를 가지고 있습니다. 다음과 같이 해보세요.


<!-- Jekyll makes posts available at `site.posts`. -->
Jekyll는 `site.posts`를 통해 포스트을 이용할 수 있게 만듭니다.

<!-- Create `blog.html` in your root (`/blog.html`) with the following content: -->
다음 내용을 포함하여 `blog.html`를 만들고, 최상위 폴더에(`/blog.html`) 추가해보세요:

{% raw %}
```liquid
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

<!-- There's a few things to note with this code: -->
다음 코드에는 주목해야 할 몇 가지 부분이 있습니다.

<!-- * `post.url` is automatically set by Jekyll to the output path of the post
* `post.title` is pulled from the post filename and can be overridden by
setting `title` in front matter
* `post.excerpt` is the first paragraph of content by default -->
* `post.url`은 Jekyll에 의해 포스트 경로가 자동으로 설정됩니다.
* `post.title`은 포스트 파일 이름에서 추출되며 앞에 `제목`을 설정하여 재정의할 수 있습니다.
* `post.excerpt`는 기본적으로 내용의 첫 번째 단락입니다.

<!-- You also need a way to navigate to this page through the main navigation. Open
`_data/navigation.yml` and add an entry for the blog page: -->
또한 메인 네비게이션을 통해 이 페이지로 이동하는 방법이 필요할 것입니다.
`_data/navigation.yml`을 열고, 블로그 페이지에 대한 항목을 추가해보세요.

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

<!-- ## More posts -->
## 더 많은 포스트

<!-- A blog isn't very exciting with a single post. Add a few more: -->
블로그는 하나의 포스트로는 굉장히 흥미롭지 않습니다. 조금 더 추가해보세요:

`_posts/2018-08-21-apples.md`:

```markdown
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in
the genus Malus. The tree originated in Central Asia, where its wild ancestor,
Malus sieversii, is still found today. Apples have been grown for thousands of
years in Asia and Europe, and were brought to North America by European
colonists.
```

`_posts/2018-08-22-kiwifruit.md`:

```markdown
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible
berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large
hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in
diameter). It has a fibrous, dull greenish-brown skin and bright green or
golden flesh with rows of tiny, black, edible seeds. The fruit has a soft
texture, with a sweet and unique flavor.
```

<!-- Open <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
and have a look through your blog posts. -->
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>를 열어
블로그 포스트을 확인해보세요.

<!-- Next we'll focus on creating a page for each post author. -->
다음은 각 포스트 저자를 위한 페이지를 만들어 볼 것입니다.
