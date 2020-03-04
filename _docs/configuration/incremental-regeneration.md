---
#title: Default Configuration
title: 기본 환경설정
permalink: "/docs/configuration/incremental-regeneration/"
---

<!--
## Incremental Regeneration
-->
## 증분 재생성
<div class="note warning">
<!--
  <h5>Incremental regeneration is still an experimental feature</h5>
-->
  <h5>증분 재생성은 여전히 개발 진행중인 기능입니다</h5>
  <p>
<!--
    While incremental regeneration will work for the most common cases, it will
    not work correctly in every scenario. Please be extremely cautious when
    using the feature, and report any problems not listed below by
    <a href="https://github.com/jekyll/jekyll/issues/new">opening an issue on GitHub</a>.
-->
    비록 증분 재생성이 대부분의 경우에 잘 작동하긴 하지만, 모든 상황에서 올바르게
    작동할 것이라고 말할 수는 없습니다. 이 기능을 사용할 때에는 부디 주의를
    기울여주시기 바라며, 아래 언급되지 않은 새로운 문제점이 있다면
    <a href="https://github.com/jekyll/jekyll/issues/new">GitHub 에 이슈를 등록</a>해주세요.
  </p>
</div>

<!--
Incremental regeneration helps shorten build times by only generating documents
and pages that were updated since the previous build. It does this by keeping
track of both file modification times and inter-document dependencies in the
`.jekyll-metadata` file.
-->
증분 재생성은 마지막으로 빌드한 시점 이후에 갱신된 문서와 페이지만
재생성하여 빌드 시간을 줄여줍니다. `.jekyll-metadata` 파일에 문서
사이의 의존관계와 수정시간 정보의 변화를 기록해서 변경된 파일을
감지합니다.

<!--
Under the current implementation, incremental regeneration will only generate a
document or page if either it, or one of its dependencies, is modified. Currently,
the only types of dependencies tracked are includes (using the
{% raw %}`{% include %}`{% endraw %} tag) and layouts. This means that plain
references to other documents (for example, the common case of iterating over
`site.posts` in a post listings page) will not be detected as a dependency.
-->
현재 구현 상으로, 이 기능은 문서나 페이지 혹은 그 의존관계가 변경되었을 때만
파일을 다시 생성합니다. 현재, 감지할 수 있는 의존관계 종류는 조각파일
({% raw %}`{% include %}`{% endraw %} 태그 사용) 과 레이아웃 뿐입니다.
다른 문서에 대한 일반적인 참조는 의존관계로서 감지되지 않는다는 뜻입니다.
(예를 들면, 게시물 목록 페이지에서 `site.posts` 를 순환하는 것)

<!--
To remedy some of these shortfalls, putting `regenerate: true` in the front-matter
of a document will force Jekyll to regenerate it regardless of whether it has been
modified. Note that this will generate the specified document only; references
to other documents' contents will not work since they won't be re-rendered.
-->
이에 대한 해결책으로, 문서의 머리말에 `regenerate: true` 를 추가해 문서의 수정 여부에
관계없이 강제로 Jekyll 이 해당 문서를 재생성하게 하는 방법이 있습니다. 오로지 해당
문서만 다시 생성된다는 점을 기억하세요; 다른 문서의 내용에 대한 참조는 해당되지
않습니다.

<!--
Incremental regeneration can be enabled via the `--incremental` flag (`-I` for
short) from the command-line or by setting `incremental: true` in your
configuration file.
-->
증분 재생성 기능을 활성화하는 방법으로는 명령행에서 `--incremental` 플래그
(짧게는 `-I`) 를 사용하는 것과 환경설정 파일에 `incremental: true` 를
설정하는 방법이 있습니다.
