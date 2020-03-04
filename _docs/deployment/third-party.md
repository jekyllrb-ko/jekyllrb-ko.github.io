---
#title: 3rd Party
title: 서드 파티
permalink: /docs/deployment/third-party/
---

## Aerobatic

<!--
[Aerobatic](https://www.aerobatic.com) has custom domains, global CDN distribution, basic auth, CORS proxying, and a growing list of plugins all included.
-->
[Aerobatic](https://www.aerobatic.com) 은 커스텀 도메인, 범세계적 CDN, 기본 인증, CORS 프록시를 제공하고, 점점 더 많은 플러그인을 지원하고 있습니다.

<!--
Automating the deployment of a Jekyll site is simple. See their [Jekyll docs](https://www.aerobatic.com/docs/static-site-generators/#jekyll) for more details. Your built `_site` folder is deployed to their highly-available, globally distributed hosting service.
-->
간단히 Jekyll 사이트 게시를 자동화할 수 있습니다. 더 자세한 내용은 [Jekyll 관련 문서](https://www.aerobatic.com/docs/static-site-generators/#jekyll)를 참고하세요. 중단 없는, 전세계적인 그들의 호스팅 서버에 당신이 생성한 `_site` 를 게시할 수 있습니다. 

## AWS Amplify

<!--
The [AWS Amplify Console](https://console.amplify.aws) provides continuous deployment and hosting for modern web apps (single page apps and static site generators). Continuous deployment allows developers to deploy updates to their web app on every code commit to their Git repository. Hosting includes features such as globally available CDNs, 1-click custom domain setup + HTTPS, feature branch deployments, redirects, trailing slashes, and password protection.
-->
[AWS Amplify Console](https://console.amplify.aws) 은 모던 웹 앱 (단일 페이지 앱과 정적 사이트 생성기) 을 위한 지속적인 배포와 호스팅을 제공합니다. 지속적인 배포는 개발자로 하여금 Git 저장소의 매 커밋마다 그들의 웹 앱에 업데이트를 배포할 수 있게 해줍니다. 호스팅에는 글로벌 CDN, 원클릭 커스텀 도메인 설정과 HTTPS, 기능 브랜치 배포, 리다이렉트, 슬래시로 끝나는 URL, 비밀번호 보호등의 기능들이 포함되어 있습니다.

<!--
Read this [step-by-step guide](https://medium.com/@jameshamann/deploy-your-jekyll-site-using-aws-amplify-with-only-a-few-clicks-8f3dd8f26112) to deploy and host your Jekyll site on AWS Amplify.
-->
당신의 Jekyll 사이트를 AWS Amplify 에 배포하고 호스팅하려면 이 [단계별 가이드](https://medium.com/@jameshamann/deploy-your-jekyll-site-using-aws-amplify-with-only-a-few-clicks-8f3dd8f26112)를 읽어보세요.

## CloudCannon

<!--
[CloudCannon](https://cloudcannon.com) has everything you need to build, host
and update Jekyll websites. Take advantage of our global CDN, automated SSL,
continuous deployment and [more](https://cloudcannon.com/features/).
-->
[CloudCannon](https://cloudcannon.com) 에는 Jekyll 웹사이트 빌드와 호스팅,
업데이트에 필요한 모든 것이 있습니다. 글로벌 CDN 과 자동 SSL, 지속적인 배포,
그리고 다른 [기능들](https://cloudcannon.com/features/)의 장점을 누려보세요.

## GitHub Pages

<!--
Sites on GitHub Pages are powered by Jekyll behind the scenes, so if you’re looking for a zero-hassle, zero-cost solution, GitHub Pages are a great way to [host your Jekyll-powered website for free](/docs/github-pages/).
-->
GitHub Pages 에 있는 페이지들의 내부는 Jekyll 로 동작합니다. 따라서 번거로운 작업이나 시간과 노력이 들지 않는 방법이라면, GitHub Pages 가 [Jekyll 기반의 웹사이트를 무료로 호스팅](/docs/github-pages/)하는 최선의 방법입니다.

## Kickster

<!--
Use [Kickster](http://kickster.nielsenramon.com/) for automated deploys to GitHub Pages when using unsupported plugins on GitHub Pages.
-->
[Kickster](http://kickster.nielsenramon.com/) 를 사용하면 GitHub Pages 에서 지원하지 않는 플러그인을 사용하는 경우에도 자동으로 GitHub Pages 에 게시할 수 있습니다.

<!--
Kickster provides a basic Jekyll project setup packed with web best practises and useful optimization tools increasing your overall project quality. Kickster ships with automated and worry-free deployment scripts for GitHub Pages.
-->
Kickster 가 제공하는 기본 Jekyll 프로젝트의 기본설정은 아주 모범적이며 프로젝트의 전반적인 질을 향상시키는데 유용한 최적화 도구도 포함되어 있습니다. Kickster 는 아무 걱정없이 사용할 수 있는 자동화된 GiHub Pages 용 배포 스크립트를 제공합니다.

<!--
Install the Kickster gem and you are good to go. More documentation can here found [here](https://github.com/nielsenramon/kickster#kickster). If you do not want to use the gem or start a new project you can just copy paste the deployment scripts for [Travis CI](https://github.com/nielsenramon/kickster/tree/master/snippets/travis) or [Circle CI](https://github.com/nielsenramon/kickster#automated-deployment-with-circle-ci).
-->
Kickster 젬만 설치하면 준비는 끝났습니다. 관련 문서는 [여기](https://github.com/nielsenramon/kickster#kickster)서 찾을 수 있습니다. 만약 루비 젬을 설치하거나 새 프로젝트를 만들고 싶지 않다면 [Travis CI](https://github.com/nielsenramon/kickster/tree/master/snippets/travis) 나 [Circle CI](https://github.com/nielsenramon/kickster#automated-deployment-with-circle-ci) 용 배포 스크립트만 복사해 사용할 수 있습니다.


## Netlify

<!--
Netlify provides Global CDN, Continuous Deployment, one click HTTPS and [much more](https://www.netlify.com/features/), providing developers the most robust toolset available for modern web projects, without added complexity. Netlify supports custom plugins for Jekyll and has a free plan for open source projects.
-->
Netlify 는 범세계적인 CDN 과 지속적인 서비스, 손쉬운 HTTPS 설정과 [그 밖의 많은 기능](https://www.netlify.com/features/)으로, 개발자들에게 현대식 웹 프로젝트에 사용할 수 있는 가장 강력한, 하지만 복잡하지 않은, 도구를 제공합니다.

<!--
Read this [Jekyll step-by-step guide](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/) to setup your Jekyll site on Netlify.
-->
Netlify 에 Jekyll 사이트를 구성하려면 [단계적 Jekyll 설정방법](https://www.netlify.com/blog/2015/10/28/a-step-by-step-guide-jekyll-3.0-on-netlify/)을 읽어보세요.

## Static Publisher

<!--
[Static Publisher](https://github.com/static-publisher/static-publisher) is another automated deployment option with a server listening for webhook posts, though it's not tied to GitHub specifically. It has a one-click deploy to Heroku, it can watch multiple projects from one server, it has an easy to user admin interface and can publish to either S3 or to a git repository (e.g. gh-pages).
-->
GitHub 과 연관성은 없지만, Webhook 포스트를 감시하는 서버를 사용한 [Static Publisher](https://github.com/static-publisher/static-publisher) 라는 게시방법도 있습니다. 한 번의 클릭으로 Heroku 에 게시가 가능하고, 한 서버에서 여러 프로젝트를 감시할 수 있으며, 직관적인 관리자 인터페이스를 가지고 있고 S3 와 git 저장소 (예, gh-pages) 에 게시할 수 있습니다.
