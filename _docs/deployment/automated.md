---
#title: Automated Deployment
title: 자동 배포
permalink: /docs/deployment/automated/
---
<!--
There are a number of ways to easily automate the deployment of a Jekyll site.
-->
Jekyll 사이트 게시를 쉽게 자동화해주는 방법이 몇 가지 있습니다.

<!--
## Continuous Integration Service
-->
## CI 서비스

<!--
One of the easiest ways to set up an automated deployment flow is by using a
CI.
-->
배포 작업을 자동화하는 가장 쉬운 방법 중 하나는
CI 를 사용하는 것입니다.

<!--
These services run a script when there's a commit on your Git repository.
You might want this script to build the site, run tests over the output then deploy it to the
service of your choice. 
-->
이 서비스들은 Git 저장소에 커밋이 있을 때 스크립트를 실행합니다.
이 스크립트는 사이트를 빌드하고, 결과물에 대해 테스트를 수행한 다음 당신이 원하는
서비스에 배포합니다.

<!--
We have guides for the following providers:
-->
다음 서비스들에 대해 가이드가 준비되어 있습니다:

* [Travis CI](/docs/continuous-integration/travis-ci/)
* [CircleCI](/docs/continuous-integration/circleci/)
* [Buddy](/docs/continuous-integration/buddyworks/)

<!--
## Git post-receive hook
-->
## Git 의 post-receive 훅

<!--
To have a remote server handle the deploy for you every time you push changes using Git, you can create a user account which has all the public keys that are authorized to deploy in its `authorized_keys` file. With that in place, setting up the post-receive hook is done as follows:
-->
Git 으로 변경사항을 push 할 때마다 원격 서버가 자동으로 게시 작업을 수행하도록 구성하려면, 일단 새 계정을 만들어 `authorized_keys` 파일에 게시작업 인증 시 사용되는 공개키를 모두 등록합니다. 그 다음, 아래와 같이 post-receive 훅을 설정합니다:

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
#!/bin/bash -l

# Install Ruby Gems to ~/gems
export GEM_HOME=$HOME/gems
export PATH=$GEM_HOME/bin:$PATH

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
