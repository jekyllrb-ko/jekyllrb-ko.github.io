---
#title: Jekyll on Ubuntu
title: 우분투에서의 Jekyll
permalink: /docs/installation/ubuntu/
---
<!--
Before we install Jekyll, we need to make sure we have all the required
dependencies.
-->
Jekyll 을 설치하기 전, 필요한 모든 의존요소를 가지고 있는지 확인해야
합니다.

```sh
sudo apt-get install ruby-full build-essential zlib1g-dev
```

<!--
It is best to avoid installing Ruby Gems as the root user. Therefore, we need to
set up a gem installation directory for your user account. The following
commands will add environment variables to your `~/.bashrc` file to configure
the gem installation path. Run them now:
-->
루트 사용자로 루비 젬을 설치하는 것은 피하는게 좋습니다. 따라서, 일반 사용자 계정에
젬 설치 디렉토리를 설정할 필요가 있습니다. 다음 명령어들은 젬 설치 경로를
설정하는 환경설정 변수들을 `~/.bashrc` 파일에 추가할 것입니다.
다음과 같이 실행하세요:

```sh
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

<!--
Finally, install Jekyll:
-->
마지막으로, Jekyll 을 설치합니다:

```sh
gem install jekyll bundler
```

<!--
That's it! You're ready to start using Jekyll.
-->
끝났습니다! 이제 Jekyll 을 사용할 준비가 되었습니다.
