---
layout: docs
title: 게시 방법
prev_section: github-pages
next_section: continuous-integration
permalink: /docs/deployment-methods/
---

Jekyll 로 생성한 사이트는, 정적이라는 근본적인 특징 덕분에 아주 다양한 방법으로 게시할 수 있습니다. 그 중 가장 일반적인 게시 방법 몇 가지를 소개합니다.

## 웹 호스팅 제공자 (FTP)

거의 모든 웹 호스팅 제공자들이 FTP 로 서버에 파일을 업로드하는 것을 허용합니다. FTP 를 사용해서 웹 호스트 서버에 Jekyll 사이트를 업로드하려면, 그냥 `jekyll` 명령을 실행 한 뒤에 생성된 `_site` 폴더를 호스팅 계정의 루트 폴더에 복사하면 됩니다. 보통 이 경로는 `httpdocs` 또는 `public_html` 폴더입니다.

### Glynn 을 사용한 FTP

[Glynn](https://github.com/dmathieu/glynn) 이라는 프로젝트가 있는데, Jekyll 로 정적인 웹 사이트 파일들을 생성하고
FTP 로 자신의 호스트에 전송하는 것을 편리하게 만들어주는 프로젝트입니다.

## 직접 관리하는 웹 서버

게시할 웹 서버에 직접 접속할 권한이 있는 경우, 파일을 옮기는 방법에 몇 가지 다른 선택사항(`scp` 또는 파일 시스템에 직접 접근)이 생기지만, 근본적으로는 동일합니다. 생성된 `_site` 폴더 내용을 웹 서버 내의 적절한 위치에 넣어야 한다는 것만 기억하세요.

## 자동적인 방법

Jekyll 사이트 게시를 쉽게 자동화하는 방법이 여러가지 있습니다. 아래 설명된 방법 외에 다른 방법을 알고 있다면, 그 편리함을 다른이들도 이용할 수 있도록 [기여](../contributing/)에 참여해주시기 바랍니다.

### Git 의 post-update 훅

만약 [Git](http://git-scm.com/) 을 사용해서 Jekyll 사이트를 관리하고 있다면
(버전 관리 시스템 사용하고 있죠? 그렇죠?),
[여기](http://web.archive.org/web/20091223025644/http://www.taknado.com/en/2009/03/26/deploying-a-jekyll-generated-site/)처럼
Git 저장소에 post-update 훅을 설정하여 게시를 쉽게 자동화 할 수 있습니다.

### Git 의 post-receive 훅

Git 으로 변경사항을 푸쉬할 때마다 자동으로 게시 작업을 수행하는 원격 서버를 구성하려면, 일단 새 계정을 만들어 게시작업 인증에 사용되는 공개키를 `authorized_keys` 파일에 모두 등록합니다. 다음, 아래와 같이 post-receive 훅을 설정합니다:

{% highlight bash %}
laptop$ ssh deployer@example.com
server$ mkdir myrepo.git
server$ cd myrepo.git
server$ git --bare init
server$ cp hooks/post-receive.sample hooks/post-receive
server$ mkdir /var/www/myrepo
{% endhighlight %}

그 다음, 서버에 Jekyll 을 설치하고 hooks/post-receive 에 아래와 같이 코드를
추가합니다:

{% highlight bash %}
GIT_REPO=$HOME/myrepo.git
TMP_GIT_CLONE=$HOME/tmp/myrepo
PUBLIC_WWW=/var/www/myrepo

git clone $GIT_REPO $TMP_GIT_CLONE
jekyll build -s $TMP_GIT_CLONE -d $PUBLIC_WWW
rm -Rf $TMP_GIT_CLONE
exit
{% endhighlight %}

마지막으로, 사용자의 PC 에서 다음 명령을 실행하여 이 훅을 사용할 수 있도록
설정합니다:

{% highlight bash %}
laptops$ git remote add deploy deployer@example.com:~/myrepo.git
{% endhighlight %}

이제 Apache 나 nginx 가 `/var/www/myrepo` 를 바라보도록 설정하고 다음 명령을
실행하기만 하면 게시됩니다:

{% highlight bash %}
laptops$ git push deploy master
{% endhighlight %}

### Jekyll-hook

또한 jekyll-hook 서버를 사용해서, GitHub 으로부터 webhook 포스트를 기다리다가,
Jekyll 로 웹사이트를 생성해서, 게시될 곳으로 옮길 수 있습니다. 이것으로 자신만의
GitHub Pages 스타일 웹 서버를 구축해보세요.

이것은 방화벽 안쪽에 웹사이트를 구축해야할 필요가 있거나 HTTP 기본 인증같은
서버-레벨의 부가기능이 필요하거나 S3 같은 파일호스트나 CDN 에 직접 사이트를
호스팅하고 싶을 때 유용한 방법입니다.

설정 방법에 대한 전체 문서는 [`jekyll-hook`
저장소](https://github.com/developmentseed/jekyll-hook)에 있습니다.

### Rake

Jekyll 사이트를 게시하는 또 다른 방법은 [Rake](https://github.com/jimweirich/rake) 와 [HighLine](https://github.com/JEG2/highline),
[Net::SSH](https://github.com/net-ssh/net-ssh) 를 사용하는 것입니다. Rake 를 사용하여 여러 브랜치를 처리할 수 있는 복합적인 Jekyll 게시 예제는 [Git Ready](https://github.com/gitready/gitready/blob/cdfbc4ec5321ff8d18c3ce936e9c749dbbc4f190/Rakefile) 에서 찾을 수 있습니다.

### rsync

일단 `_site` 디렉토리를 생성하고 난 뒤에는, 이 [게시용 스크립트](https://github.com/henrik/henrik.nyh.se/blob/master/tasks/deploy)와 유사한 쉘 스크립트 `tasks/deploy` 를 사용하여 쉽게 rsync 할 수 있습니다. 물론 자신의 사이트 정보에 맞게 일부를 수정해서 사용해야 합니다.
또한, Textmate 에서 이 스크립트를 실행할 수 있게 해주는 [TextMate 명령어](http://gist.github.com/214959)도 있습니다.


## Rack-Jekyll

[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) 은 Amazon EC2 나 Slicehost, Heroku 등의 Rack 서버에 쉽게 게시할 수 있는 방법을 제공합니다. [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/) 이나 [그 밖에 다른 것들](https://github.com/adaoraul/rack-jekyll#readme)과 함께 사용할 수 있습니다.

Rack-Jekyll 을 사용하여 Heroku 에 게시하는 방법을 설명한 [이 포스트](http://blog.crowdint.com/2010/08/02/instant-blog-using-jekyll-and-heroku.html)를 읽어보세요.

## Rails 를 위한 Jekyll-Admin

[Jekyll-Admin](https://github.com/zkarpinski/Jekyll-Admin) 을 사용하면, 자신의 Rails 응용프로그램 내에서 Jekyll 을 관리할 수 있습니다. 더 자세한 내용은 Jekyll-Admin 의 [README](https://github.com/zkarpinski/Jekyll-Admin/blob/master/README) 를 읽어보세요.

## Amazon S3

만약 Amazon S3 에 사이트를 호스팅하고 싶다면,
[s3_website](https://github.com/laurilehmijoki/s3_website) 라는 응용프로그램을
사용하세요.
유동적으로 거의 무한대의 트래픽까지 규모가 조정되는 Amazon S3 에 당신의 사이트를
서비스 해줍니다. 사용하는 만큼에 대해서만 지불하기 때문에 소규모 블로그에는 이
방법을 적용하는 것이 가장 저렴할 것입니다.

## OpenShift

만약 OpenShift gear 에 사이트를 게시하고 싶다면, [이를 위한
카트리지](https://github.com/openshift-cartridges/openshift-jekyll-cartridge)도 있습니다.

<div class="note">
  <h5>ProTip™: GitHub Pages 로 귀찮은 일 없이 Jekyll 을 호스팅하세요</h5>
  <p>GitHub Pages 는 내부적으로 Jekyll 을 사용합니다. GitHub Pages 는 <a href="../github-pages/">Jekyll 웹사이트를 호스팅</a>하는 최고의 방법으로, 귀찮은 일도 없고 비용도 들지 않습니다.</p>
</div>
