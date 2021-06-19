---
title: "<37> 단속카메라 (프로그래머스 코딩테스트)"
excerpt: "탐욕법"

categories:
  - Algorithms Practice
tags:
  - greedy
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 단속 카메라

의외로 간단한 문제이다. 각 차량들의 진입 시점과 진출 시점이 담긴 array를 받자. 그리고 가장 차량이 많이 지나다니는 시점에 단속카메라를 설치해야하고, 모든 차량이 한번은 단속카메라의 범위에 들어와야한다고 하자. 이때, 설치되는 총 카메라 수를 리턴하면 된다.

예를 들어서 아래와 같이 정보가 주어진다고 하자.

```javascript
[
  [-20, -15],
  [-14, -5],
  [-18, -13],
  [-5, -3],
]; // 2
```

첫 번째 차량은 -20에 들어와서 -15에 나간다고 보면 된다. 이걸 그림으로 보면서 최적의 카메라 위치를 찾아보자.

![camera](https://yeonghunko.github.io/assets/img/algorithms/camera.png){:class="img-fluid"}

```javascript
[[-20,15], [-14,-5], [-18,-13], [-5,-3]]	2
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
