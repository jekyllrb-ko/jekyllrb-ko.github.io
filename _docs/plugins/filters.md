---
#title: Filters
title: 필터
permalink: /docs/plugins/filters/
---

<!--
Filters are modules that export their methods to liquid.
All methods will have to take at least one parameter which represents the input
of the filter. The return value will be the output of the filter.
-->
필터는 Liquid 에 메소드를 추가하는 모듈입니다.
모든 메소드에는 최소한 하나의 매개변수가 있어야 하며, 이것은 바로 필터의
입력입니다. 반환 값이 필터의 출력이 됩니다.

```ruby
module Jekyll
  module AssetFilter
    def asset_url(input)
      "http://www.example.com/#{input}?#{Time.now.to_i}"
    end
  end
end

Liquid::Template.register_filter(Jekyll::AssetFilter)
```

<div class="note">
<!--
  <h5>ProTip™: Access the site object using Liquid</h5>
  <p>
    Jekyll lets you access the <code>site</code> object through the
    <code>@context.registers</code> feature of Liquid at <code>@context.registers[:site]</code>. For example, you can
    access the global configuration file <code>_config.yml</code> using
    <code>@context.registers[:site].config</code>.
  </p>
-->
  <h5>ProTip™: Liquid 를 사용해서 site 객체에 접근할 수 있습니다</h5>
  <p>
    Jekyll 은 <code>@context.registers[:site]</code> 와 같이 Liquid 의
    <code>@context.registers</code> 기능을 통해서 <code>site</code> 객체에 접근할
    수 있게 해줍니다. 예를 들어, <code>@context.registers[:site].config</code>
    라고 입력하여 전역 환경설정 파일 <code>_config.yml</code> 에 접근할 수 있습니다.
  </p>
</div>
