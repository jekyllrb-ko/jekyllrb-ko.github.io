---
layout: docs
title: 데이터 파일
prev_section: collections
next_section: assets
permalink: /docs/datafiles/
---

Jekyll 의 [내장 변수](../variables/)에 이어서, [Liquid 템플릿 시스템](https://wiki.github.com/shopify/liquid/liquid-for-designers)을 통해 접근할 수 있는 자신만의 고유 데이터를 작성할 수 있습니다.

Jekyll 은 `_data` 디렉토리에 있는 [YAML](http://yaml.org/) 과 [JSON](http://www.json.org/), [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) 파일로부터 데이터를 읽어들일 수 있습니다. 여기서 CSV 파일에는 *반드시* 헤더 행이 있어야 합니다.

이 강력한 기능으로 당신은 템플릿에 반복적인 작업을 피할 수 있고 `_config.yml` 파일을 수정하지 않고 사이트 전반적인 옵션을 설정할 수 있습니다.

플러그인/테마도 데이터 파일을 사용하여 환경설정 변수를 설정할 수 있습니다.

## 데이터 폴더

[디렉토리 구조](../structure/) 페이지에 설명한 것처럼, `_data` 폴더는 자신의 사이트를 생성할 때 Jekyll 이 사용하는 부가적인 데이터를 저장할 수 있는 공간입니다. 이것들은 반드시 (`.yml`, `.yaml` 이나 `.json` 을 사용하는) YAML 파일이어야 하며 `site.data` 를 통해 접근할 수 있습니다.

## 예제: 멤버들의 목록

여기 데이터 파일을 활용하여, Jekyll 템플릿에 큰 코드 조각을 복사-붙여넣기 하는 것을 피하는 기본 예제가 있습니다:

`_data/members.yml` 에:

{% highlight yaml %}
- name: Tom Preston-Werner
  github: mojombo

- name: Parker Moore
  github: parkr

- name: Liu Fengyun
  github: liufengyun
{% endhighlight %}

이 데이터는 `site.data.members` 로 (파일 이름이 변수 이름을 결정짓는 것에 주목하세요) 접근할 수 있습니다.

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

데이터 파일은 `_data` 폴더의 하위 폴더에 담을 수도 있다. 각 폴더 레벨은 변수의 네임스페이스에 영향을 미친다. 아래 예제는 GitHub 단체가 `orgs` 폴더에 별도로 정의될 수 있다는 것을 보여준다:

`_data/orgs/jekyll.yml` 에:

{% highlight yaml %}
username: jekyll
name: Jekyll
members:
  - name: Tom Preston-Werner
    github: mojombo

  - name: Parker Moore
    github: parkr
{% endhighlight %}

`_data/orgs/doeorg.yml` 에:

{% highlight yaml %}
username: doeorg
name: Doe Org
members:
  - name: John Doe
    github: jdoe
{% endhighlight %}

그 다음 단체는 `site.data.orgs` 를 통해서, 파일이름을 이어 적고 접근할 수 있습니다:

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
