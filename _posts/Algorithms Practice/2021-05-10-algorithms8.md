---
title: "<8> 마구간에 말을 배치하자"
excerpt: "binary search"

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

# 1. 마구간 문제

이번에는 마구간의 갯수와 거리가 주어지고 말의 갯수가 주어진다. 이 말들을 모두 배치한다고 했을때 가장 서로의 거리가 멀게 배치하려면 얼마의 간격을 두고 배치해야하는가의 문제이다.

예를 들어서, 3마리의 말이 주어지고 마굿간은 `[1, 2, 4, 8, 9]` 의 간격으로 주어진다고 했을때 3의 간격으로 배치할때 가장 사이가 멀어지며 3마리의 말이 모두다 배치 가능하다.

# 2. 접근방법

접근 방법은 어떻게 해야할까?

- PeusdoCode
  - 우선 거리를 정하자. 그리고 마구간을 순회하면서 말을 그 거리에 맞게 배치해보는거다.
  - 첫번째 칸에 하나의 말이 들어가는건 확실하다. cnt = 1로 설정
  - 그리고 다시 다음칸으로 옮겨서 거리를 측정하고 거리가 같거나 넘으면 배치한다.
  - 최종적으로 다 순회를 하고 나서 cnt를 말의 갯수와 비교.
  - cnt가 주어진 말보다 많으면 거리를 늘린다. 즉 lt(시작점)를 오른쪽으로 이동(거리가 좁으니 더 촘촘하게 비교가능했던것이므로 거리를 좀 더 늘릴 필요가 있다.)
    - 그리고 distance를 answer에 저장한다
  - cnt가 더 적으면 거리를 좁힌다. 즉 rt(끝점)를 왼쪽으로 옮긴다
  - lt > rt 가 되면 중단하고 answer를 리턴한다.

```javascript
function stable(horses, stable) {
  stable.sort((a, b) => a - b);
  let lt = 1;
  let rt = stable[stable.length - 1];
  let distance;

  let answer;

  let cnt = 1;
  let lastHorsePos = 0;

  function countHorse(distance) {
    for (let i = 0; i < stable.length; i++) {
      if (stable[i] - stable[lastHorsePos] >= distance) {
        cnt++;
        lastHorsePos = i;
      }
    }

    lastHorsePos = 0;
  }

  while (lt <= rt) {
    distance = parseInt((lt + rt) / 2);
    countHorse(distance);

    if (cnt >= distance) {
      answer = distance;
      lt = distance + 1;
    } else {
      rt = distance - 1;
    }
    cnt = 1;
  }

  return answer;
}

// 3 ,[1, 2, 8, 4, 9] // 3
// 3, [1, 5, 7, 8, 15, 19, 23, 26] // 11
```
