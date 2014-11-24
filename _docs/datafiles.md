---
layout: docs
title: 데이터 파일
prev_section: collections
next_section: assets
permalink: /docs/datafiles/
---

[내장 변수](../variables/)뿐만 아니라, 자신만의 데이터를 정의해서 [Liquid 템플릿
시스템](https://wiki.github.com/shopify/liquid/liquid-for-designers)을 통해
사용할 수 있습니다.

Jekyll 은 `_data` 디렉토리의 [YAML](http://yaml.org/) 과 [JSON](http://www.json.org/),
[CSV](https://en.wikipedia.org/wiki/Comma-separated_values) 파일로부터 데이터를
읽어들일 수 있습니다. 단, CSV 파일에는 *반드시* 헤더 행이 있어야 합니다.

이 강력한 기능 덕분에 템플릿에 뭔가를 반복해서 입력하지 않아도 되고,
`_config.yml` 파일을 수정하지 않고 사이트 옵션을 설정할 수 있습니다.

플러그인/테마도 데이터 파일을 사용하여 환경설정 변수를 설정할 수 있습니다.

## 데이터 폴더

[디렉토리 구조](../structure/) 페이지에서 설명했던 것처럼, `_data` 폴더는
사이트를 생성할 때 사용하는 부가적인 데이터를 저장하는 공간입니다. 이것들은
반드시 (`.yml`, `.yaml`, `.json` 이나 `csv` 확장자를 가진) YAML 파일이어야 하며
`site.data` 를 통해 접근할 수 있습니다.

## 예제: 멤버들의 목록

커다란 코드 뭉치를 여러 Jekyll 템플릿에 복사-붙여넣기하지 않기 위해 데이터
파일을 활용하는 기본적인 예제입니다:

`_data/members.yml` 에:

{% highlight yaml %}
- name: Tom Preston-Werner
  github: mojombo

- name: Parker Moore
  github: parkr

- name: Liu Fengyun
  github: liufengyun
{% endhighlight %}

또는 `_data/members.csv` 에:

{% highlight text %}
name,github
Tom Preston-Werner,mojombo
Parker Moore,parkr
Liu Fengyun,liufengyun
{% endhighlight %}

`site.data.members` 로 (파일 이름이 변수 이름으로 사용되는 것에 주목) 이
데이터에 접근할 수 있습니다.

이제 템플릿에서 멤버들 목록을 출력할 수 있습니다:

{% highlight html %}
{% raw %}
<ul>
{% for member in site.data.members %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

## 예제: 단체

`_data` 의 하위 폴더에도 데이터 파일을 담을 수 있습니다. 각 폴더 레벨은 변수의 네임스페이스에 영향을 줍니다. 아래는 여러 GitHub 단체를 `orgs` 폴더 안에 각각 별도의 파일로 정의하고 예제입니다:

`_data/orgs/jekyll.yml` 파일:

{% highlight yaml %}
username: jekyll
name: Jekyll
members:
  - name: Tom Preston-Werner
    github: mojombo

  - name: Parker Moore
    github: parkr
{% endhighlight %}

`_data/orgs/doeorg.yml` 파일:

{% highlight yaml %}
username: doeorg
name: Doe Org
members:
  - name: John Doe
    github: jdoe
{% endhighlight %}

파일 이름을 `site.data.orgs` 뒤에 적으면, 단체 정보에 접근할 수 있습니다:

{% highlight html %}
{% raw %}
<ul>
{% for org_hash in site.data.orgs %}
{% assign org = org_hash[1] %}
  <li>
    <a href="https://github.com/{{ org.username }}">
      {{ org.name }}
    </a>
    ({{ org.members | size }} members)
  </li>
{% endfor %}
</ul>
{% endraw %}
{% endhighlight %}
