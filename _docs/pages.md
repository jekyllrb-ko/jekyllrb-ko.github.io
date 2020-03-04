---
#title: Pages
title: 페이지
permalink: /docs/pages/
---

<!--
Pages are the most basic building block for content. They're useful for standalone
content (content which is not date based or is not a group of content such as staff
members or recipes).
-->
페이지는 컨텐츠를 구성하는 가장 기본적인 요소입니다. 단독
컨텐츠 (날짜별로 구성되거나, 스태프 멤버 또는 레시피 같이 그룹지어지지 않는 컨텐츠) 를
구성하는데 유용하게 쓰입니다.

<!--
The simplest way of adding a page is to add an HTML file in the root
directory with a suitable filename. You can also write a page in Markdown using
a `.md` extension which converts to HTML on build. For a site with
a homepage, an about page, and a contact page, here’s what the root directory
and associated URLs might look like:
-->
페이지를 추가하는 가장 간단한 방법은 루트 디렉토리에 적절한 이름으로 HTML
파일을 추가하는 것입니다. 또한 마크다운으로 페이지를 작성하여
`.md` 확장자를 사용하면 빌드시에 HTML 로 변환됩니다. 예를 들어
홈페이지와 소개 (About) 페이지, 연락처 (Contact) 페이지를 가진 사이트에서, 루트 디렉토리의
내용과 각각에 해당하는 URL 은 다음과 같습니다:

```sh
.
|-- about.md    # => http://example.com/about.html
|-- index.html    # => http://example.com/
└── contact.html  # => http://example.com/contact.html
```

<!--
If you have a lot of pages, you can organize them into subfolders. The same subfolders that are used to group your pages in your project's source will then exist in the `_site` folder when your site builds. However, when a page has a *different* permalink set in the front matter, the subfolder at `_site` changes accordingly.
-->
페이지가 많이 있는 경우에는, 하위 폴더로 정리할 수 있습니다. 사이트 빌드 시, 사이트 소스에서 페이지를 그룹지을 때 사용한 하위 폴더가 동일한 형태로 `_site` 폴더 안에 생성됩니다. 하지만, 페이지의 머리말에 *다른* 고유주소가 설정되어 있으면, `_site` 의 하위 폴더는 이에 맞게 변형됩니다.

<!--
```sh
.
|-- about.md          # => http://example.com/about.html
|-- documentation     # folder containing pages
    └── doc1.md       # => http://example.com/documentation/doc1.html
|-- design            # folder containing pages
    └── draft.md      # => http://example.com/design/draft.html
```
-->
```sh
.
|-- about.md          # => http://example.com/about.html
|-- documentation     # 페이지가 들어있는 폴더
    └── doc1.md       # => http://example.com/documentation/doc1.html
|-- design            # 페이지가 들어있는 폴더
    └── draft.md      # => http://example.com/design/draft.html
```

<!--
## Changing the output URL
-->
## 결과 URL 바꾸기

<!--
You might want to have a particular folder structure for your source files that changes for the built site. With [permalinks](/docs/permalinks) you have full control of the output URL.
-->
생성된 사이트에서는 소스 파일과는 다른 형태의 폴더 구조를 원할 수도 있을 것입니다. [고유주소](/docs/permalinks)를 사용하면 결과 URL 을 완벽하게 조정할 수 있습니다.
