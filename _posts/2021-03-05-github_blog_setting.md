---

title: "깃허브 블로그 커스터마이징"
excerpt: "깃 블로그는 Github 저장소에 저장된 html 파일과 같은 정적 웹 문서들을 GitHub에서 무료로 웹에서 볼 수 있도록 호스팅 서비스를 제공해 주는 블로그이다." 

categories:
  - Blog
tags:
  - Blog
last_modified_at: 2021-03-05 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### Git Blog란

깃 블로그는 Github 저장소에 저장된 html 파일과 같은 정적 웹 문서들을 GitHub에서 무료로 웹에서 볼 수 있도록 호스팅 서비스를 제공해 주는 블로그이다. Github 계정을 갖고 있는 사용자들은 누구나 자신만의 정적 웹 사이트 1개를 가질 수 있다. 저장소명은 `{Git ID}.github.com` 으로 세팅하면 된다. 그렇게 저장소를 만들면 자동으로 `Github Pages` 가 생성되게 된다. 



### Jekyll이란

Jekyll이란 HTML(.html), Markdown(.md) 등 다양한 포맷의 텍스트들을 읽고 가공하여 자신의 웹 사이트에 바로 게시할 수 있게 해주는 Ruby언어로 만들어진 하나의 **텍스트 변환 엔진**이다. 쉽게 말해 html을 모르더라도 공부하기 비교적 수월한 markdown 파일을 작성하면 알아서 html파일로 변환되어 웹 서비스를 구축해준다. Jekyll을 사용하여 게시글을 작성한다면 웹 사이트를 효율적으로 구성할 수 있다. Jekyll은 Github의 내부 엔진이기 때문에 Github page에서도 자연스럽게 동작한다. 이러한 Jekyll을 가지고 사용자들이 다양한 테마를 미리 만들고 공유하고 있는데 주소는 아래와 같다. 아래의 주소에서 원하는 블로그 디자인 테마를 적용할 수 있다. 참고로 이 블로그는 <https://github.com/mmistakes/minimal-mistakes> 기반으로 커스터마이징 되었다. 

- <http://jekyllthemes.org/>
- <http://themes.jekyllrc.org/>
- <https://jekyllthemes.io/>



### Customizing

#### 1. _config.yml 수정

깃허브 페이지의 큰 부분들을 커스터마이징 하는 곳이라고 생각하면 된다. 주석으로 설명이 되어있기 때문에 직관적으로 필요한 부분을 고치면 된다. 

~~~yaml
# Welcome to Jekyll!
#
# This config file is meant for settings that affect your entire site, values
# which you are expected to set up once and rarely need to edit after that.
# For technical reasons, this file is *NOT* reloaded automatically when you use
# `jekyll serve`. If you change this file, please restart the server process.

# Theme Settings
#
# Review documentation to determine if you should use `theme` or `remote_theme`
# https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#installing-the-theme

# theme                  : "minimal-mistakes-jekyll"
# remote_theme           : "mmistakes/minimal-mistakes"
minimal_mistakes_skin    : "custom" # 현재 내 스킨은 custom.scss 파일에 커스터마이징 되어 있다. "default" "contrast", "aqua", "air", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "en-US"
title                    : "Divide and Comquer"
title_separator          : "-"
subtitle                 : # site tagline that appears below site title in masthead
name                     : "Yohan Sun"
description              : "An amazing website."
url                      : "https://syh39.github.io" # the base hostname & protocol for your site e.g. "https://mmistakes.github.io"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : # GitHub username/repo-name e.g. "mmistakes/minimal-mistakes"
teaser                   : "/assets/images/profile_image.jpg"# path of fallback teaser image, e.g. "/assets/images/500x300.png"
logo                     : # "/assets/mylogo2.png"  # 최상단 메뉴 바에 사이트 로고 넣기 / path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"
masthead_title           : "Divide and Comquer" # overrides the website title displayed in the masthead, use " " for no title
# breadcrumbs            : false # true, false (default)
words_per_minute         : 200
comments:
  provider               : "disqus" # false (default), "disqus", "discourse", "facebook", "staticman", "staticman_v2", "utterances", "custom"
  disqus:
    shortname            : "syh39-github-io" # https://help.disqus.com/customer/portal/articles/466208-what-s-a-shortname-
  discourse:
    server               : # https://meta.discourse.org/t/embedding-discourse-comments-via-javascript/31963 , e.g.: meta.discourse.org
  facebook:
    # https://developers.facebook.com/docs/plugins/comments
    appid                :
    num_posts            : # 5 (default)
    colorscheme          : # "light" (default), "dark"
  utterances:
    theme                : minimal-mistakes-jekyll # "github-light" (default), "github-dark"
    issue_term           : # "pathname" (default)
  staticman:
    branch               : # "master"
    endpoint             : # "https://{your Staticman v3 API}/v3/entry/github/"
reCaptcha:
  siteKey                :
  secret                 :
atom_feed:
  path                   : # blank (default) uses feed.xml
search                   : true # true, false (default)
search_full_content      : # true, false (default)
search_provider          : # lunr (default), algolia, google
algolia:
  application_id         : # YOUR_APPLICATION_ID
  index_name             : # YOUR_INDEX_NAME
  search_only_api_key    : # YOUR_SEARCH_ONLY_API_KEY
  powered_by             : # true (default), false
google:
  search_engine_id       : ######## 비공개 ########  # YOUR_SEARCH_ENGINE_ID
  instant_search         : # false (default), true
# SEO Related
google_site_verification :
bing_site_verification   :
yandex_site_verification :
naver_site_verification  :

# Header 
header:
  image: /assets/images/header-image.jpg

# Social Sharing
twitter:
  username               :
facebook:
  username               :
  app_id                 :
  publisher              :
og_image                 : "/assets/images/profile-image.jpg" # Open Graph/Twitter default site image
# For specifying social profiles
# - https://developers.google.com/structured-data/customize/social-profiles
social:
  type                   : # Person or Organization (defaults to Person)
  name                   : # If the user or organization name differs from the site's name
  links: # An array of links to social media profiles

# Analytics
analytics:
  provider               : "google-gtag" # false (default), "google", "google-universal", "custom"
  google:
    tracking_id          : ######## 비공개 ########
    anonymize_ip         : false # true, false (default)


# Site Author
author:
  name             : "Yohan Sun" # 왼쪽 상단에 보여질 내 이름
  avatar           : "/assets/images/profile3.jpg" # 왼쪽 상단에 보여질 프로필 이미지# path of avatar image, e.g. "/assets/images/bio-photo.jpg"
  bio              : "Happy Coding :)"  # 왼쪽 상단에 보여질 상태메세지 # - 폴 부르제"  # "컴린이의 좌충우돌 일기메모장<br><br>
  location         : "Pohang, Korea"  # 왼쪽 상단에 보여질 내 위치
  email            :
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: mailto:syh30@naver.com
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://syh39.github.io"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url: "https://twitter.com/"
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url: "https://facebook.com/"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/syh39"
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      # url: "https://instagram.com/"

# Site Footer
footer:
  links:
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url:
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/syh39"
    - label: "GitLab"
      icon: "fab fa-fw fa-gitlab"
      # url:
    - label: "Bitbucket"
      icon: "fab fa-fw fa-bitbucket"
      # url:
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      # url:


# Reading Files
include:
  - .htaccess
  - _pages
exclude:
  - "*.sublime-project"
  - "*.sublime-workspace"
  - vendor
  - .asset-cache
  - .bundle
  - .jekyll-assets-cache
  - .sass-cache
  - assets/js/plugins
  - assets/js/_main.js
  - assets/js/vendor
  - Capfile
  - CHANGELOG
  - config
  - Gemfile
  - Gruntfile.js
  - gulpfile.js
  - LICENSE
  - log
  - node_modules
  - package.json
  - package-lock.json
  - Rakefile
  - README
  - tmp
  - /docs # ignore Minimal Mistakes /docs
  - /test # ignore Minimal Mistakes /test
keep_files:
  - .git
  - .svn
encoding: "utf-8"
markdown_ext: "markdown,mkdown,mkdn,mkd,md"


# Conversion
markdown: kramdown
highlighter: rouge
lsi: false
excerpt_separator: "\n\n"
incremental: false


# Markdown Processing
kramdown:
  input: GFM
  hard_wrap: false
  auto_ids: true
  footnote_nr: 1
  entity_output: as_char
  toc_levels: 1..6
  smart_quotes: lsquo,rsquo,ldquo,rdquo
  enable_coderay: false


# Sass/SCSS
sass:
  sass_dir: _sass
  style: compressed # https://sass-lang.com/documentation/file.SASS_REFERENCE.html#output_style


# Outputting
permalink: /:categories/:title/
paginate: 6 # 첫 페이지에 보여줄 최근 게시물 수를 지정
paginate_path: /page:num/
timezone: Asia/Seoul # https://en.wikipedia.org/wiki/List_of_tz_database_time_zones


# Plugins (previously gems:)
plugins:
  - jekyll-paginate
  - jekyll-sitemap
  - jekyll-gist
  - jekyll-feed
  - jekyll-include-cache

# mimic GitHub Pages with --safe
whitelist:
  - jekyll-paginate
  - jekyll-sitemap
  - jekyll-gist
  - jekyll-feed
  - jekyll-include-cache


# Archives
#  Type
#  - GitHub Pages compatible archive pages built with Liquid ~> type: liquid (default)
#  - Jekyll Archives plugin archive pages ~> type: jekyll-archives
#  Path (examples)
#  - Archive page should exist at path when using Liquid method or you can
#    expect broken links (especially with breadcrumbs enabled)
#  - <base_path>/tags/my-awesome-tag/index.html ~> path: /tags/
#  - <base_path>/categories/my-awesome-category/index.html ~> path: /categories/
#  - <base_path>/my-awesome-category/index.html ~> path: /
category_archive:
  type: liquid
  path: /categories/
tag_archive:
  type: liquid
  path: /tags/
# https://github.com/jekyll/jekyll-archives
# jekyll-archives:
#   enabled:
#     - categories
#     - tags
#   layouts:
#     category: archive-taxonomy
#     tag: archive-taxonomy
#   permalinks:
#     category: /categories/:name/
#     tag: /tags/:name/


# HTML Compression
# - https://jch.penibelst.de/
compress_html:
  clippings: all
  ignore:
    envs: development


# Defaults
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      show_date: true
      layout: single
      author_profile: true
      read_time: true
      comments: true
      share: true
      related: true

  # _pages. # 이건 devinlife 보고 붙여넣기 한거
  - scope:
      path: ""
      type: pages
    values:
      layout: single
      author_profile: true
      read_time: false
      comments: false
      share: true
      related: false

~~~

 

#### 2. 제목, 링크, 강조색 바꾸기

/*sass/minimal-mistakes/skins/*(자신의스킨).scss

_default.scss 기반으로 추가된 부분은 아래와 같다. 참고로 _default.scss는 아무런 코드가 없다. 

~~~scss
$background-color: #fbfcfc !default; // 배경색 
$text-color: #000 !default; // 폰트색
$primary-color: #3d719b !default; // 주 컨셉 색깔(상단 메뉴바의 밑줄)
$footer-background-color:  #3d719b/* mix(#000, $background-color, 25%)*/ !default; // footer 색
$link-color: #3d719b !default; // 링크색(글 제목)
~~~



#### 3. 글자 크기 바꾸기

/_sass/minimal-mistakes/_reset.scss 수정

mmistakes는 사용자의 환경에 따른 유동적인 폰트 크기 환경을 지원하기 위해 breakpoint라는 개념을 사용한다.

~~~scss
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 14px;

  @include breakpoint($medium) {
    font-size: 16px;
  }

  @include breakpoint($large) {
    font-size: 16px;
  }

  @include breakpoint($x-large) {
    font-size: 16px;
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
~~~



#### 출처

- <https://honbabzone.com/jekyll/start-gitHubBlog/>
- <https://danggai.github.io/categories/#github-io>















