---
layout: docs
title: 페이지 생성하기
prev_section: drafts
next_section: variables
permalink: /docs/pages/
---

Jekyll 은 [포스트 작성](../posts/)뿐만 아니라 정적 페이지 생성에도 사용할 수
있습니다. 디렉토리와 파일을 복사하는 Jekyll 의 동작 방식을 활용하면 너무나도
쉽습니다.

## 홈페이지

당신이 접하는 거의 모든 웹 서버 환경설정이 사이트의 루트 폴더에서 (관례상)
`index.html` 라는 이름의 HTML 파일을 찾아 홈페이지로 보여줍니다. 웹 서버가 다른
파일을 찾도록 설정되어 있지 않는 한, 이 파일이 사이트의 홈페이지가 됩니다.



<div class="note">
  <h5>ProTip™: 홈페이지에 레이아웃을 사용하세요</h5>
  <p>
    사이트의 모든 HTML 파일에 <code>_layouts</code> 와 <code>_includes</code> 를
    사용할 수 있습니다. 홈페이지도 예외는 아니죠. 레이아웃으로 추출할 만한 좋은
    후보감으로는 헤더나 푸터 같은 공용 컨텐츠가 있습니다.
  </p>
</div>

## 페이지의 위치

HTML 파일을 생성하는 위치에 따라 페이지 작동 방식이 달라집니다. 페이지를
생성하는 방법은 두 가지가 있습니다:

- 사이트의 루트 폴더에 각 페이지 별 HTML 파일을 만든다.
- 사이트의 루트 폴더에 각 페이지 별 폴더를 만들고, 각 폴더에 index.html 파일을
  만든다.

어떤 방법을 사용하든지 (또는 두 방법을 함께 사용해도) 잘 작동합니다. 하지만,
최종 URL 모양이 서로 다릅니다.

### HTML 파일에 이름 쓰기

페이지를 추가하는 가장 간단한 방법은 루트 디렉토리에 생성하고자 하는 페이지
이름을 가진 HTML 파일을 추가하는 것입니다. 다음은 홈페이지와 about 페이지,
contact 페이지를 추가한 루트 디렉토리와 그 URL 의 모습입니다:


{% highlight bash %}
.
|-- _config.yml
|-- _includes/
|-- _layouts/
|-- _posts/
|-- _site/
|-- about.html    # => http://yoursite.com/about.html
|-- index.html    # => http://yoursite.com/
└── contact.html  # => http://yoursite.com/contact.html
{% endhighlight %}

### 디렉토리에 이름 쓰고 인덱스 HTML 파일 넣기

위에 소개한 방법은 아무런 문제없이 잘 작동합니다만,
파일 확장자 같은 것들이 보이지 않는 단순한 URL 을 좋아하는 사람들도 있습니다.
Jekyll 의 페이지 URL 을 깔끔하게 만들려면, 각 페이지 별로 폴더를 만들고 그 안에
`index.html` 파일을 넣으면 됩니다.
이렇게 하면 폴더 이름으로 끝나는 URL 을 사용할 수 있으며, 웹 서버는 그에 맞는
`index.html` 파일을 보여줄 것입니다.
이 구조를 가진 예시는 다음과 같습니다:

{% highlight bash %}
.
├── _config.yml
├── _includes/
├── _layouts/
├── _posts/
├── _site/
├── about/
|   └── index.html  # => http://yoursite.com/about/
├── contact/
|   └── index.html  # => http://yoursite.com/contact/
└── index.html      # => http://yoursite.com/
{% endhighlight %}

모든 사람들에게 적합한 방법은 아닐 수도 있지만, 깔끔한 URL 을 좋아하는
사람들에게는 아주 쉬운 방법이며 잘 작동합니다. 선택은 당신의 몫입니다!
