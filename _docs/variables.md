---
layout: docs
title: 변수
prev_section: pages
next_section: collections
permalink: /docs/variables/
---

Jekyll 은 작업 대상 파일을 찾기 위해 사이트 내부를 검색합니다. [YAML 머리말](../frontmatter/)을 가진 파일이 작업 대상입니다. Jekyll 은 각각의 파일마다 [Liquid 템플릿 시스템](https://github.com/Shopify/liquid/wiki)을 통해 다양한 데이터를 만들어냅니다. 사용가능한 데이터 목록은 다음과 같습니다.

## 전역 변수

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
      <td><p><code>site</code></p></td>
      <td><p>

          사이트 정보 + `_config.yml` 의 환경설정 정보. 더 자세한 내용은 아래 참조.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page</code></p></td>
      <td><p>

        페이지 정보 + <a href="../frontmatter/">YAML 머리말</a>. YAML 머리말에 설정된 사용자 변수도 포함됩니다. 더 자세한 내용은 아래 참조.

      </p></td>
    </tr>
    <tr>
      <td><p><code>content</code></p></td>
      <td><p>

        레이아웃에 포함된 포스트 또는 페이지 컨텐츠. 포스트나 페이지 파일에는 정의되어 있지 않습니다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>paginator</code></p></td>
      <td><p>

        When the <code>paginate</code> configuration option is set, this
        variable becomes available for use. See <a
        href="../pagination/">Pagination</a> for details.
        이 변수는 환경설정 옵션 <code>paginate</code> 이 설정되어 있을 때 사용가능합니다. 더 자세한 내용은 <a href="../pagination/">페이지 나누기</a>를 참조.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

## 사이트 변수

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
      <td><p><code>site.time</code></p></td>
      <td><p>

        현재 시간 (<code>jekyll</code> 명령을 실행한 시간).

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.pages</code></p></td>
      <td><p>

        모든 페이지 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.posts</code></p></td>
      <td><p>

        시간 역순의 모든 페이지 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.related_posts</code></p></td>
      <td><p>

        포스트인 경우에, 최대 10 개의 관련 포스트가 이 변수에 담겨 있습니다. 기본적으로는, 처리속도가 빠른 대신 결과의 질이 낮은 방식을 사용합니다. 느린 속도를 감수하고 좋은 결과를 얻으려면, <code>jekyll</code>명령을 <code>--lsi</code> (latent semantic indexing) 옵션과 함께 실행합니다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.static_files</code></p></td>
      <td><p>

        정적 파일 (다시 말해, Jekyll 의 변환기나 Liquid 렌더러가 처리하지 않는 파일들) 전체 목록. 각 파일에는 세 가지 속성이 있다: <code>path</code> 와 <code>modified_time</code>, <code>extname</code>.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.html_pages</code></p></td>
      <td><p>

        모든 HTML 페이지 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.collections</code></p></td>
      <td><p>

        모든 콜렉션 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.data</code></p></td>
      <td><p>

        <code>_data</code> 디렉토리에 있는 YAML 파일에서 읽어들인 데이터 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.documents</code></p></td>
      <td><p>

        각 콜렉션의 모든 문서 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.categories.CATEGORY</code></p></td>
      <td><p>

        <code>CATEGORY</code> 카테고리에 속한 모든 포스트 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.tags.TAG</code></p></td>
      <td><p>

        <code>TAG</code> 태그가 붙은 모든 포스트 목록.

      </p></td>
    </tr>
    <tr>
      <td><p><code>site.[CONFIGURATION_DATA]</code></p></td>
      <td><p>

        All the variables set via the command line and your
        <code>_config.yml</code> are available through the <code>site</code>
        variable. For example, if you have <code>url: http://mysite.com</code>
        in your configuration file, then in your Posts and Pages it will be
        stored in <code>site.url</code>. Jekyll does not parse changes to
        <code>_config.yml</code> in <code>watch</code> mode, you must restart
        Jekyll to see changes to variables.
        명령행이나 `_config.yml` 에 설정된 모든 변수를 `site` 변수를 통해 사용할 수 있습니다. 예를 들어, 환경설정 파일에 `url: http://mysite.com` 가 있다면, 포스트나 페이지에서 `site.url` 을 사용할 수 있습니다. Jekyll 은 `watch` 모드에서도 `_config.yml` 파일의 변경사항을 자동으로 적용하지 않는다. 변수의 변경사항을 적용하려면 Jekyll 을 재시작해야 한다.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

## 페이지 변수

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
      <td><p><code>page.content</code></p></td>
      <td><p>

        페이지의 컨텐츠이며, 렌더링 여부는 어떤 Liquid 처리가 되었는지 어떤 <code>page</code> 인지에 따라 다르다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.title</code></p></td>
      <td><p>

        페이지의 제목.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.excerpt</code></p></td>
      <td><p>

        렌더링 되지 않은 페이지 발췌 부분.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.url</code></p></td>
      <td><p>

        도메인을 제외한, 포스트 URL. 슬래쉬로 시작함. 예시, <code>/2008/12/14/my-post.html</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.date</code></p></td>
      <td><p>

        포스트에 할당된 날짜. 포스트의 머리말에 `YYYY-MM-DD HH:MM:SS` (UTC 기준), 또는 `YYYY-MM-DD HH:MM:SS +/-TTTT` (UTC 오프셋을 사용한 타임 존 지정. 예시, `2008-12-14 10:30:00 +0900`) 형식으로 새로운 날짜/시간을 지정하여 덮어쓸 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.id</code></p></td>
      <td><p>

        포스트에 대한 유일한 식별자 (RSS 피드에 유용함). 예시, <code>/2008/12/14/my-post</code>

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.categories</code></p></td>
      <td><p>

        포스트가 속한 카테고리 목록. 카테고리는 <code>_posts</code> 디렉토리의 상위 디렉토리 구조로부터 파생된다. 예를 들어, <code>/work/code/_posts/2008-12-24-closures.md</code> 에는 이 변수가 <code>['work', 'code']</code> 로 설정되어 있다. 이 변수는 <a href="../frontmatter/">YAML 머리말</a>에서도 설정할 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.tags</code></p></td>
      <td><p>

        포스트에 붙어있는 태그 목록. 이 변수는 <a href="../frontmatter/">YAML 머리말</a>에서도 설정할 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.path</code></p></td>
      <td><p>

        페이지 또는 포스트의 실제 경로. 활용 예시: 페이지 또는 포스트의 GitHub 소스 링크. 이 변수는 <a href="../frontmatter/">YAML 머리말</a>에서도 설정할 수 있다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.next</code></p></td>
      <td><p>

        <code>site.posts</code> 안의 현재 포스트 위치에서 다음 포스트에 대한 상대 경로. 마지막 항목이라면 <code>nil</code> 이 반환된다.

      </p></td>
    </tr>
    <tr>
      <td><p><code>page.previous</code></p></td>
      <td><p>

        <code>site.posts</code> 안의 현재 포스트 위치에서 이전 포스트에 대한 상대 경로. 첫 번째 항목이라면 <code>nil</code> 이 반환된다.

      </p></td>
    </tr>
  </tbody>
</table>
</div>

<div class="note">
  <h5>ProTip™: 사용자 머리말을 사용하세요</h5>
  <p>

    Any custom front matter that you specify will be available under
    <code>page</code>. For example, if you specify <code>custom_css: true</code>
    in a page’s front matter, that value will be available as
    <code>page.custom_css</code>.
    모든 사용자 머리말은 `page` 로 사용할 수 있습니다. 예를 들어, 페이지 머리말에 `custom_css: true` 를 설정한 경우, `page.custom_css` 로 해당 값을 사용할 수 있습니다.

  </p>
</div>

## Paginator

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
      <td><p><code>paginator.per_page</code></p></td>
      <td><p>페이지 당 포스트 수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.posts</code></p></td>
      <td><p>페이지에서 사용할 수 있는 포스트들.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.total_posts</code></p></td>
      <td><p>전체 포스트 수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.total_pages</code></p></td>
      <td><p>전체 페이지 수.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.page</code></p></td>
      <td><p>현재 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.previous_page</code></p></td>
      <td><p>이전 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.previous_page_path</code></p></td>
      <td><p>이전 페이지 경로.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.next_page</code></p></td>
      <td><p>다음 페이지 번호.</p></td>
    </tr>
    <tr>
      <td><p><code>paginator.next_page_path</code></p></td>
      <td><p>다음 페이지 경로.</p></td>
    </tr>
  </tbody>
</table>
</div>

<div class="note info">
  <h5>Paginator 변수 사용 위치</h5>
  <p>

    이 변수들은 오직 인덱스 파일에서만 사용할 수 있지만, `/blog/index.html` 같이 하위 디렉토리에도 해당됩니다.

  </p>
</div>
