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

<p>이번에는 블로그 상단에 "post by category" 라고 뜨게 한 다음 그 글을 클릭해서 들어가면 카테고리가 나오도록 해보겠다. 그 카테고리에 해당하는 글이 밑에 간략하게 디스플레이 되도록 설정하는 것이다. 우선 그럼 카테고리 archive를 만들어야 한다.</p>

<p>먼저 config 파일에 들어간다. 그리고 category-archive 코드가 주석해제되었는지 확인한다.</p>

```bash
category_archive:
  type: liquid
  path: /categories/
tag_archive:
  type: liquid
  path: /tags/
```

그리고 _pages이름의 폴더를 만든다음 안에 category-archive.md 파일을 만들어준다. 그리고 파일안에 아래의 코드를 추가한다.

```yml
---
title: "Posts by Category"
layout: categories #카테고리별로 글이 나열되도록 설정
permalink: /categories/ #내부링크를 categories라고 설정. 그럼 url : /categories/ 이라고 설정하면 이 페이지로 이동하게끔 내부링크를 설정했다. 
author_profile: true
---
```

그러고 data폴더에 navigaion.yml 파일에 들어가면 네비게이션 메뉴를 확인 할 수 있다. 아래의 코드를 추가하자. 

```bash
- title: "post by categories"
    url: /categories/
```

그럼 블로그 상단 메뉴에 아래그림과 같이 post by categories 메뉴가 추가되어있고 들어가면 카테고리별로 글이 정리되어있는 모습을 볼 수 있다.


![category1](https://yeonghunko.github.io/assets/img/github-blog-start/category1.png){:class="img-fluid"}

![category2](https://yeonghunko.github.io/assets/img/github-blog-start/category2.png){:class="img-fluid"}

# 2.태그별로 글 정리
<p>사실 태그도 마찬가지다. 카테고리 만들때 처럼 pages폴더에 tag-archive.md 파일 추가한다. 그리고 아래의 코드를 입력한다.</p>

```yml
---
title: "Posts by Category"
layout: tags #태그별로 글이 나열되도록 하는 기능
permalink: /tags/ 
author_profile: true 
```

그런다음 navigation 파일에 들어가 tags 메뉴를 추가해주면 된다.

* P.S : 년도별로 글이 정리되게끔 하려면 pages 폴더에 year-archive.md를 만들고 아래의 코드를 추가한다음 navigation에 메뉴를 추가한다.

```bash
---
title: "Posts by Year"
permalink: /year-archive/
layout: posts #년도별로 글이 나열되게끔 함.
author_profile: true
---
```