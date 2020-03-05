# Jekyll 문서 사이트 한글 번역

Jekyll 문서 사이트 [jekyllrb.com](https://jekyllrb.com/) 의 한글 번역 [jekyllrb-ko.github.io](https://jekyllrb-ko.github.io) 저장소입니다.

## 로컬 서버 구동 방법

프로젝트 루트 디렉토리에서 다음과 같이 입력합니다:

1. `bundle config set --local path vendor/bundle`
2. `bundle install`
3. `bundle exec jekyll serve`

## Updating Font Awesome

1. Go to <https://icomoon.io/app/>
2. Choose Import Icons and load `icomoon-selection.json`
3. Choose Generate Font → Download
4. Copy the font files and adapt the CSS to the paths we use in Jekyll
