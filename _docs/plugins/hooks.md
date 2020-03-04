---
#title: Hooks
title: 훅
permalink: /docs/plugins/hooks/
---

<!--
Using hooks, your plugin can exercise fine-grained control over various aspects
of the build process. If your plugin defines any hooks, Jekyll will call them
at pre-defined points.
-->
Hook 을 사용하면, 당신의 플러그인이 사이트 빌드에 다방면으로 정교한 작업을
수행할 수 있습니다. 당신의 플러그인에 Hook 이 포함되어 있으면, Jekyll 은 정해진
시점에 해당 Hook 을 호출합니다.

<!--
Hooks are registered to a container and an event name. To register one, you
call Jekyll::Hooks.register, and pass the container, event name, and code to
call whenever the hook is triggered. For example, if you want to execute some
custom functionality every time Jekyll renders a post, you could register a
hook like this:
-->
Hook 은 이벤트 이름과 컨테이너에 등록됩니다. 등록하는 방법은,
Jekyll::Hooks.register 를 호출하고 컨테이너, 이벤트 이름과 Hook 이 실행될 때
호출할 코드를 연결하는 것입니다. 예를 들어, Jekyll 이 포스트를 렌더링할 때마다
특정 코드를 실행하도록 하려면, 다음과 같이 Hook 을 등록하면 됩니다:

```ruby
Jekyll::Hooks.register :posts, :post_render do |post|
  # code to call after Jekyll renders a post
end
```

<!--
Jekyll provides hooks for <code>:site</code>, <code>:pages</code>,
<code>:posts</code>, <code>:documents</code> and <code>:clean</code>. In all
cases, Jekyll calls your hooks with the container object as the first callback
parameter. All `:pre_render` hooks and the`:site, :post_render` hook will also
provide a payload hash as a second parameter. In the case of `:pre_render`, the
payload gives you full control over the variables that are available while
rendering. In the case of `:site, :post_render`, the payload contains final
values after rendering all the site (useful for sitemaps, feeds, etc).
-->
Jekyll 은 <code>:site</code> 와 <code>:pages</code>, <code>:posts</code> 와
<code>:documents</code>, <code>:clean</code> 에 관련된 Hook 을 제공합니다. 어떤 상황에서든, Jekyll 은
컨테이너 객체를 첫 번째 매개변수로 사용해 당신의 Hook 을 호출합니다.
모든 `:pre_render` 와 `:site`, `:post_render` Hook 은 두 번째 매개변수로
페이로드 해시 또한 전달합니다. `:pre_render` 의 경우, 페이로드 해시는
렌더링 중 사용할 수 있는 변수들에 대한 완전한 권한을 제공합니다.
`:site`, `:post_render` 의 경우, 페이로드에는 전체 사이트 렌더링이 끝난 후의
최종 값을 가지고 있다 (사이트맵이나 피드 등에 유용하다).

<!--
The complete list of available hooks is below:
-->
사용 가능한 Hook 들의 전체 목록은 다음과 같습니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Container</th>
      <th>Event</th>
      <th>Called</th>
-->
      <th>컨테이너</th>
      <th>이벤트</th>
      <th>호출 시점</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:after_init</code></p>
      </td>
      <td>
<!--
        <p>Just after the site initializes, but before setup & render. Good
        for modifying the configuration of the site.</p>
-->
        <p>사이트 초기화 직후, 환경설정과 렌더링 작업 전. 사이트 환경설정을
        조정하기에 적절한 시점이다.</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:after_reset</code></p>
      </td>
      <td>
<!--
        <p>Just after site reset</p>
-->
        <p>사이트가 초기화된 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_read</code></p>
      </td>
      <td>
<!--
        <p>After site data has been read and loaded from disk</p>
-->
        <p>디스크로부터 사이트 데이터를 읽어들인 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering the whole site</p>
-->
        <p>전체 사이트를 렌더링하기 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering the whole site, but before writing any files</p>
-->
        <p>전체 사이트를 렌더링한 직후 (파일 생성 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:site</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing the whole site to disk</p>
-->
        <p>전체 사이트 파일을 디스크에 생성한 직후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a page is initialized</p>
-->
        <p>페이지가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a page</p>
-->
        <p>페이지 렌더링 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a page, but before writing it to disk</p>
-->
        <p>페이지 렌더링 직후 (디스크에 생성 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:pages</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a page to disk</p>
-->
        <p>페이지를 디스크에 생성한 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a post is initialized</p>
-->
        <p>포스트가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a post</p>
-->
        <p>포스트를 렌더링하기 직전</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a post, but before writing it to disk</p>
-->
        <p>포스트 렌더링 후 (디스크에 쓰기 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:posts</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a post to disk</p>
-->
        <p>포스트를 디스크에 생성한 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_init</code></p>
      </td>
      <td>
<!--
        <p>Whenever a document is initialized</p>
-->
        <p>문서가 초기화될 때마다</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:pre_render</code></p>
      </td>
      <td>
<!--
        <p>Just before rendering a document</p>
-->
        <p>문서 렌더링 직후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_render</code></p>
      </td>
      <td>
<!--
        <p>After rendering a document, but before writing it to disk</p>
-->
        <p>문서를 렌더링한 후 (디스크에 쓰기 전)</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:documents</code></p>
      </td>
      <td>
        <p><code>:post_write</code></p>
      </td>
      <td>
<!--
        <p>After writing a document to disk</p>
-->
        <p>문서를 디스크에 생성한 후</p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>:clean</code></p>
      </td>
      <td>
        <p><code>:on_obsolete</code></p>
      </td>
      <td>
<!--
        <p>During the cleanup of a site's destination before it is built</p>
-->
        <p>사이트 생성 전 Destination 삭제 도중</p>
      </td>
    </tr>
  </tbody>
</table>
</div>
