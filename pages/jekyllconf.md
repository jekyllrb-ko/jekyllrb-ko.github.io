---
layout: page
title: JekyllConf
permalink: /jekyllconf/
---

<!--
[JekyllConf](http://jekyllconf.com) is a free, online conference for all things Jekyll hosted by [CloudCannon](http://cloudcannon.com). Each year members of the Jekyll community speak about interesting use cases, tricks they've learned, or meta Jekyll topics.
-->
[JekyllConf](http://jekyllconf.com) 는 [CloudCannon](http://cloudcannon.com) 이 주최하는 무료, 온라인 컨퍼런스로서 Jekyll 에 관한 모든 것을 다룹니다. 매년 Jekyll 커뮤니티 멤버들이 흥미로운 사용 사례와 그들이 발견한 트릭 또는 기타 Jekyll 관련 주제에 관해 이야기합니다.

## Featured

{% assign random = site.time | date: "%s%N" | modulo: site.data.jekyllconf-talks.size %}
{% assign featured = site.data.jekyllconf-talks[random] %}

**{{ featured.topic }}** - [*{{ featured.speaker }}*](https://twitter.com/{{ featured.twitter_handle }})
<div class="videoWrapper">
    <iframe width="420" height="315" src="https://www.youtube.com/embed/{{ featured.youtube_id }}" frameborder="0" allowfullscreen></iframe>
</div>

{% assign talks = site.data.jekyllconf-talks | group_by: 'year' %}
{% for year in talks reversed %}
## {{ year.name }}
{% for talk in year.items %}
 * [**{{ talk.topic }}**](https://youtu.be/{{ talk.youtube_id }}) - [*{{ talk.speaker }}*](https://twitter.com/{{ talk.twitter_handle }})
{% endfor %}
{% endfor %}
