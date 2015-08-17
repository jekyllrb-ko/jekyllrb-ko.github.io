---
layout: docs
title: 고유주소
permalink: /docs/permalinks/
---

Jekyll 의 사이트 URL 구성 방법은 아주 유연합니다.
[환경설정](../configuration/)을 통해서 사이트의 고유주소를 설정하거나 [YAML
머리말](../frontmatter/)로 각 포스트의 고유주소를 설정할 수 있습니다. Jekyll 에
내장된 스타일을 사용해도 되고 자신만의 링크를 만들어도 됩니다. 기본 스타일은
`date` 입니다.

고유주소는 템플릿 URL 에 의해 구성되고, 템플릿 URL 은 동적 요소들로 이루어 지며,
동적 요소는 키워드 앞에 콜론을 붙여 나타냅니다. 예를 들어, 고유주소 기본값인
`date` 의 형식은 `/:categories/:year/:month/:day/:title.html` 로 정의되어 있습니다.

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
        <p>
            파일 이름에 정의된 제목. YAML 머리말의 <code>slug</code> 로 설정을
            덮어쓸 수 있습니다.
        </p>
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

[템플릿 변수](#template-variables)를 사용하여 고유주소 스타일을 지정할 수
있지만, 편의를 위해 Jekyll 에서 빌트-인으로 제공하는 고유주소 스타일도 있다.

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
        <p><code>ordinal</code></p>
      </td>
      <td>
        <p><code>/:categories/:year/:y_dat/:title.html</code></p>
      </td>
    </tr>
    <tr>
      </td>
        <p><code>none</code></p>
      </td>
      <td>
        <p><code>/:categories/:title.html</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 페이지와 콜렉션

<div class="note unreleased">
  <h5>페이지와 콜렉션 고유주소의 기능 개선은 아직 릴리스되지 않았습니다.</h5>
  <p>
    이 기능을 사용하려면, <a href="/docs/installation/#pre-releases">Jekyll 의
    최신 개발 버전을 설치하세요</a>.
  </p>
</div>

환경설정 `permalink` 를 사용하면 포스트의 고유주소 스타일을 지정할 수 있습니다.
페이지와 콜렉션은 서로 다른 기본 고유주소 스타일을 가지고 있습니다; 페이지의
기본 스타일은 `/:path/:basename` 이고 콜렉션의 기본 스타일은
`/:collection/:path` 입니다.

이 스타일을 수정하여 포스트 고유주소의 접미 스타일을 조정할 수 잇씁니다. 예를
들어, 고유주소 스타일을 `pretty` 로 설정하면, 페이지 고유주소의 끝에 슬래쉬를
추가합니다: `/:path/:basename/`. 고유주소 스타일을 `date` 로 설정하면, 페이지
고유주소의 끝에 확장자를 추가합니다: `/:path/:basename:output_ext`. 어떤
고유주소 스타일이든지 이와 같이 동작합니다.


페이지나 문서의 [YAML 머리말](../frontmatter/) 을 수정하여 언제든지 개별적으로
페이지나 콜렉션 문서의 고유주소를 덮어쓸 수 있습니다.
또한, 특정 콜렉션의 고유주소는 [콜렉션 환경설정에서](../collections/)도 변경할
수 있습니다.

## 고유주소 스타일 예시

포스트 이름: `/2009-04-29-slap-chop.md`

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
        <p><code>/blog/:year/:month/:day/:title/</code></p>
      </td>
      <td>
        <p><code>/blog/2009/04/29/slap-chop/</code></p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>/:year/:month/:title</code></p>
        <p>자세한 사항은 <a href="#extensionless-permalinks">확장자 없는 고유주소</a>를 참고하세요.</p>
      </td>
      <td>
        <p><code>/2009/04/slap-chop</code></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

## 확장자 없는 고유주소

<div class="note unreleased">
  <h5>확장자 없는 고유주소 기능은 아직 릴리스되지 않았습니다.</h5>
  <p>
    이 기능을 사용하려면, <a href="/docs/installation/#pre-releases">Jekyll 의
    최신 개발 버전을 설치하세요</a>.
  </p>
</div>

Jekyll 은 끝부분에 슬래쉬나 파일 확장자를 포함하지 않는 고유주소를 지원하지만,
올바르게 작동하려면 추가적으로 웹 서버의 지원을 필요로 합니다. 확장자 없는
고유주소를 사용할 때, 생성되는 사이트 파일은 여전히 파일 확장자를 가지고 있기
때문에 (일반적으로 `.html`), 웹 서버가 확장자 없이 들어오는 요청을 이 파일에
매핑해줘야만 합니다.

[Github Pages](../github-pages/) 와 Jekyll 에 빌트-인 되어 있는 WEBrick 서버는
추가 작업 없이 이러한 요청을 처리할 수 있습니다.

### Apache

Apache 웹 서버는 컨텐츠 선택에 관련된 지원을 광범위하게 제공하며 `httpd.conf`
또는 `.htaccess` 파일의 [multiviews][] 옵션을 설정해서 확장자 없는 URL 을 처리할
수 있습니다:

[multiviews]: https://httpd.apache.org/docs/current/content-negotiation.html#multiviews

{% highlight apache %}
Options +MultiViews
{% endhighlight %}

### Nginx

[try_files][] 옵션으로 요청을 처리하기 위한 파일 검색 목록을 정의할 수 있습니다.
환경설정을 다음과 같이 하면 nginx 가 요청 받은 URI 에 해당하는 파일을 찾지
못했을 때 `.html` 확장자를 가진 파일을 검색합니다.


[try_files]: http://nginx.org/en/docs/http/ngx_http_core_module.html#try_files

{% highlight nginx %}
try_files $uri $uri.html $uri/ =404;
{% endhighlight %}
