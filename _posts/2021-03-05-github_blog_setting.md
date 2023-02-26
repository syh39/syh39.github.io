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

깃허브 페이지의 큰 부분들을 커스터마이징 하는 곳이라고 생각하면 된다. 주석으로 웬만한건 설명이 되어있기 때문에 직관적으로 필요한 부분을 고치면 된다. 

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

... etc ... 

~~~

 

#### 2. 제목, 링크, 강조색 바꾸기

/*sass/minimal-mistakes/skins/*(자신의스킨).scss

_default.scss 기반으로 추가된 부분은 아래와 같다. 참고로 _default.scss는 아무런 코드가 없다. 

~~~scss
$background-color: #fbfcfc !default; // 배경색 
$text-color: #000 !default; // 폰트색
$primary-color: #3d719b !default; // 주 컨셉 색깔(상단 메뉴바의 밑줄, 목차 등)
$footer-background-color:  #3d719b/* mix(#000, $background-color, 25%)*/ !default; // footer 색
$link-color: #3d719b !default; // 링크색(글 제목)
~~~



#### 3. 글자 크기 바꾸기

/_sass/minimal-mistakes/_reset.scss 수정

mmistakes는 사용자의 환경에 따른 유동적인 폰트 크기 환경을 지원하기 위해 breakpoint라는 개념을 사용한다.

이 블로그의 경우 폰 화면에서는 14px, 테블릿이나 PC 화면에서는 16px로 보이도록 수정했다. 

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



#### 4. 좌우 사이드 비율 수정

/sass/minimal-mistakes/_variables.scss 수정

처음의 default값은 중간에 내용이 들어가는 영역이 너무 좁아서 비효율적으로 느껴져서 내용이 들어가는 영역을 늘리고자 코드를 수정하였다. 이게 왼쪽과 오른쪽이 동시에 수정이 되는 부분이라 화면이 narrow인 경우를 제외하고 각각 30px과 50px만 줄였는데 확 넓어진게 느껴졌다. 게시물 글이 들어가는 부분이 더 넓어지고 왼쪽(프로필 사진과 상태메세지 등)과 오른쪽(목차)의 넓이가 줄어들어서 내용 영역에 더 많은 내용을 넣을 수 있고 내용을 중점적으로 부각시킬 수 있게 되어서 블로그로서의 기능을 더 충실하게 할 수 있게 된 것 같다. 

~~~scss
$right-sidebar-width-narrow: 200px !default;
$right-sidebar-width: 270px !default;
$right-sidebar-width-wide: 350px !default;

// $right-sidebar-width-narrow: 200px !default;
// $right-sidebar-width: 300px !default;
// $right-sidebar-width-wide: 400px !default;
// 원래 코드 - 사이드 여백 너무 많아서 수정
~~~



#### 5. 상단 네비게이션 바 목록 수정

/_data/navigation.yml 이동

목록은 여기서 수정한다. 

url의 경우 /_pages/ 안에 여러 파일들의 permalink의 값을 넣으면 된다. 

~~~yaml
# main links
main:
  - title: "Home"   # 보여지는 이름 
    url: https://syh39.github.io/ # 이동하는 url
  - title: "Category"
    url: /categories/
  - title: "Tag"
    url: /tags/
  - title: "Posts"
    url: /year-archive/
    

  # - title: "Quick-Start Guide"
  #   url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  # - title: "About"
  #   url: https://mmistakes.github.io/minimal-mistakes/about/
~~~



#### 6. 상단 네비게이션 바 디자인 수정

/_sass/minimal-mistakes/_masthead.scss 수정

상단 네비게이션 바의 글씨 굵기, 크기, 여백 등을 수정할 수 있다. 

~~~scss
font-size: $type-size-3; // 폰트 사이즈 4 -> 5으로 수정(더 작게)
// font-weight: bold;    // 폰트 굵기 굵게 -> 평범하게로 수정
~~~



#### 7. 프로필사진 디자인 수정

/_sass/minimal-mistakes/sidebar.scss 수정

프로필사진의 CSS를 수정할 수 있다. 

~~~scss
.author__avatar {
  display: table-cell;
  vertical-align: top;
  width: 30px;// 36px;   / 프로필사진 넓이
  height: 30px;// 36px;  / 프로필사진 높이

  @include breakpoint($large) {
    display: block;
    width: auto;
    height: auto;
  }

  img {
    // max-width: 110px;
    max-width: 150px;
    border-radius: 30%;  // 50%인 경우 원이 된고 0%인 경우 사각형이 된다

    @include breakpoint($large) {
      // padding: 5px;
      // border: 1px solid $border-color;
      padding: 3px;                     // border 와의 거리 
      border: 2px solid $border-color;  // border 속성
    }
  }
}
~~~



#### 8. 파비콘 수정하기 

- [참고링크](https://danggai.github.io/github.io/Github.io-%ED%8C%8C%EB%B9%84%EC%BD%98-%EC%88%98%EC%A0%95%ED%95%98%EA%B8%B0/)



### 출처

- <https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/>
- <https://honbabzone.com/jekyll/start-gitHubBlog/>
- <https://danggai.github.io/categories/#github-io>















