---
layout: docs
title: 초안 활용하기
prev_section: posts
next_section: pages
permalink: /docs/drafts/
---

초안은 날짜가 없는 포스트입니다. 아직 작성이 끝나지 않아 온라인에 게시하고 싶지
않은 포스트를 초안이라고 부릅니다. 초안 기능을 사용하려면, 사이트의 루트
디렉토리 ([디렉토리 구조](/docs/structure/) 섹션 참조) 에 `_drafts` 폴더를
만들고 초안을 넣으면 됩니다:

{% highlight text %}
|-- _drafts/
|   |-- a-draft-post.md
{% endhighlight %}

사이트의 미리보기에 초안을 포함시키려면, `jekyll serve` 나 `jekyll build` 에
`--drafts` 스위치를 추가해서 실행합니다. 초안의 작성시간은 해당 파일의
수정시간이기 때문에, 제일 최신 포스트처럼 표시될 것입니다.
