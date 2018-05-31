---
#title: Static Files
title: 정적 파일
permalink: /docs/static-files/
---

<!--
In addition to renderable and convertible content, we also have **static
files**.
-->
Jekyll 에는 변환이나 렌더링되는 컨텐츠뿐만 아니라, **정적 파일**이라는 것도
있습니다.

<!--
A static file is a file that does not contain any YAML front matter. These
include images, PDFs, and other un-rendered content.
-->
정적 파일은 YAML 머리말이 없는 파일을 뜻합니다. 이미지나 PDF 들, 그 밖에
렌더링되지 않는 컨텐츠들이 여기에 속합니다.

<!--
They're accessible in Liquid via `site.static_files` and contain the
following metadata:
-->
이 파일들은 `site.static_files` 라는 Liquid 태그를 통해 접근할 수 있으며, 다음과
같은 메타데이터를 갖고 있습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Variable</th>
      <th>Description</th>
-->
      <th>변수</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><p><code>file.path</code></p></td>
      <td><p>

<!--
        The relative path to the file, e.g. <code>/assets/img/image.jpg</code>
-->
        파일에 대한 상대 경로. 예, <code>/assets/img/image.jpg</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.modified_time</code></p></td>
      <td><p>

<!--
        The `Time` the file was last modified, e.g. <code>2016-04-01 16:35:26 +0200</code>
-->
        파일이 마지막으로 수정된 `Time`. 예, <code>2016-04-01 16:35:26 +0200</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.name</code></p></td>
      <td><p>

<!--
        The string name of the file e.g. <code>image.jpg</code> for <code>image.jpg</code>
-->
        파일 이름. 예시, <code>image.jpg</code> 의 경우 <code>image.jpg</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.basename</code></p></td>
      <td><p>

<!--
        The string basename of the file e.g. <code>image</code> for <code>image.jpg</code>
-->
        확장자를 제외한 파일 이름. 예시, <code>image.jpg</code> 의 경우 <code>image</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>file.extname</code></p></td>
      <td><p>

<!--
        The extension name for the file, e.g.
        <code>.jpg</code> for <code>image.jpg</code>
-->
        파일의 확장자 이름. 예시,
        <code>image.jpg</code> 의 경우 <code>.jpg</code>

      </p></td>
    </tr>
  </tbody>
</table>
</div>
