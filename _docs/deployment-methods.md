---
layout: docs
title: 게시 방법
permalink: /docs/deployment-methods/
---

Jekyll 로 생성한 사이트는, 정적이라는 그 근본적인 특징 덕분에 아주 다양한 방법으로 게시할 수 있습니다. 이 중 가장 자주 사용하는 게시 방법 몇 가지를 여기에 소개합니다.

## 웹 호스팅 제공자 (FTP)

거의 모든 웹 호스팅 제공자들이 FTP 로 서버에 파일을 업로드하는 것을 허용합니다. FTP 를 이용해서 Jekyll 사이트를 웹 호스트 서버에 업로드하는 방법은, 단지 `jekyll` 명령을 실행 한 뒤에 생성된 `_site` 폴더를 호스팅 계정의 루트 폴더에 복사하는 것입니다. 대부분의 경우 이 루트 폴더의 이름은 `httpdocs` 나 `public_html` 입니다.

### Glynn 을 사용한 FTP

[Glynn](https://github.com/dmathieu/glynn) 이라는 프로젝트가 있는데, Jekyll 로 웹 사이트 파일들을 생성한 후 FTP 로 호스트에 전송하는 작업을 쉽게
도와주는 프로젝트입니다.

## 직접 관리하는 웹 서버

게시할 웹 서버에 직접 접속할 권한이 있다면, 해야할 작업 내용은 근본적으로 동일하지만, 파일을 옮기는 방법에 몇 가지 다른 선택사항 (`scp` 또는 파일 시스템에 직접 접근) 이 생깁니다. 생성된 `_site` 폴더 내용을 옮길 때 반드시 웹 서버의 올바른 웹 루트 디렉토리에 저장해야 한다는 것만 기업하면 됩니다.

## 자동적인 방법

쉽게 Jekyll 사이트 게시를 자동화해주는 방법들도 많이 있습니다. 아래 설명되지 않은 다른 방법을 알고 있다면, 다른 이들도 그 편리함을 누릴 수 있도록 [기여](../contributing/)해주시기 바랍니다.

### Git 의 post-update 훅

만약 [Git](http://git-scm.com/) 을 사용해서 Jekyll 사이트를 관리하고 있다면
(버전 관리 시스템 사용하고 있죠? 그렇죠?),
[이것](http://web.archive.org/web/20091223025644/http://www.taknado.com/en/2009/03/26/deploying-a-jekyll-generated-site/)처럼
Git 저장소에 post-update 훅을 설정하여 쉽게 게시를 자동화 할 수 있습니다.

### Git 의 post-receive 훅

Git 으로 변경사항을 푸쉬할 때마다 원격 서버가 자동으로 게시 작업을 수행하도록 구성하려면, 일단 새 계정을 만들어 `authorized_keys` 파일에 게시작업 인증 시 사용되는 공개키를 모두 등록합니다. 그 다음, 아래와 같이 post-receive 훅을 설정합니다:

{% highlight bash %}
laptop$ ssh deployer@example.com
server$ mkdir myrepo.git
server$ cd myrepo.git
server$ git --bare init
server$ cp hooks/post-receive.sample hooks/post-receive
server$ mkdir /var/www/myrepo
{% endhighlight %}

이제, 서버에 Jekyll 을 설치하고 hooks/post-receive 에 아래와 같이 코드를
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

### Static Publisher

GitHub 과 연관성은 없지만, Webhook 포스트를 감시하는 서버를 사용한 [Static Publisher](https://github.com/static-publisher/static-publisher) 라는 게시방법도 있습니다. 한 번의 클릭으로 Heroku 에 게시가 가능하고, 한 서버에서 여러 프로젝트를 감시할 수 있으며, 직관적인 관리자 인터페이스를 가지고 있고 S3 와 git 저장소 (예, gh-pages) 에 게시할 수 있습니다.

### Rake

Jekyll 사이트를 게시하는 또 다른 방법은 [Rake](https://github.com/jimweirich/rake) 와 [HighLine](https://github.com/JEG2/highline),
[Net::SSH](https://github.com/net-ssh/net-ssh) 를 사용하는 것입니다. Rake 를 사용하여 여러 브랜치를 처리하는, 좀 더 복잡한 Jekyll 게시 예제를 [Git Ready](https://github.com/gitready/gitready/blob/cdfbc4ec5321ff8d18c3ce936e9c749dbbc4f190/Rakefile) 에서 찾을 수 있습니다.


### scp

`_site` 디렉토리 생성이 끝나면, [이 게시용 스크립트](https://github.com/henrik/henrik.nyh.se/blob/master/script/deploy)와 유사한 쉘 스크립트인 `tasks/deploy` 를 사용하여 scp 를 쉽게 할 수 있습니다. 물론 자신의 사이트에 맞게 일부는 수정해서 사용해야 합니다. 게다가 이 스크립트를 Textmate 에서 실행할 수 있게 해주는 [Textmate 명령어](http://gist.github.com/214959)도 있습니다.

### rsync

`_site` 디렉토리 생성이 끝나면, [이 게시용 스크립트](https://github.com/vitalyrepin/vrepinblog/blob/master/transfer.sh)와 유사한 쉘 스크립트인 `tasks/deploy` 를 사용하여 rsync 를 쉽게 할 수 있습니다. 물론 자신의 사이트에 맞게 일부는 수정해서 사용해야 합니다.

#### 1 단계: 홈 폴더에 rrsync 설치 (서버-사이드)

게시 작업을 단순하게 만들기 위해서 인증서를 사용해서 인증 작업을 합니다. 이는 rsync 가 동기화를 해야하는 디렉토리에만 접근 권한을 가질 수 있게 하기 때문에 당연히 필요한 절차입니다.

그렇게 때문에 rrsync wrapper 를 설치해야 하는 것입니다. 호스트에 설치되어 있지 않다면 자신이 직접 설치할 수 있습니다:

- [rrsync 를 다운로드 한다](http://ftp.samba.org/pub/unpacked/rsync/support/rrsync)
- 홈 폴더의 bin 디렉토리에 저장한다 (```~/bin```)
- 실행 권한을 부여한다 (```chmod +x```)

#### 2 단계: 인증서-기반 ssh 접속 설정 (서버 사이드)

[인터넷 상에 이 설정 방법에 대한 글이 많이 있습니다](https://wiki.gentoo.org/wiki/SSH#Passwordless_Authentication). 여기선 설명하지 않겠습니다. 유일한 차이점이라면 인증서-기반 인증을 ```~/.ssh/authorized_keys``` 에 제한한다는 것입니다). ```rrsync``` 유틸리티를 실행하고 읽기-쓰기 권한을 가질 폴더를 지정합니다:

```
command="$HOME/bin/rrsync <folder>",no-agent-forwarding,no-port-forwarding,no-pty,no-user-rc,no-X11-forwarding ssh-rsa <cert>
```

```<folder>``` 는 자신의 사이트 경로입니다. 예, ```~/public_html/you.org/blog-html/```.

#### 3 단계: Rsync! (클라이언트 사이드)

웹 사이트 소스 디렉토리에 ```deploy``` 스크립트를 추가합니다:

{% highlight bash %}
#!/bin/sh

rsync -avr --rsh='ssh -p2222' --delete-after --delete-excluded   <folder> <user>@<site>:
{% endhighlight %}

아래는 전달인자 목록입니다:

- ```--rsh='ssh -p2222'``` 는 SSH 접근을 위해 호스트가 제공하는 SSH 포트 번호가 기본값이 아닌 다른 번호일 경우 필요합니다 (예, hostgator 가 이런 방식을 사용합니다)
- ```<folder>``` 는 생성된 웹 컨텐츠가 있는 로컬 디렉토리 이름입니다. Jekyll 에서 기본값은 ```_site/``` 입니다
- ```<user>``` &mdash; 호스트에 접속하는 ssh 계정 사용자 이름
- ```<site>``` &mdash; 호스트 서버

예시는 다음과 같습니다:

{% highlight bash %}
rsync -avr --rsh='ssh -p2222' --delete-after --delete-excluded   _site/ hostuser@vrepin.org:
{% endhighlight %}

서버명 뒤에 ':' 를 잊지 마세요!

#### 4 단계 (선택사항): transfer.sh 가 Jekyll 의 Site Destination 에 복사되지 않도록 제외시키기

Jekyll-기반 웹 사이트에 게시하는 경우에는 이 단계를 따르길 권장합니다. 프로젝트 루트 디렉토리에 ```deploy``` 스크립트를 넣어두면, Jekyll 은 이 파일을 Site Destination 에 복사할 것입니다.
```_config.yml``` 을 수정해서 이를 바꿀 수 있습니다. 다음 코드를 추가합니다:

{% highlight yaml %}
# 이 파일들은 출력 디렉토리에 복사하지 않는다
exclude: ["deploy"]
{% endhighlight %}

#### 끝났습니다!

이제 ```deploy``` 스크립트를 실행해서 웹 사이트를 게시할 수 있습니다. ssh 인증서에  [패스프레이즈-보안](https://martin.kleppmann.com/2013/05/24/improving-security-of-ssh-private-keys.html)이 설정되어 있으면, 비밀번호를 입력해야 합니다.

## Rack-Jekyll

[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) 은 Amazon EC2 나 Slicehost, Heroku 등의 Rack 서버에 쉽게 게시할 수 있는 방법을 제공합니다. [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/) 이나 [그 밖에 다른 것들](https://github.com/adaoraul/rack-jekyll#readme)과 함께 사용할 수 있습니다.

Rack-Jekyll 을 사용하여 Heroku 에 게시하는 방법을 설명한 [이 포스트](http://blog.crowdint.com/2010/08/02/instant-blog-using-jekyll-and-heroku.html)를 읽어보세요.

## Rails 를 위한 Jekyll-Admin

[Jekyll-Admin](https://github.com/zkarpinski/Jekyll-Admin) 을 사용하면, 자신의 Rails 응용프로그램 내에서 Jekyll 을 관리할 수 있습니다. 더 자세한 내용은 Jekyll-Admin 의 [README](https://github.com/zkarpinski/Jekyll-Admin/blob/master/README) 를 읽어보세요.

## Amazon S3

만약 Amazon S3 에 사이트를 호스팅하고 싶다면,
[s3_website](https://github.com/laurilehmijoki/s3_website) 라는 응용프로그램을
사용하세요. 이 응용프로그램은 거의 무한대의 트래픽까지 유동적으로 규모가
조정되면서,
다른 웹 서버들처럼 서비스되는 Amazon S3 에 당신의 사이트를 업로드 해줍니다.
사용하는 만큼에 대해서만 비용을 지불하기 때문에 소규모 블로그에는 이 방법을
적용하는 것이 가장 저렴할 것입니다.

## OpenShift

만약 OpenShift gear 에 사이트를 게시하고자 한다면, [이를 위한
카트리지](https://github.com/openshift-cartridges/openshift-jekyll-cartridge)를 사용해 보세요.

<div class="note">
  <h5>ProTip™: GitHub Pages 로 귀찮은 일 없이 Jekyll 을 호스팅하세요</h5>
  <p>GitHub Pages 는 내부적으로 Jekyll 을 사용합니다. GitHub Pages 는 <a href="../github-pages/">Jekyll 웹사이트를 호스팅</a>하는 최고의 방법으로써, 귀찮은 일도 없고 비용도 들지 않습니다.</p>
</div>
