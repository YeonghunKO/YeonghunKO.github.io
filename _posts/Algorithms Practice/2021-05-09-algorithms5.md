---
title: "<5> 격자판 최대합 (인프런 알고리즘)"
excerpt: "Array 가로 세로 대각선 루프"

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

# 1. 격자판의 합

격자판이 주어지면 가로로 더한 값 세로로 더한값 대각선으로 더한 값중에 최대값을 찾는 문제이다. 루프를 도는건 어렵지 않지만 동시에 가로와 세로의 값을 더하는게 관건이다.

나같은 경우는 격자를 아예 새로 수정해서 더했는데 선생님의 방법은 동시에 구하는 것이었다.

```javascript
let arr = [
  [10, 13, 10, 12, 15],
  [12, 39, 30, 23, 11],
  [11, 25, 50, 53, 15],
  [19, 27, 29, 37, 27],
  [19, 13, 30, 13, 19],
];
```

위와 같은 격자의 최대합을 구하는 것이다.

```javascript
function maxSum(arr) {
  let answer = Number.MIN_SAFE_INTEGER;
  let n = arr.length;
  let sum1 = (sum2 = 0);

  // 가로 세로의 합을 구하고 비교를 통해 최대값 추출
  for (let i = 0; i < n; i++) {
    sum1 = sum2 = 0;
    for (let j = 0; j < n; j++) {
      sum1 += arr[i][j];
      sum2 += arr[j][i];
    }
  }

  answer = Math.max(answer, sum1, sum2);

  // 대각선의 합을 구하고 비교를 통해 최대값 추출
  for (let i = 0; i < n; i++) {
    sum1 = arr[i][i];
    sum2 = arr[i][n - i - 1];
  }

  answer = Math.max(answer, sum1, sum2);
  return answer;
}
```
