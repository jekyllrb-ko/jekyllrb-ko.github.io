---
#title: Commands
title: 명령어
permalink: /docs/plugins/commands/
---
<!--
As of version {% include docs_version_badge.html version="2.5.0"%}, Jekyll can be extended with plugins which provide
subcommands for the `jekyll` executable. This is possible by including the
relevant plugins in a `Gemfile` group called `:jekyll_plugins`:
-->
버전 {% include docs_version_badge.html version="2.5.0"%} 부터, Jekyll 은 `jekyll` 실행파일에 하위명령어를 추가로 제공하는
플러그인들로 확장될 수 있습니다. `Gemfile` 의 `:jekyll_plugins` 라는 그룹에 관련
플러그인을 추가하면 됩니다:

```ruby
group :jekyll_plugins do
  gem "my_fancy_jekyll_plugin"
end
```

<!--
Each `Command` must be a subclass of the `Jekyll::Command` class and must
contain one class method: `init_with_program`. An example:
-->
각 `명령어` 는 반드시 `Jekyll::Command` 클래스의 하위 클래스이어야 하고
`init_with_program` 이라는 하나의 클래스 메소드를 가져야 합니다. 예를 들면 다음과 같습니다:

```ruby
class MyNewCommand < Jekyll::Command
  class << self
    def init_with_program(prog)
      prog.command(:new) do |c|
        c.syntax "new [options]"
        c.description 'Create a new Jekyll site.'

        c.option 'dest', '-d DEST', 'Where the site should go.'

        c.action do |args, options|
          Jekyll::Site.new_site_at(options['dest'])
        end
      end
    end
  end
end
```

<!--
Commands should implement this single class method:
-->
명령어는 반드시 이 클래스 메소드를 구현해야 합니다:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
<!--
      <th>Method</th>
      <th>Description</th>
-->
      <th>메소드</th>
      <th>설명</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>init_with_program</code></p>
      </td>
      <td><p>
<!--
        This method accepts one parameter, the
        <code><a href="https://github.com/jekyll/mercenary#readme">Mercenary::Program</a></code>
        instance, which is the Jekyll program itself. Upon the program,
        commands may be created using the above syntax. For more details,
        visit the Mercenary repository on GitHub.com.
-->
        이 메소드의 파라메터는 단 하나,
        <code><a href="https://github.com/jekyll/mercenary#readme">Mercenary::Program</a></code>
        인스턴스인데 이는 바로 Jekyll 프로그램 그 자체입니다. 프로그램에 따라,
        명령어는 위 문법을 사용해서 생성될 것입니다. 더 자세한 내용은,
        GitHub.com 의 Mercenary 저장소를 방문하세요.
      </p></td>
    </tr>
  </tbody>
</table>
</div>
