---
layout: docs
title: 고유주소
prev_section: templates
next_section: pagination
permalink: /docs/permalinks/
---

Jekyll 의 사이트 URL 구성 방법은 아주 유연합니다.
[환경설정](../configuration/)을 통해서 사이트의 고유주소를 설정하거나 [YAML
머리말](../frontmatter/)로 각 포스트의 고유주소를 설정할 수 있습니다. Jekyll 에
내장된 스타일을 사용해도 되고 자신만의 링크를 만들어도 됩니다. 기본 스타일은
`date` 입니다.

고유주소는 템플릿 URL 에 의해 구성되고, 템플릿 URL 은 동적 요소들로 이루어 지며,
동적 요소는 키워드 앞에 콜론을 붙여 나타냅니다. 예를 들어, 고유주소 기본값인
`date` 의 정의는 `/:categories/:year/:month/:day/:title.html` 입니다.

## 템플릿 변수

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
      <td>
        <p><code>year</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 연도</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>month</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 월</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_month</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 월 (한 자리일 경우 앞에 0 이 없음)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>day</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 일</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>i_day</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 일 (한 자리일 경우 앞에 0 이 없음)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>short_year</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 연도 (두 자리)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>title</code></p>
      </td>
      <td>
        <p>포스트 파일 이름의 제목</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>categories</code></p>
      </td>
      <td>
        <p>
          해당 포스트에 지정된 카테고리들. 만약 포스트가 여러 카테고리에
          속해있다면, 계층 구조로 URL 이 생성됩니다 (예시.
          <code>/category1/category2</code>). 또한, Jekyll 은 URL 에서 연속된
          슬래시를 자동으로 처리하기 때문에, 카테고리가 없을 경우 이 설정은 무시됩니다.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 내장된 고유주소 스타일

**주의:** 이 기능은 포스트에만 적용될 것입니다. 페이지나 콜렉션, 정적인
파일들에는 해당되지 않습니다. 예를 들면, 페이지가 HTML 일 경우 `pretty` 는
페이지의 고유주소를 `/:path/:basename:output_ext` 에서 `/:page/:basename/` 으로
변경되어, 페이지의 고유주소가 "prettyifying" 됩니다. `date` 나 `none` 및 다른
모든 사용자 변수는 페이지에 적용되지 않습니다. 정적 파일에는 고유주소 스타일이
적용되지 않으며, 콜렉션에는 고유주소를 설정하는 방법이 별도로 존재합니다. 상당히
혼동스럽지만 [Issue #2691](https://github.com/jekyll/jekyll/issues/2691) 을
읽어보면 해당 주제에 대한 배경지식을 얻을 수 있습니다. 또한 이를 고칠 모험심이
강한 분은 PR 을 제출해 주시기 바랍니다!

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>고유주소 스타일</th>
      <th>URL 템플릿</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>pretty</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:month/:day/:title/</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>none</code></p>
      </td>
      <td>
        <p><code>/:categories/:title.html</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 고유주소 스타일 예시

포스트 이름: `/2009-04-29-slap-chop.textile`

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>URL 템플릿</th>
      <th>고유주소 URL 결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p>설정하지 않음, 또는 <code>permalink: date</code></p>
      </td>
      <td>
        <p><code>/2009/04/29/slap-chop.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>pretty</code></p>
      </td>
      <td>
        <p><code>/2009/04/29/slap-chop/index.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>/:month-:day-:year/:title.html</code></p>
      </td>
      <td>
        <p><code>/04-29-2009/slap-chop.html</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>/blog/:year/:month/:day/:title</code></p>
      </td>
      <td>
        <p><code>/blog/2009/04/29/slap-chop/index.html</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>
