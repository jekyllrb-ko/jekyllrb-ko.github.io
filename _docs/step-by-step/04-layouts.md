---
layout: step
#title: Layouts
title: 레이아웃
position: 4
---
<!--
Websites typically have more than one page and this website is no different.
-->
웹사이트는 보통 하나 이상의 페이지를 가지고 있으며 이 웹사이트 또한 마찬가지입니다.

<!--
Jekyll supports [Markdown](https://daringfireball.net/projects/markdown/syntax)
as well as HTML for pages. Markdown is a great choice for pages with a simple
content structure (just paragraphs, headings and images), as it's less verbose
than raw HTML. Let's try it out on the next page.
-->
Jekyll 은 HTML 뿐만 아니라 [마크다운](https://daringfireball.net/projects/markdown/syntax)도
지원합니다. 마크다운은 순수 HTML 보다 간략하여, 컨텐츠 구조가 단순한
페이지에 (예시, 문단, 제목, 이미지만 있는 문서) 탁월한
선택입니다. 다음 장에서 직접 해보기로 합니다.

<!--
Create `about.md` in the root.
-->
루트 디렉토리에 `about.md` 를 생성합니다.

<!--
For the structure you could copy `index.html` and modify it for the about page.
The problem with doing this is duplicate code. Let's say you wanted to add a
stylesheet to your site, you would have to go to each page and add it to the
`<head>`. It might not sound so bad for a two page site, imagine doing it
for 100 pages. Even simple changes will take a long time to make.
-->
구조를 통일하기 위해 `index.html` 을 복사하고 수정해서 about 페이지로 만들수도
있을 것입니다. 하지만 문제는 코드가 중복된다는 것입니다. 사이트에 스타일시트를
추가하는 상황을 가정해보면, 모든 페이지를 열어 `<head>` 에 스타일시트를
추가해야할 것입니다. 2 페이지짜리 사이트에서는 문제될 것이 없지만, 100 페이지에
이 작업을 한다고 생각해보세요. 아주 작은 변경사항에도 시간이 많이 걸릴것입니다.

<!--
## Creating a layout
-->
## 레이아웃 생성하기

<!--
Using a layout is a much better choice. Layouts are templates that wrap around
your content. They live in a directory called `_layouts`.
-->
레이아웃을 사용하는게 훨씬 더 나은 선택입니다. 레이아웃은 당신의 컨텐츠를 포장하는
템플릿입니다. `_layouts` 라는 디렉토리에 보관합니다.

<!--
Create your first layout at `_layouts/default.html` with the following content:
-->
다음과 같은 내용으로 `_layouts/default.html` 에 당신의 첫 번째 레이아웃을 생성합니다:

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```
{% endraw %}

<!--
You'll notice this is almost identical to `index.html` except there's
no front matter and the content of the page is replaced with a `content`
variable. `content` is a special variable which has the value of the rendered
content of the page it's called on.
-->
내용이 `index.html` 과 거의 똑같다는 것을 눈치챌 수 있겠지만, 머리말이
없고 페이지의 컨텐츠 부분에 변수 `content` 가 사용되었다는 차이점이
있습니다. `content` 라는 이 특별한 변수는 자신이 호출된 페이지의 컨텐츠를
렌더링 한 내용을 담고 있습니다.

<!--
To have `index.html` use this layout, you can set a `layout` variable in front
matter. The layout wraps around the content of the page so all you need in
`index.html` is:
-->
`index.html` 에 이 레이아웃을 사용하기 위해, `layout` 변수를 머리말에
설정합니다.

{% raw %}
```liquid
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
```
{% endraw %}

<!--
After doing this, the output will be exactly the same as before. Note that you
can access the `page` front matter from the layout. In this case `title` is
set in the index page's front matter but is output in the layout.
-->
이렇게 하면, 출력 결과는 이전과 완벽하게 동일할 것입니다. 기억할 것은
레이아웃으로부터 페이지(`page`)의 머리말에 접근한다는 것입니다. 위 예시에서, `title` 은
인덱스 페이지의 머리말에 설정되었지만 레이아웃에서 출력되었습니다.

<!--
## About page
-->
## 페이지에 관하여

<!--
Back to the about page, instead of copying from `index.html`, you can use the
layout.
-->
about 페이지로 돌아와서, `index.html` 을 복사하는 대신 레이아웃을 사용할 수
있습니다.

<!--
Add the following to `about.md`:
-->
다음 내용을 `about.md` 에 추가합니다:

```markdown
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```

<!--
Open <a href="http://localhost:4000/about.html" target="_blank" data-proofer-ignore>http://localhost:4000/about.html</a>
in your browser and view your new page.
-->
브라우저에서 <a href="http://localhost:4000/about.html" target="_blank" data-proofer-ignore>http://localhost:4000/about.html</a>
를 열어 새 페이지를 확인합니다.

<!--
Congratulations, you now have a two page website! But how do you
navigate from one page to another? Keep reading to find out.
-->
축하합니다. 이제 두 페이지짜리 웹사이트가 생겼네요! 그런데
페이지간의 이동은 어떻게 하죠? 계속해서 알아봅시다.
