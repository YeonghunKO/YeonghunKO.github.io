---
title:  "댓글기능, TOC 추가"
excerpt: "댓글 utterances"

categories:
  - github
tags:
  - utterances
  - toc
last_modified_at: 2020-08-13T08:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

# Utterances 를 사용하기

<p>utterances 는 다른 댓글 서비스보다 가볍다. 그래서 사이트가 느려지는것을 어느정도 방지한다. 또한 마크다운 문법을 허용한다. 그래서 깃헙 사용자들에게 최적화된 댓글서비스가 아닌가 한다. 그리고 누군가 댓글을 입력했을때 그 정보를 내 메일로 보내주는 기능도 가지고 있다. 추가하는 방법은 매우 간단하다.</p>

## 1. 깃헙블로그에 utterances 전용 repository를 설치한다.

<p>리파지토리 이름을 YeonghunKO-comment 라고 정했다. 그리고 json.file을 하나 생성한다. 그라고 그 파일에 아래 코드를 추가한다.</p>

```json
// utterances.json    
{
  "origins": ["https://블로그 주소.github.io"]
}
```

## 2.utterances를 comment 리파지토리에 설치.

<p>아래 링크를 들어가서 설치하자.</p>

 [https://github.com/apps/utterances](https://github.com/apps/utterances) 

<p>그러곤 issue mapping에 각자 자신의 블로그 구조에 맞는 것을 선택하시면 됩니다.</p>

![utterances](https://yeonghunko.github.io/assets/img/github-blog-start/utterances-issue.png){:class="img-fluid"}

<p>그렇게 하고 원래라면 enable utteraces 안에 있는 코드를 복사하여 원하는 곳에 붙여넣기 하면 댓글 창이 뜨는데 minimal mistakes theme는 이미 utterances 기능을 제공하고 있다. config 파일로 들어가자.</p>

```bash
words_per_minute         : 200
comments:
  provider               : "utterances" # utterances를 입력
  disqus:
    shortname            : # https://help.disqus.com/customer/portal/articles/466208-what-s-a-shortname-
  discourse:
    server               : # https://meta.discourse.org/t/embedding-discourse-comments-via-javascript/31963 , e.g.: meta.discourse.org
  facebook:
    # https://developers.facebook.com/docs/plugins/comments
    appid                :
    num_posts            : # 5 (default)
    colorscheme          : # "light" (default), "dark"
  utterances:
    theme                : "github-light" #마음에 드는 테마를 입력
    issue_term           : "pathname" #pathname을 입력
```
<p>그리고 config 파일 아무데나 아래의 코드를 추가한다</p>

<code class="highlighter-rouge">repository: "YeonghunKO/YeonghunKO-comment" #utterances를 위한 리파지토리 주소를 입력.</code>

# TOC 추가

<p>minimal mistakes는 toc기능도 이미 제공하고 있다.</p>

<p>config파일 마지막에 default.value에 default 값으로 toc: true를 추가해주거나 글을 적을때 마다 YFM에 아래의 코드를 추가해주면 된다.</p>

```bash
# Defaults
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: false
      comments: true
      share: true
      related: true
      show_date: true
      toc: true
```

```yml
---
toc: true #TOC 기능 활성화
toc_label: "목차" #TOC 제목설정
toc_icon: "cog" #TOC테마 설정
toc_sticky: true #스크롤을 내릴때 TOC가 오른쪽에 붙어서 따라옴. 오른쪽 고정
---
```

<p>그럼 옆에 이런식으로 목차가 뜨고 스크롤을 내릴 때 그 위치에 있는 링크가 하이라이트 된다.</p>

![toc](https://yeonghunko.github.io/assets/img/github-blog-start/toc.png){:class="img-fluid"}

<p>그럼 다음엔 카테고리, 태그별로 글이 정리되는 기능을 알아보자.</p>