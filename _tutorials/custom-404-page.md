---
layout: tutorials
permalink: /tutorials/custom-404-page/
#title: Custom 404 Page
title: 커스텀 404 페이지
---

<!--
You can easily serve custom 404 error pages with Jekyll to replace the default **Error 404 -- File Not Found** page displayed when one tries to access a broken link on your site.
-->
누군가 잘못된 링크를 사용해 당신의 사이트에 접근했을 때 표시되는 기본 **Error 404 -- File Not Found** 페이지를 커스터마이즈하는것은 아주 간단합니다.


<!--
## On GitHub Pages
-->
## GitHub Pages 의 경우 {#on-github-pages}

<!--
Any `404.html` at the **root of your `_site` directory** will be served automatically by GitHub Pages and the local WEBrick development server.
-->
GitHub Pages 와 로컬 WEBrick 개발 서버는 **`_site` 의 루트 디렉토리**에 있는 `404.html` 파일을 자동으로 사용합니다.

<!--
Simply add a `404.md` or `404.html` at the root of your site's source directory and include the YAML Front Matter data to use the theme's base layout.
-->
단순히 사이트의 Site Source 의 루트 디렉토리에 `404.md` 또는 `404.html` 을 추가하고 파일의 YAML 머리말에서 테마의 기본 레이아웃을 사용하도록 정의하면 됩니다.

<!--
If you plan to organize your files under subdirectories, the error page should have the following Front Matter Data, set: `permalink: /404.html`. This is to ensure that the compiled `404.html` resides at the root of your processed site, where it'll be picked by the server.
-->
다른 하위 디렉토리에 파일을 보관하려하는 경우에는, 에러 페이지의 머리말은 반드시 아래와 같이 정의되어야 합니다; `permalink: /404.html`. 이 설정으로 인해, 컴파일된 `404.html` 파일은 생성된 사이트의 루트 디렉토리에 저장되고, 서버가 사용할 수 있습니다.

<!--
```markdown
---
# example 404.md

layout: default
permalink: /404.html
---

# 404

Page not found! :(
```
-->
```markdown
---
# 404.md 예제

layout: default
permalink: /404.html
---

# 404

페이지를 찾을 수 없습니다! :(
```

<!--
## Hosting on Apache Web Servers
-->
## Apache Web Server 에 호스팅하기 {#hosting-on-apache-web-servers}

<!--
Apache Web Servers load a configuration file named [`.htaccess`](http://www.htaccess-guide.com/) that modifies the functionality of these servers.
-->
Apache Web Server 의 기능을 조정하는 환경설정 파일 이름은 [`.htaccess`](http://www.htaccess-guide.com/) 입니다.

<!--
Simply add the following to your `.htaccess` file.
-->
그냥 아래 내용을 `.htaccess` 파일에 추가하면 됩니다.

```apache
ErrorDocument 404 /404.html
```

<!--
With an `.htaccess` file, you have the freedom to place your error page within a subdirectory.
-->
이 `.htaccess` 파일 덕분에, 에러 페이지를 하위 디렉토리 어디에든 자유롭게 관리할 수 있습니다.

```apache
ErrorDocument 404 /error_pages/404.html
```

<!--
Where the path is relative to your site's domain.
-->
경로는 당신의 사이트 도메인에 대한 상대경로입니다.

<!--
More info on configuring Apache Error Pages can found in [official documentation](https://httpd.apache.org/docs/current/mod/core.html#errordocument).
-->
Apache 에러 페이지 환경설정에 대한 추가 정보는 [공식 문서](https://httpd.apache.org/docs/current/mod/core.html#errordocument)에서 얻을 수 있습니다.



<!--
## Hosting on Nginx server
-->
## Nginx 에 호스팅하기 {#hosting-on-nginx-server}

<!--
The procedure is just as simple as configuring Apache servers, but slightly different.
-->
방법은 Apache Server 환경설정 방법처럼 간단한데, 약간 다를 뿐입니다.

<!--
Add the following to the nginx configuration file, `nginx.conf`, which is usually located inside `/etc/nginx/` or `/etc/nginx/conf/`:
-->
아래의 내용을 Nginx 환경설정 파일 `nginx.conf` 에 추가하는데, 이 파일은 보통 `/etc/nginx/` 또는 `/etc/nginx/conf/` 에 있습니다:

```nginx
server {
  error_page 404 /404.html;
  location = /404.html {
    internal;
  }
}
```

<!--
The `location` directive prevents users from directly browsing the 404.html page.
-->
이 `location` 지시자는 사용자가 직접 404.html 페이지에 접근하는것을 방지합니다.
