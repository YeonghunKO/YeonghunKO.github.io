---
title: "<1> Big O Notation"
excerpt: "Big O"

categories:
  - Algorithms and Data structures - Udemy
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

# 1. 알고리즘과 자료구조 배우기!

코딩 테스트를 준비하기 위해 기본적인 것만 배우려고 관련 강의를 찾다가 Udemy에서 좋은 강의를 찾았다. 영어로 가르치기 떄문에 관련 영어 표현도 익히고 영어도 공부해서 더 좋다.

알고리즘과 자료구조는 코딩 테스트 뿐만 아니라 성능을 최대한 잘 활용하면서 읽기 좋은 코드를 만들기 위해 꼭 배워야 한다고 항상 생각했었다. 그래서 이번에 제대로 배워보려 한다.
(메모, 관련 코드 예제는 깃헙에 다 올려놓았다.)

# 2. Big O

처음에 배우는 개념이 Big O이다. 한마디로 , 코드의 성능을 평가하는 단위라고 보면된다. 시간은 얼마나 잡아먹고 공간은 얼마나 차지하는지 나타내준다. 일종의 코드 표준 평가 기준이다. 정리한 내용을 적어보겠다.

- Definition: Big O notations varies according to how many operations inside function computer has to go through to yield final result.

-TIme complexity

1. o(1) : No matter how much n grows, it takes Num time.

2. o(n) : general trend for runtime is linear.

3. o(n square) : exponential 하게 시간이 걸림.(usually to nested loop)
   It is all about general trend for the time required for the final result. the trend is proportionate with n. and we simplify various equations down to just fuzzy level like above.
   So time-complexity wise, o(1) > o(n) > o(n square). In other words, avoid nested loops if possible

-Space complexity
It only counts how much variables are made through algorithms inside.

- Objects through lens of BigO
  :Insertion/removal/access = o(1) , searching = o(n)
  :Object.keys/values/entries = o(n) , hasOwnProperty = o(1)

- Array through lens of BigO
  :Insertion/removal = depends . Because If you insert or remove elements at the beginning of the array, Javascript will re-index every elements in the array which is not the case for doing the same job at the end.
  :Searching = o(n) , Access = o(1)

# 3. Graph of Big O

![bigOGraph](https://yeonghunko.github.io/assets/img/algorithms_Udemy/bigOGraph.png){:class="img-fluid"}
