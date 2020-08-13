---
title:  "카테고리, 태그별로 글 정리"
excerpt: "카테고리, 태그"

categories:
  - github
tags:
  - 카테고리
  - 태그
  - 
last_modified_at: 2020-08-13T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

# 1. Category 별로 글 정리

<p>마크다운 문법을 사용해서 글을 적으면 글 상단에 y이번에는 블로그 상단에 "post by category" 라고 뜨게 한 다음 그 글을 클릭해서 들어가면 카테고리가 나오도록 해보겠다. 그 카테고리에 해당하는 글이 밑에 간략하게 디스플레이 되도록 설정하는 것이다. 우선 그럼 카테고리 archive를 만들어야 한다.</p>

<p>먼저 config 파일에 들어간다. 그리고 category-archive 코드가 주석해제되었는지 확인한다.</p>

```bash
category_archive:
  type: liquid
  path: /categories/
tag_archive:
  type: liquid
  path: /tags/
```

<p>그런 다음 _pages 라는 폴더를 블로그 폴더안에 만들고 pages 폴더 안에 category-archive.md 라는 폴더를 만든다. 그래서 navigation.yml에서 category-archive 폴더로 permalink 가 걸리게 끔 하는 작업이다.(나중에 다시 설명할테니 지금은 무슨 말인지 몰라도 된다.)</p>

<p> category archive 파일에 들어가서 YFM 란에 아래의 코드를 추가해준다</p>

```yml
---
title: "Posts by Category"
layout: categories #카테고리별로 글이 나열되도록 하는 기능
permalink: /categories/ #내부링크를 categories로 설정. 그래서 다음부터 url: /categories/라고 하면 이 파일이 열리도록 세팅해놓는 것이다.
author_profile: true #왼쪽에 주인장의 프로필이 고정되도록 하는 기능. 이 기능은 config.default 에도 추가되어있다.
---
```

<p>그리고 data폴더 navigation.yml 파일에 들어간다. 그럼 아래와 같은 코드가 나온다</p>

```yml
# main links
main:
  # - title: "Quick-Start Guide"
  #   url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
  - title: "About me"
    url: /about/
  - title: "post by categories"
    url: /categories/
  - title: "post by year"
    url: /year-archive/
  - title: "post by tag"
    url: /tags/
```

<p>여기서 title에 post by categories 라고 해주고 그 밑에 url 을 /categories/ 라고 지정해준다. </p>


<p>그럼 아래와 같이 블로그에 네비게이션 메뉴에 post by category 가 추가된 것을 볼 수 있다.</p>

![category1](https://yeonghunko.github.io/assets/img/github-blog-start/category1.png){:class="img-fluid"}

![category2](https://yeonghunko.github.io/assets/img/github-blog-start/category2.png){:class="img-fluid"}


# 2.태그별로 글 정리
<p>사실 태그도 마찬가지다. 카테고리 만들때 처럼 page폴더에 tag-archive.md 파일 추가한다. 그리고 아래의 코드를 입력한다</p>

```yml
---
title: "Posts by Category"
layout: tags #태그별로 글이 나열되도록 하는 기능
permalink: /tags/ 
author_profile: true 
```

<p>그리고 navigation.yml 파일에 post by tags 를 추가하고 url에다 /tags/를 지정하면 끝!</p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>



