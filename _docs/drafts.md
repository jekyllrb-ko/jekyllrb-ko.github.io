---
#title: Working with drafts
title: 초안 활용하기
permalink: /docs/drafts/
---

<!--
Drafts are posts without a date. They're posts you're still working on and
don't want to publish yet. To get up and running with drafts, create a
`_drafts` folder in your site's root (as described in the [site structure](/docs/structure/) section) and create your
first draft:
-->
초안이란 날짜 정보가 없는 포스트입니다. 현재 작성중이기 때문에 아직은 온라인에
게시하고 싶지 않은 포스트를 의미합니다. 초안 기능을 사용하려면, 사이트의 루트
디렉토리에 `_drafts` 폴더를 만들고 ([디렉토리 구조](/docs/structure/) 섹션 참조)
초안을 생성하면 됩니다:

```text
|-- _drafts/
|   |-- a-draft-post.md
```

<!--
To preview your site with drafts, simply run `jekyll serve` or `jekyll build`
with the `--drafts` switch. Each will be assigned the value modification time
of the draft file for its date, and thus you will see currently edited drafts
as the latest posts.
-->
초안을 포함해서 사이트를 미리보기 하려면, `jekyll serve` 나 `jekyll build`
명령에 `--drafts` 스위치를 추가해서 실행하기만 하면 됩니다. 초안 파일의 마지막
수정시간이 초안의 작성시간으로 할당되기 때문에, 현재 작성중인 초안은 가장 최신
포스트로 표시됩니다.
