---
title: "<35> 가장 큰 수 (프로그래머스 코딩테스트)"
excerpt: "탐욕법"

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

# 1. 가장 큰 수 구하기

바로 예시를 통해서 배워보자.

```javascript
  number      k    return 값
"1924"	      2	   // 94
"1231234"	    3	   // 3324
"4177252841"  4    // 775841
```

이렇게 정보가 주어졌을때 k만큼 number에서 숫자를 제외하고 나머지 숫자의 갯수들로 숫자를 조합한다고 했을때, 만들어 질 수 있는 숫자중 가장 큰 수를 리턴하면 된다. 그럼 return 값 처럼 결과가 출력된다.

# 2. 접근 방법

우선 조합이 가장 먼저 떠올랐다. k만큼 제외한 숫자들을 조합으로 만든다음 그중에 가장 큰수를 max를 이용해서 뽑아내면 되는 거다.

```javascript
x = 2;
x = x + 2;
print(x);
```

![getcombination1](https://yeonghunko.github.io/assets/img/algorithms/getcombination1.jpg){:class="img-fluid"}

![getcombination2](https://yeonghunko.github.io/assets/img/algorithms/getcombination2.jpg){:class="img-fluid"}

![biggest](https://yeonghunko.github.io/assets/img/algorithms/biggest.jpg){:class="img-fluid"}

```javascript
x = 2;
x = x + 2;
print(x);
```

```javascript
x = 2;
x = x + 2;
print(x);
```

```html
x = 2 x = x + 2 print(x)
```

```css
x = 2
x = x + 2
print(x)
```

## Week 3 영어문장 정리

- So like I said, you can do interactive in Python or you can run a script.(Interactive: You type directly to python one line at a time and it responds.)

- And you'll notice that this is indented at the same level as the print statement.

![shortest.png](https://yeonghunko.github.io/assets/img/algorithms/shortest.png){:class="img-fluid"}
