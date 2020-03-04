---
#title: Data Files
title: 데이터 파일
permalink: /docs/datafiles/
---

<!--
In addition to the [built-in variables](../variables/) available from Jekyll,
you can specify your own custom data that can be accessed via the [Liquid
templating system](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).
-->
[기본 변수](../variables/)뿐만 아니라, [Liquid 템플릿
시스템](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)을 통해
접근할 수 있는 자신만의 데이터를 정의할 수도 있습니다.

<!--
Jekyll supports loading data from [YAML](http://yaml.org/), [JSON](http://www.json.org/), [CSV](https://en.wikipedia.org/wiki/Comma-separated_values), and [TSV](https://en.wikipedia.org/wiki/Tab-separated_values) files located in the `_data` directory.
Note that CSV and TSV files *must* contain a header row.
-->
Jekyll 은 `_data` 디렉토리의 [YAML](http://yaml.org/) 과 [JSON](http://www.json.org/), [CSV](https://en.wikipedia.org/wiki/Comma-separated_values), [TSV](https://en.wikipedia.org/wiki/Tab-separated_values) 파일로부터 데이터를 읽어들일 수 있습니다.
단, CSV 와 TSV 파일에는 *반드시* 헤더 행이 있어야 합니다.

<!--
This powerful feature allows you to avoid repetition in your templates and to
set site specific options without changing `_config.yml`.
-->
이 강력한 기능 덕분에 무언가를 반복해서 템플릿에 입력하는 일을 피할 수 있고,
`_config.yml` 파일을 수정하지 않고도 사이트 옵션을 설정할 수 있습니다.

<!--
Plugins/themes can also leverage Data Files to set configuration variables.
-->
플러그인/테마에서도 데이터 파일을 사용하여 환경설정 변수를 설정할 수 있습니다.

<!--
## The Data Folder
-->
## 데이터 폴더

<!--
The `_data` folder is where you can store additional data for Jekyll to use when
generating your site. These files must be YAML, JSON, or CSV files (using either
the `.yml`, `.yaml`, `.json` or `.csv` extension), and they will be
accessible via `site.data`.
-->
`_data` 폴더는 사이트를 생성할 때 사용하는 부가적인 데이터를 저장하는
공간입니다. 이 파일들은 반드시 YAML 이나 JSON, CSV 파일 (확장자가 `.yml`,
`.yaml` 이나 `.json`, `.csv`) 이어야 하며, `site.data` 를 통해 이
데이터를 사용할 수 있습니다.

<!--
## Example: List of members
-->
## 예제: 구성원 목록

<!--
Here is a basic example of using Data Files to avoid copy-pasting large chunks
of code in your Jekyll templates:
-->
커다란 코드 뭉치를 여러 Jekyll 템플릿에 복사-붙여넣기하지 않기 위해 데이터
파일을 활용하는 기본적인 예제입니다:

<!--
In `_data/members.yml`:
-->
`_data/members.yml` 에:

```yaml
- name: Eric Mill
  github: konklone

- name: Parker Moore
  github: parkr

- name: Liu Fengyun
  github: liufengyun
```

<!--
Or `_data/members.csv`:
-->
또는 `_data/members.csv` 에:

```
name,github
Eric Mill,konklone
Parker Moore,parkr
Liu Fengyun,liufengyun
```

<!--
This data can be accessed via `site.data.members` (notice that the filename
determines the variable name).
-->
`site.data.members` 로 (파일명이 변수 이름으로 사용되는 것에 주목) 이
데이터에 접근할 수 있습니다.

<!--
You can now render the list of members in a template:
-->
이제 템플릿에 멤버들 목록을 출력할 수 있습니다:

{% raw %}
```liquid
<ul>
{% for member in site.data.members %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>
```
{% endraw %}

<!--
## Subfolders
-->
## 하위 폴더

<!--
Data files can also be placed in sub-folders of the `_data` folder. Each folder
level will be added to a variable's namespace. The example below shows how
GitHub organizations could be defined separately in a file under the `orgs`
folder:
-->
`_data` 의 하위 폴더에도 데이터 파일을 저장할 수 있습니다. 각 단계의 폴더 이름이
변수의 네임스페이스에 영향을 줍니다. 아래 예시에서는 여러 GitHub 단체들의 정보를
별도의 파일로 각각 분리하여 `orgs` 폴더 안에 정의하는 방법을 보여주고 있습니다:


<!--
In `_data/orgs/jekyll.yml`:
-->
`_data/orgs/jekyll.yml` 파일:

```yaml
username: jekyll
name: Jekyll
members:
  - name: Tom Preston-Werner
    github: mojombo

  - name: Parker Moore
    github: parkr
```

<!--
In `_data/orgs/doeorg.yml`:
-->
`_data/orgs/doeorg.yml` 파일:

```yaml
username: doeorg
name: Doe Org
members:
  - name: John Doe
    github: jdoe
```

<!--
The organizations can then be accessed via `site.data.orgs`, followed by the
file name:
-->
이제 `site.data.orgs` 뒤에 파일명을 사용하면, 단체 정보에 접근할 수 있습니다:


{% raw %}
```liquid
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
```
{% endraw %}

<!--
## Example: Accessing a specific author
-->
## 예제: 특정 저자 정보 사용하기

<!--
Pages and posts can also access a specific data item. The example below shows how to access a specific item:
-->
페이지나 포스트는 특정 데이터를 사용할 수 있습니다. 아래 예제는 특정 정보에 접근하는 방법을 보여줍니다:

`_data/people.yml`:

```yaml
dave:
    name: David Smith
    twitter: DavidSilvaSmith
```

<!--
The author can then be specified as a page variable in a post's front matter:
-->
이제 포스트의 머리말에 페이지 변수처럼 저자 정보를 정의할 수 있습니다:

{% raw %}
```liquid
---
title: sample post
author: dave
---

{% assign author = site.data.people[page.author] %}
<a rel="author"
  href="https://twitter.com/{{ author.twitter }}"
  title="{{ author.name }}">
    {{ author.name }}
</a>
```
{% endraw %}

<!--
For information on how to build robust navigation for your site (especially if you have a documentation website or another type of Jekyll site with a lot of pages to organize), see [Navigation](/tutorials/navigation).
-->
당신의 사이트에 어울리는 탄탄한 탐색기능 구축방법에 대해서는(특히 설명서 웹사이트거나 정리해야할 페이지가 아주 많은 Jekyll 사이트인 경우), [탐색](/tutorials/navigation)을 살펴보세요.
