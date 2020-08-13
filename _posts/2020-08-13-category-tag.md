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


![category1](https://yeonghunko.github.io/assets/img/github-blog-start/category1.png){:class="img-fluid"}

![category2](https://yeonghunko.github.io/assets/img/github-blog-start/category2.png){:class="img-fluid"}


