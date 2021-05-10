---
title: "<9> 부분집합 (DFS)"
excerpt: "재귀함수"

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

# 1. 부분집합 구하기

이번엔 재귀를 사용해보려고 한다. 이번문제는 간단하다. N이라는 숫자를 넣었을때 N의 부분집합을 모두구하면 된다.
예를 들어 3을 투입했을때, 아래와 같은 집합이 부분집합들이다.

```javascript
1 2 3
1 2
1 3
1
2 3
2
3
```

# 2. 접근법

기본적으로 0,1을 어떤 배열에 넣고 최종적으로 1인것만 구별하여 경우의 수를 뽑아내는 방법을 써야한다. 로직을 보자.

- pseudoCode
  - dfs 라는 함수를 만들고 1을 num으로써 pass한다
  - `ch[num] = 1` 이라고 한다
  - 그리고 dfs(num+1)을 호출한다
  - num 이 N보다 클 경우 ch안에 1에 해당하는 index를 tempArr에 넣는다
  - tempArr answer에 push한다
  - dfs(num+1) 가 끝나면 `ch[num] = 0` 이라고 바꾼다
  - 다시 dfs(num+1) 호출한다.

그럼 코드를 적어보자.

```javascript
function subSet(n) {
  let ch = Array.from({ length: n }, () => 0);
  let tempArr;
  let answer;

  function dfs(num) {
    if (num > n) {
      for (let i = 0; i < ch.length; i++) {
        if (ch[i] === 1) {
          tempArr.push(i);
        }
      }
      if (tempArr.length > 0) answer.push(tempArr);
      tempArr = [];
    } else {
      ch[num] = 1;
      dfs(num + 1);
      ch[num] = 0;
      dfs(num + 1);
    }
  }
  dfs(1);

  return answer;
}
```

그럼 ch에 따라서 tempArr가 바뀌는 것을 알 수 있다.

![subSetCh](https://yeonghunko.github.io/assets/img/algorithms/subSetCh.png){:class="img-fluid"}
subSetCh

dfs트리를 그림으로 나타내면 아래와 같다.

![subset.png](https://yeonghunko.github.io/assets/img/algorithms/subset.png){:class="img-fluid"}
