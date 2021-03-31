---
title: "<4> 재귀함수"
excerpt: "Recursion"

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

# 1. Recursion basic part

재귀함수는 함수안에 또 자신과 같은 함수가 있는것을 말한다. 재귀 함수의 특징은 재귀를 멈추는 조건문이 있어야 하고, 재귀 함수 안에 들어갈 인자가 달라야 한다는 것이다. 맨처음엔 다소 생소하지만 언제나 그렇듯 계속 마주치면 익숙해진다.

**Essential Parts**

- Base Case: the condition when the recursion ends. This is the most important concept to understand.

- Different input.

1. Where things go wrong

- Obviously No base case

- Forgetting to return or returning the wrong thing

->> Stack Overflow!!

- Helper: This is a common pattern when we are trying to compile some sort of result usually in an array or some other sort of data structure along those lines.

**Pure Recursion Tip**

- For arrays, use methods like slice, the spread operator , and concat that make copies of arrays so you do not mutate them.

- For strings, they are immutable so you will need to use methods like slice, substr.

- For objs , You can use Obj.assign or the spread operator.
