---
#title: Ruby 101
title: 루비 기초
permalink: /docs/ruby-101/
---

<!--
Jekyll is written in Ruby. If you're new to Ruby, this page is to help you get
up to speed with some of the terminology.
-->
Jekyll 은 루비로 작성되었습니다. 루비를 처음 접한다면, 용어들에 빨리 익숙해지는데에
이 페이지가 도움이 될 것입니다.

<!--
## Gems
-->
## 젬

<!--
A gem is code you can include in Ruby projects. It allows you to package up functionality and share it across other projects or with other people. Gems can perform functionality such as:
-->
젬은 루비 프로젝트에 포함시킬 수 있는 코드입니다. 기능들을 패키지화해서 다른 사람들이나 프로젝트에 공유할 수 있게 해줍니다. 젬은 다음과 같은 기능을 가질 수 있습니다:

<!--
* Converting a Ruby object to JSON
* Pagination
* Interacting with APIs such as GitHub
* Jekyll itself is a gem as well as many Jekyll plugins including
[jekyll-feed](https://github.com/jekyll/jekyll-feed),
[jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) and
[jekyll-archives](https://github.com/jekyll/jekyll-archives).
-->
* 루비 오브젝트를 JSON 으로 변환
* 페이지 나누기
* GitHub 과 같은 API 와 연동
* Jekyll 자체도 [jekyll-feed](https://github.com/jekyll/jekyll-feed) 와
[jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag),
[jekyll-archives](https://github.com/jekyll/jekyll-archives)
같은 Jekyll 플러그인과 마찬가지로 하나의 젬이다.


## Gemfile

<!--
A `Gemfile` is a list of gems required for your site. For a simple Jekyll site it might look something like this:
-->
`Gemfile` 은 사이트에 필요한 젬들의 목록입니다. 단순한 Jekyll 사이트를 예로 들면 이렇게 생겼습니다:

```ruby
source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

## Bundler

<!--
Bundler installs the gems in your `Gemfile`. It's not a requirement for you to use a `Gemfile` and `bundler` however it's highly recommended as it ensures you're running the same version of Jekyll and Jekyll plugins across different environments.
-->
Bundler 는 `Gemfile` 에 있는 젬들을 설치합니다. `Gemfile` 과 `bundler` 를 사용하는 것이 필수는 아니지만 여러 다른 환경에서 올바른 버전의 Jekyll 과 Jekyll 플러그인을 사용하게 도와주기 때문에 적극적으로 권장하고 있습니다.

<!--
`gem install bundler` installs [Bundler](https://rubygems.org/gems/bundler). You only need to install it once &mdash; not every time you create a new Jekyll project. Here are some additional details:
-->
`gem install bundler` 명령으로 [Bundler](https://rubygems.org/gems/bundler) 를 설치합니다. 이 설치는 한 번만 하면 됩니다 &mdash; Jekyll 프로젝트를 생성할 때마다가 아닙니다. 여기 세부사항이 몇 가지 더 있습니다:

<!--
If you're using a `Gemfile` you would first run `bundle install` to install the gems, then `bundle exec jekyll serve` to build your site. This guarantees you're using the gem versions set in the `Gemfile`. If you're not using a `Gemfile` you can just run `jekyll serve`.
-->
만약 `Gemfile` 을 사용하고 있다면 먼저 `bundle install` 을 실행해 젬들을 설치하고, `bundle exec jekyll serve` 로 사이트를 빌드합니다. 이는 `Gemfile` 에 설정된 버전의 젬들을 사용하도록 보장해줍니다. `Gemfile` 을 사용하지 않는다면 그냥 `jekyll serve` 라고 실행하면 됩니다.

<!--
For more information about how to use Bundler in your Jekyll project, this [tutorial](/tutorials/using-jekyll-with-bundler/) should provide answers to the most common questions and explain how to get up and running quickly.
-->
당신의 Jekyll 프로젝트에 Bundler 를 사용하는 방법에 대한 더 자세한 내용을 원하는 경우, 이 [튜토리얼](/tutorials/using-jekyll-with-bundler/)에 가장 흔히 묻는 질문들에 대한 답변과 빠르게 준비를 끝내고 실행하는 방법이 설명되어 있습니다.
