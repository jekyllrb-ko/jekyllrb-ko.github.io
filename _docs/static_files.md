---
layout: docs
title: 정적 파일
permalink: /docs/static-files/
---

Jekyll 에는 변환이나 렌더링되는 컨텐츠뿐만 아니라, **정적 파일**이라는 것도
있습니다.

정적 파일은 YAML 머리말이 없는 파일을 뜻합니다. 이미지나 PDF 들, 그 밖에
렌더링되지 않는 컨텐츠들이 여기에 속합니다.

이 파일들은 `site.static_files` 라는 Liquid 태그를 통해 접근할 수 있으며, 다음과
같은 메타데이터를 갖고 있습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><code>file.path</code></p></td>
      <td><p>

        파일에 대한 상대 경로.

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.modified_time</code></p></td>
      <td><p>

        파일이 마지막으로 수정된 `Time`.

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.extname</code></p></td>
      <td><p>

        파일의 확장자 이름. 예를 들어,
        <code>image.jpg</code> 의 경우 <code>.jpg</code>.

      </p></td>
    </tr>
  </tbody>
</table>
</div>
