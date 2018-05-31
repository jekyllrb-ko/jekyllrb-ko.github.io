---
#title: Deployment methods
title: 게시 방법
permalink: /docs/deployment-methods/
---

<!--
Sites built using Jekyll can be deployed in a large number of ways due to the static nature of the generated output. A few of the most common deployment techniques are described below.
-->
Jekyll 로 생성한 사이트는, 정적이라는 그 근본적인 특징 덕분에 아주 다양한 방법으로 게시할 수 있습니다. 이 중 가장 자주 사용하는 게시 방법 몇 가지를 여기에 소개합니다.

<div class="note">
<!--
  <h5>ProTip™: Use GitHub Pages for zero-hassle Jekyll hosting</h5>
  <p>GitHub Pages are powered by Jekyll behind the scenes, so if you’re looking for a zero-hassle, zero-cost solution, GitHub Pages are a great way to <a href="../github-pages/">host your Jekyll-powered website for free</a>.</p>
-->
  <h5>ProTip™: 번거로운 일 없이 GitHub Pages 로 Jekyll 사이트 호스팅하기</h5>
  <p>GitHub Pages 의 내부는 Jekyll 로 동작합니다. 따라서 번거로운 작업이나 시간과 노력이 들지 않는 방법이라면, GitHub Pages 가 <a href="../github-pages/">Jekyll 기반의 웹사이트를 무료로 호스팅</a>하는 최선의 방법입니다.</p>
</div>

## Netlify

<!--
Netlify provides Global CDN, Continuous Deployment, one click HTTPS and [much more](https://www.netlify.com/features/), providing developers the most robust toolset available for modern web projects, without added complexity. Netlify supports custom plugins for Jekyll and has a free plan for open source projects.
-->
Netlify 는 범세계적인 CDN 과 지속적인 서비스, 손쉬운 HTTPS 설정과 [그 밖의 많은 기능](https://www.netlify.com/features/)으로, 개발자들에게 현대식 웹 프로젝트에 사용할 수 있는 가장 강력한, 하지만 복잡하지 않은, 도구를 제공합니다.

<!--
Read this [Jekyll step-by-step guide](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/) to setup your Jekyll site on Netlify.
-->
Netlify 에 Jekyll 사이트를 구성하려면 [단계적 Jekyll 설정방법](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/)을 읽어보세요.

## Aerobatic

<!--
[Aerobatic](https://www.aerobatic.com) has custom domains, global CDN distribution, basic auth, CORS proxying, and a growing list of plugins all included.
-->
[Aerobatic](https://www.aerobatic.com) 은 커스텀 도메인, 범세계적 CDN, 기본 인증, CORS 프록시를 제공하고, 점점 더 많은 플러그인을 지원하고 있습니다.

<!--
Automating the deployment of a Jekyll site is simple. See their [Jekyll docs](https://www.aerobatic.com/docs/static-site-generators/#jekyll) for more details. Your built `_site` folder is deployed to their highly-available, globally distributed hosting service.
-->
간단히 Jekyll 사이트 게시를 자동화할 수 있습니다. 더 자세한 내용은 [Jekyll 관련 문서](https://www.aerobatic.com/docs/static-site-generators/#jekyll)를 참고하세요. 중단 없는, 전세계적인 그들의 호스팅 서버에 당신이 생성한 `_site` 를 게시할 수 있습니다. 

## Kickster

<!--
Use [Kickster](http://kickster.nielsenramon.com/) for easy (automated) deploys to GitHub Pages when using unsupported plugins on GitHub Pages.
-->
[Kickster](http://kickster.nielsenramon.com/) 를 사용하면 GitHub Pages 에서 지원하지 않는 플러그인을 사용하는 경우에도 쉽게 (자동으로) GitHub Pages 에 게시할 수 있습니다.

<!--
Kickster provides a basic Jekyll project setup packed with web best practises and useful optimization tools increasing your overall project quality. Kickster ships with automated and worry-free deployment scripts for GitHub Pages.
-->
Kickster 가 제공하는 기본 Jekyll 프로젝트의 기본설정은 아주 모범적이며 프로젝트의 전반적인 질을 향상시키는데 유용한 최적화 도구도 포함되어 있습니다. Kickster 는 아무 걱정없이 사용할 수 있는 자동화된 GiHub Pages 용 배포 스크립트를 제공합니다.

<!--
Setting up Kickster is very easy, just install the gem and you are good to go. More documentation can here found [here](https://github.com/nielsenramon/kickster#kickster). If you do not want to use the gem or start a new project you can just copy paste the deployment scripts for [Travis CI](https://github.com/nielsenramon/kickster/tree/master/snippets/travis) or [Circle CI](https://github.com/nielsenramon/kickster#automated-deployment-with-circle-ci).
-->
Kickster 설정은 관련 gem 을 설치하는 것이 전부라서 아주 간단합니다. 관련 문서는 [여기](https://github.com/nielsenramon/kickster#kickster)서 찾을 수 있습니다. 만약 관련 gem 을 설치하거나 새 프로젝트를 만들고 싶지 않다면 [Travis CI](https://github.com/nielsenramon/kickster/tree/master/snippets/travis) 나 [Circle CI](https://github.com/nielsenramon/kickster#automated-deployment-with-circle-ci) 용 배포 스크립트만 복사해 사용할 수 있습니다.

<!--
## Web hosting providers (FTP)
-->
## 웹 호스팅 제공자 (FTP)

<!--
Just about any traditional web hosting provider will let you upload files to their servers over FTP. To upload a Jekyll site to a web host using FTP, simply run the `jekyll build` command and copy the contents of the generated `_site` folder to the root folder of your hosting account. This is most likely to be the `httpdocs` or `public_html` folder on most hosting providers.
-->
거의 모든 웹 호스팅 제공자들이 FTP 로 서버에 파일을 업로드하는 것을 허용합니다. FTP 를 이용해서 Jekyll 사이트를 웹 호스트 서버에 업로드하는 방법은, 단지 `jekyll build` 명령을 실행 한 뒤에 생성된 `_site` 폴더의 내용을 호스팅 계정의 루트 폴더에 복사하는 것입니다. 대부분의 경우 이 루트 폴더의 이름은 `httpdocs` 나 `public_html` 입니다.

<!--
## Self-managed web server
-->
## 직접 관리하는 웹 서버

<!--
If you have direct access to the deployment web server, the process is essentially the same, except you might have other methods available to you (such as `scp`, or even direct filesystem access) for transferring the files. Just remember to make sure the contents of the generated `_site` folder get placed in the appropriate web root directory for your web server.
-->
게시할 웹 서버에 접속할 권한이 있다면, 해야할 작업 내용은 근본적으로 동일하지만, 파일을 옮기는 방법에 몇 가지 다른 선택사항 (`scp` 또는 파일 시스템에 직접 접근) 이 생깁니다. 생성된 `_site` 폴더 내용을 옮길 때 반드시 웹 서버의 올바른 웹 루트 디렉토리에 저장해야 한다는 것만 기억하면 됩니다.

<!--
## Automated methods
-->
## 자동화 방법

<!--
There are also a number of ways to easily automate the deployment of a Jekyll site. If you’ve got another method that isn’t listed below, we’d love it if you [contributed](../contributing/) so that everyone else can benefit too.
-->
쉽게 Jekyll 사이트 게시를 자동화해주는 방법들도 많이 있습니다. 아래 설명되지 않은 다른 방법을 알고 있다면, 다른 이들도 그 편리함을 누릴 수 있도록 [기여](../contributing/)해주시기 바랍니다.

<!--
### Git post-update hook
-->
### Git 의 post-update 훅

<!--
If you store your Jekyll site in [Git](https://git-scm.com/) (you are using
version control, right?), it’s pretty easy to automate the
deployment process by setting up a post-update hook in your Git
repository, [like
this](http://web.archive.org/web/20091223025644/http://www.taknado.com/en/2009/03/26/deploying-a-jekyll-generated-site/).
-->
만약 [Git](https://git-scm.com/) 을 사용해서 Jekyll 사이트를 관리하고
있다면 (버전 관리 시스템 사용하고 있죠? 그렇죠?),
[이것](http://web.archive.org/web/20091223025644/http://www.taknado.com/en/2009/03/26/deploying-a-jekyll-generated-site/)처럼
Git 저장소에 post-update 훅을 설정하여 쉽게 게시를 자동화할 수
있습니다.

<!--
### Git post-receive hook
-->
### Git 의 post-receive 훅

<!--
To have a remote server handle the deploy for you every time you push changes using Git, you can create a user account which has all the public keys that are authorized to deploy in its `authorized_keys` file. With that in place, setting up the post-receive hook is done as follows:
-->
Git 으로 변경사항을 푸쉬할 때마다 원격 서버가 자동으로 게시 작업을 수행하도록 구성하려면, 일단 새 계정을 만들어 `authorized_keys` 파일에 게시작업 인증 시 사용되는 공개키를 모두 등록합니다. 그 다음, 아래와 같이 post-receive 훅을 설정합니다:

```sh
laptop$ ssh deployer@example.com
server$ mkdir myrepo.git
server$ cd myrepo.git
server$ git --bare init
server$ cp hooks/post-receive.sample hooks/post-receive
server$ mkdir /var/www/myrepo
```

<!--
Next, add the following lines to hooks/post-receive and be sure Jekyll is
installed on the server:
-->
이제, 서버에 Jekyll 을 설치하고 hooks/post-receive 에 아래와 같이 코드를
추가합니다:

```bash
GIT_REPO=$HOME/myrepo.git
TMP_GIT_CLONE=$HOME/tmp/myrepo
GEMFILE=$TMP_GIT_CLONE/Gemfile
PUBLIC_WWW=/var/www/myrepo

git clone $GIT_REPO $TMP_GIT_CLONE
BUNDLE_GEMFILE=$GEMFILE bundle install
BUNDLE_GEMFILE=$GEMFILE bundle exec jekyll build -s $TMP_GIT_CLONE -d $PUBLIC_WWW
rm -Rf $TMP_GIT_CLONE
exit
```

<!--
Finally, run the following command on any users laptop that needs to be able to
deploy using this hook:
-->
마지막으로, 사용자의 PC 에서 다음 명령을 실행하여 이 훅을 사용할 수 있도록
설정합니다:

```sh
laptops$ git remote add deploy deployer@example.com:~/myrepo.git
```

<!--
Deploying is now as easy as telling nginx or Apache to look at
`/var/www/myrepo` and running the following:
-->
이제 Apache 나 nginx 가 `/var/www/myrepo` 를 바라보도록 설정하고 다음 명령을
실행하기만 하면 게시됩니다:

```sh
laptops$ git push deploy master
```

### Static Publisher

<!--
[Static Publisher](https://github.com/static-publisher/static-publisher) is another automated deployment option with a server listening for webhook posts, though it's not tied to GitHub specifically. It has a one-click deploy to Heroku, it can watch multiple projects from one server, it has an easy to user admin interface and can publish to either S3 or to a git repository (e.g. gh-pages).
-->
GitHub 과 연관성은 없지만, Webhook 포스트를 감시하는 서버를 사용한 [Static Publisher](https://github.com/static-publisher/static-publisher) 라는 게시방법도 있습니다. 한 번의 클릭으로 Heroku 에 게시가 가능하고, 한 서버에서 여러 프로젝트를 감시할 수 있으며, 직관적인 관리자 인터페이스를 가지고 있고 S3 와 git 저장소 (예, gh-pages) 에 게시할 수 있습니다.

### Rake

<!--
Another way to deploy your Jekyll site is to use [Rake](https://github.com/ruby/rake), [HighLine](https://github.com/JEG2/highline), and
[Net::SSH](https://github.com/net-ssh/net-ssh). A more complex example of deploying Jekyll with Rake that deals with multiple branches can be found in [Git Ready](https://github.com/gitready/gitready/blob/cdfbc4ec5321ff8d18c3ce936e9c749dbbc4f190/Rakefile).
-->
Jekyll 사이트를 게시하는 또 다른 방법은 [Rake](https://github.com/ruby/rake) 와 [HighLine](https://github.com/JEG2/highline),
[Net::SSH](https://github.com/net-ssh/net-ssh) 를 사용하는 것입니다. Rake 를 사용하여 여러 브랜치를 처리하는, 좀 더 복잡한 Jekyll 게시 예제를 [Git Ready](https://github.com/gitready/gitready/blob/cdfbc4ec5321ff8d18c3ce936e9c749dbbc4f190/Rakefile) 에서 찾을 수 있습니다.


### scp

<!--
Once you’ve generated the `_site` directory, you can easily scp its content using a
`tasks/deploy` shell script similar to [this deploy script][]. You’d obviously
need to change the values to reflect your site’s details. There is even [a
matching TextMate command][] that will help you run this script.
-->
`_site` 디렉토리 생성이 끝나면, 이 [게시용 스크립트][this deploy script]와 유사한
쉘 스크립트인 `tasks/deploy` 를 사용하여 손쉽게 그 내용을 scp 로 복사할 수
있습니다. 물론 자신의 사이트에 맞게 일부는 수정해서 사용해야 합니다. 게다가 이
스크립트를 실행하는 [Textmate 명령어][a matching TextMate command]도 있습니다.

[this deploy script]: https://github.com/henrik/henrik.nyh.se/blob/master/script/deploy

[a matching TextMate command]: https://gist.github.com/henrik/214959

### rsync

<!--
Once you’ve generated the `_site` directory, you can easily rsync its content using a `tasks/deploy` shell script similar to [this deploy script here](https://github.com/vitalyrepin/vrepinblog/blob/master/transfer.sh). You’d obviously need to change the values to reflect your site’s details.
-->
`_site` 디렉토리 생성이 끝나면, 이 [게시용 스크립트](https://github.com/vitalyrepin/vrepinblog/blob/master/transfer.sh)와 유사한 쉘 스크립트인 `tasks/deploy` 를 사용하여 손쉽게 그 내용을 rsync 할 수 있습니다. 물론 자신의 사이트에 맞게 일부는 수정해서 사용해야 합니다.

<!--
Certificate-based authorization is another way to simplify the publishing
process. It makes sense to restrict rsync access only to the directory which it is supposed to sync. This can be done using rrsync.
-->
게시 작업을 편하게 만드는 또 다른 방법으로는 인증서 기반 인증이 있습니다.
rsync 가 접근할 필요가 있는 디렉토리에만 접근 권한을 허용하는 것이 합리적입니다. 이는 rrsync 를 사용하면 가능합니다.

<!--
#### Step 1: Install rrsync to your home folder (server-side)
-->
#### 1 단계: 홈 폴더에 rrsync 설치 (서버-사이드)

<!--
If it is not already installed by your host, you can do it yourself:
-->
호스트에 설치되어 있지 않다면, 직접 설치할 수도 있습니다:

<!--
- [Download rrsync](https://ftp.samba.org/pub/unpacked/rsync/support/rrsync)
- Place it in the `bin` subdirectory of your home folder  (`~/bin`)
- Make it executable (`chmod +x`)
-->
- [rrsync 다운로드](https://ftp.samba.org/pub/unpacked/rsync/support/rrsync)
- 자신의 홈 폴더의 하위 디렉토리 `bin` 에 옮긴다 (`~/bin`)
- 실행 권한을 부여한다 (`chmod +x`)

<!--
#### Step 2: Set up certificate-based SSH access (server side)
-->
#### 2 단계: 인증서-기반 SSH 접속 설정 (서버 사이드)

<!--
This [process](https://wiki.gentoo.org/wiki/SSH#Passwordless_Authentication) is
described in several places online. What is different from the typical approach
is to put the restriction to certificate-based authorization in
`~/.ssh/authorized_keys`. Then, launch `rrsync` and supply
it with the folder it shall have read-write access to:
-->
온라인 상에 이 [설정 방법](https://wiki.gentoo.org/wiki/SSH#Passwordless_Authentication)에
대한 글이 많이 있습니다. 유일한 차이점이라면
`~/.ssh/authorized_keys` 에 인증서 기반 인증으로 제한을 건다는
것입니다. 그 다음, `rrsync` 를 실행할 때 읽기-쓰기 권한을 가질 폴더를
지정합니다:

```sh
command="$HOME/bin/rrsync <folder>",no-agent-forwarding,no-port-forwarding,no-pty,no-user-rc,no-X11-forwarding ssh-rsa <cert>
```

<!--
`<folder>` is the path to your site. E.g., `~/public_html/you.org/blog-html/`.
-->
`<folder>` 는 자신의 사이트 경로입니다. 예, `~/public_html/you.org/blog-html/`.

<!--
#### Step 3: Rsync (client-side)
-->
#### 3 단계: Rsync (클라이언트 사이드)

<!--
Add the `deploy` script to the site source folder:
-->
사이트 소스 디렉토리에 `deploy` 스크립트를 추가합니다:

```sh
#!/bin/sh

rsync -crvz --rsh='ssh -p2222' --delete-after --delete-excluded   <folder> <user>@<site>:
```

<!--
Command line parameters are:
-->
아래는 전달인자 목록입니다:

<!--
- `--rsh=ssh -p2222` &mdash; The port for SSH access. It is required if
your host uses a different port than the default (e.g, HostGator)
- `<folder>` &mdash; The name of the local output folder (defaults to `_site`)
- `<user>` &mdash; The username for your hosting account
- `<site>` &mdash; Your hosting server
-->
- `--rsh=ssh -p2222` &mdash; SSH 접속에 사용할 포트. 호스트가 기본값이
아닌 다른 포트를 사용하는 경우 필요합니다 (예, HostGator)
- `<folder>` &mdash; 결과물이 저장되는 로컬 디렉토리 이름 (기본값 `_site`)
- `<user>` &mdash; 호스트에 접속하는 계정의 사용자 이름
- `<site>` &mdash; 호스트 서버

<!--
Using this setup, you might run the following command:
-->
이 전달인자들을 사용하는 명령어 예시입니다:

```sh
rsync -crvz --rsh='ssh -p2222' --delete-after --delete-excluded _site/ hostuser@example.org:
```

<!--
Don't forget the column `:` after server name!
-->
서버명 뒤에 `:` 를 잊지 마세요!

<!--
#### Step 4 (Optional): Exclude the transfer script from being copied to the output folder.
-->
#### 4 단계 (선택사항): 전송 스크립트가 Site Destination 에 복사되지 않도록 제외시키기

<!--
This step is recommended if you use these instructions to deploy your site. If
you put the `deploy` script in the root folder of your project, Jekyll will
copy it to the output folder. This behavior can be changed in `_config.yml`.
-->
웹 사이트를 게시할 때 위 절차대로 진행했다면 이 단계도 따르길 권합니다. 프로젝트
루트 디렉토리에 `deploy` 스크립트를 넣어두면, Jekyll 은 이 파일을 Site
Destination 에 복사할 것입니다. `_config.yml` 을 수정해서 이를 바꿀 수 있습니다.

<!--
Just add the following line:
-->
다음 코드를 추가합니다:

```yaml
# Do not copy these files to the output directory
exclude: ["deploy"]
```

<!--
Alternatively, you can use an `rsync-exclude.txt` file to control which files will be transferred to your server.
-->
아니면, `rsync-exclude.txt` 파일을 사용해서 서버에 전송될 파일을 관리할 수 있습니다.

<!--
#### Done!
-->
#### 끝났습니다!

<!--
Now it's possible to publish your website simply by running the `deploy`
script. If your SSH certificate  is [passphrase-protected](https://martin.kleppmann.com/2013/05/24/improving-security-of-ssh-private-keys.html), you will be asked to enter it when the
script executes.
-->
이제 단순히 `deploy` 스크립트를 실행하는 것만으로 웹사이트를 게시할 수
있습니다. SSH 인증서에  [패스프레이즈-보안](https://martin.kleppmann.com/2013/05/24/improving-security-of-ssh-private-keys.html)이 설정되어 있으면,
스크립트를 실행할 때 패스프레이즈를 입력해야 합니다.

## Rack-Jekyll

<!--
[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) is an easy way to deploy your site on any Rack server such as Amazon EC2, Slicehost, Heroku, and so forth. It also can run with [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/), and [others](https://github.com/adaoraul/rack-jekyll#readme).
-->
[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) 은 Amazon EC2 나 Slicehost, Heroku 등의 Rack 서버에 쉽게 게시할 수 있는 방법을 제공합니다. [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/) 이나 [그 밖에 다른 것들](https://github.com/adaoraul/rack-jekyll#readme)과 함께 사용할 수 있습니다.

<!--
Read [this post](http://andycroll.com/ruby/serving-a-jekyll-blog-using-heroku/) on how to deploy to Heroku using Rack-Jekyll.
-->
[이 포스트](http://andycroll.com/ruby/serving-a-jekyll-blog-using-heroku/)는 Rack-Jekyll 을 사용하여 Heroku 에 게시하는 방법을 설명하고 있으니 한 번 읽어보세요.

<!--
## Jekyll-Admin for Rails
-->
## Rails 를 위한 Jekyll-Admin

<!--
If you want to maintain Jekyll inside your existing Rails app, [Jekyll-Admin](https://github.com/zkarpinski/Jekyll-Admin) contains drop in code to make this possible. See Jekyll-Admin’s [README](https://github.com/zkarpinski/Jekyll-Admin/blob/master/README) for more details.
-->
[Jekyll-Admin](https://github.com/zkarpinski/Jekyll-Admin) 을 사용하면, 자신의 Rails 응용프로그램 내에서 Jekyll 을 관리할 수 있습니다. 더 자세한 내용은 Jekyll-Admin 의 [README](https://github.com/zkarpinski/Jekyll-Admin/blob/master/README) 를 읽어보세요.

## Amazon S3

<!--
If you want to host your site in Amazon S3, you can do so by
using the [s3_website](https://github.com/laurilehmijoki/s3_website)
application. It will push your site to Amazon S3 where it can be served like
any web server,
dynamically scaling to almost unlimited traffic. This approach has the
benefit of being about the cheapest hosting option available for
low-volume blogs as you only pay for what you use.
-->
만약 Amazon S3 에 사이트를 호스팅하고 싶다면,
[s3_website](https://github.com/laurilehmijoki/s3_website) 라는 응용프로그램을
사용하세요. 이 응용프로그램은 거의 무한대의 트래픽까지 유동적으로 규모가
조정되면서,
다른 웹 서버들처럼 서비스되는 Amazon S3 에 당신의 사이트를 업로드 해줍니다.
사용하는 만큼에 대해서만 비용을 지불하기 때문에 소규모 블로그에는 이 방법을
적용하는 것이 가장 저렴할 것입니다.

## OpenShift

<!--
If you'd like to deploy your site to an OpenShift gear, there's [a cartridge
for that](https://github.com/openshift-quickstart/jekyll-openshift).
-->
만약 OpenShift gear 에 사이트를 게시하고자 한다면, [이를 위한
카트리지](https://github.com/openshift-quickstart/jekyll-openshift)를 사용해 보세요.
