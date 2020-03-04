---
#title: Manual Deployment
title: 수동 배포
permalink: /docs/deployment/manual/
---

<!--
Jekyll generates your static site to the `_site` directory by default. You can
transfer the contents of this directory to almost any hosting provider to get
your site live. Here are some manual ways of achieving this:
-->
Jekyll 은 기본적으로 `_site` 디렉토리에 정적 사이트를 생성합니다. 거의 모든,
어떤 호스팅 제공자든지 이 디렉토리의 내용을 전송해서 사이트를
띄울 수 있습니다. 수동으로 이를 수행하는 방법은 다음과 같습니다:

## rsync

<!--
Rsync is similar to scp except it can be faster as it will only send changed
parts of files as opposed to the entire file. You can learn more about using
rsync in the [Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps).
-->
Rsync 는 scp 와 유사하지만 파일 전체를 보내지 않고 변경된 부분만 보내기 때문에
더 빠르다는 차이점이 있습니다.
[Digital Ocean tutorial](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps) 에서 Rsync 를 사용하는 방법을 배울 수 있습니다.

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

## FTP

<!--
Most traditional web hosting provider let you upload files to their servers over FTP. To upload a Jekyll site to a web host using FTP, run the `jekyll build` command and copy the contents of the generated `_site` folder to the root folder of your hosting account. This is most likely to be the `httpdocs` or `public_html` folder on most hosting providers.
-->
대부분의 웹 호스팅 제공자들이 FTP 로 서버에 파일을 업로드하는 것을 허용합니다. FTP 를 이용해서 Jekyll 사이트를 웹 호스트 서버에 업로드하는 방법은, `jekyll build` 명령을 실행 한 뒤에 생성된 `_site` 폴더의 내용을 호스팅 계정의 루트 폴더에 복사하는 것입니다. 대부분의 경우 이 루트 폴더의 이름은 `httpdocs` 나 `public_html` 입니다.

## scp

<!--
If you have direct access to the deployment web server, the process is essentially the same, except you might have other methods available to you (such as `scp`, or even direct filesystem access) for transferring the files. Remember to make sure the contents of the generated `_site` folder get placed in the appropriate web root directory for your web server.
-->
게시하려는 웹 서버에 접속할 권한이 있다면, 해야할 작업 내용은 근본적으로 동일하지만, 파일을 옮기는 방법에 몇 가지 다른 선택사항 (`scp` 또는 파일 시스템에 직접 접근) 이 생깁니다. 기억해야할 것은 생성된 `_site` 폴더 내용을 옮길 때 반드시 웹 서버의 올바른 웹 루트 디렉토리에 저장해야 한다는 점입니다.


## Rack-Jekyll

<!--
[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) allows you to deploy your site on any Rack server such as Amazon EC2, Slicehost, Heroku, and so forth. It also can run with [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/), and [others](https://github.com/adaoraul/rack-jekyll#readme).
-->
[Rack-Jekyll](https://github.com/adaoraul/rack-jekyll/) 은 Amazon EC2 나 Slicehost, Heroku 등의 Rack 서버에 사이트를 배포할 수 있게 해줍니다. [shotgun](https://github.com/rtomayko/shotgun/), [rackup](https://github.com/rack/rack), [mongrel](https://github.com/mongrel/mongrel), [unicorn](https://github.com/defunkt/unicorn/) 이나 [그 밖에 다른 것들](https://github.com/adaoraul/rack-jekyll#readme)과 함께 사용할 수 있습니다.
