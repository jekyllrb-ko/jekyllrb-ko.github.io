---
#title: Jekyll on Linux
title: 리눅스에서의 Jekyll
permalink: /docs/installation/other-linux/
---
<!--
Installation on other Linux distributions works similarly as on [Ubuntu](../ubuntu/).
-->
[우분투](../ubuntu/)에서의 설치방법을 다른 리눅스 배포판에도 비슷하게 적용할 수 있습니다.

<!--
On Fedora, the dependencies can be installed as follows:
-->
페도라의 경우, 의존요소를 설치할 때 다음과 같이 실행합니다:

 ```sh
sudo dnf install ruby ruby-devel @development-tools
```

<!--
On Debian:
-->
데비안에서는:

```sh
sudo apt-get install ruby-full build-essential
```

<!--
On ArchLinux:
-->
ArchLinux 에서는:

```sh
sudo pacman -S ruby base-devel
```

<!--
On openSUSE:
-->
openSUSE 에서는:

```sh
sudo zypper install -t pattern devel_ruby devel_C_C++
```

<!--
The rest works the same as on [Ubuntu](../ubuntu/).
-->
나머지 절차들은 [우분투](../ubuntu/)와 동일합니다.
