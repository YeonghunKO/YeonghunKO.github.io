---
title: "<6> 글자 최단거리 구하기"
excerpt: "생각의 전환"

categories:
  - Algorithms Practice
tags:
  -
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 최단거리

정말 뒤통수 딱 한대 얻어맞는 알고리즘이었다. 반대로 loop한다음에 더 작은값이 저장되도록 하다니... 박수...

s과 t를 넣은 다음 s의 각 글자가 t와 얼마나 떨어져있는지 알아보는 것이다. t사이에 글자가 있다면 가까운 t와 거리를 측정한다.

```javascript
function shortest(s, t) {
  let answer = [];
  let p = 1000;
  for (let x of s) {
    if (x === t) {
      p = 0;
      answer.push(p);
    } else {
      p++;
      answer.push(p);
    }
  }

  p = 1000;
  for (let i = s.length - 1; i >= 0; i--) {
    if (s[i] === t) {
      p = 0;
    } else {
      p++;
      answer[i] = Math.min(answer[i], p);
    }
  }
  return answer;
}
//  shortest('teachermode', 'e'); //  1 0 1 2 1 0 1 2 2 1 0
```

그림을 그려가면서 해보면 더 쉽게 알 수 있다.

![shortest.png](https://yeonghunko.github.io/assets/img/algorithms/shortest.png){:class="img-fluid"}
