---
title: "<29> 네트워크 (프로그래머스 코딩테스트)"
excerpt: "dfs"

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

# 1. 네트워크

이번엔 나름 신선한 문제이다. 컴퓨터가 주어져있는데 서로 연결된 컴퓨터를 찾으면 된다. 일단 서로 연결되어있는 컴퓨터끼리는 같은 네트워크를 공유하므로 네트워크가 1개 생겼다고 보면된다. 예를 들어서, 아래와 같은 배열이 주어졌다고 생각해보자.

```javascript
let n = 3;

let computers = [
  [1, 1, 0],
  [1, 1, 0],
  [0, 0, 1],
];
```

이때 컴퓨터의 갯수는 3대이다. 첫번째 컴퓨터를 보면 자기 자신과 두번째 컴퓨터가 연결되어있고 두번째 컴퓨터도 첫번째 컴퓨터와 자기 자신과 연결되어있다.(참고로, 항상 자기 자신은 자기 자신과 연결되어있을 수 밖에 없다) 그런데 세번째 컴퓨터는 자기 자신이외에 아무도 연결되어있지 않다.(외롭다..ㅋㅋㅋㅋㅋ) 그러므로 네트워크 갯수는 2개를 출력하면 된다. 그림으로 나타내면 아래와 같다.

![network1.png](https://yeonghunko.github.io/assets/img/algorithms/network1.png){:class="img-fluid"}

그럼 dfs를 이용해서 한 번 구현해보자!

# 2. 접근 방법

사실 혼자서 한 시간정도 고민해보았지만 도저히 어떻게 접근해야할지도 몰라서 다른분들의 풀이를 보았다. 이윽고 나의 부랄을 치고 깨달음을 얻었다 ㅋㅋㅋㅋㅋㅋ

- pseudo code
  - visited array를 만들어 방문한 컴퓨터를 체크한다.
  - dfs를 만든다.
  - 각각의 컴퓨터를 dfs안에 pass한다.
    - 방문한 컴퓨터를 visted에 마크한다
    - 각각의 컴퓨터에 들어가서 연결되어있는 컴퓨터를 체크한다.
    - 연결되어있으면 연결되어있는 컴퓨터에 또 다시 들어가서 다른 컴퓨터와의 연결여부를 확인한다.

```javascript
function solution1(n, computers) {
  let answer = 0;
  let isVisited = [];

  for (let i = 0; i < n; i++) {
    isVisited.push(false);
  }

  let DFS = function (computers, i) {
    console.log("DFS executed");
    if (isVisited[i]) return;
    isVisited[i] = true;

    // 방문한 컴퓨터에 들어가서 다른 컴퓨터와 연결되어있는지 본다. 연결되어있으면 그 컴퓨터에 또다시 들어가서 연결되어있는 또 다른 컴퓨터를 찾아낸다.
    for (let c = 0; c < computers.length; c++) {
      if (computers[i][c] === 1) {
        console.log(i + ", " + j);
        console.log("connected");
        DFS(computers, c);
      }
    }
  };

  for (let j = 0; j < n; j++) {
    answer++;
    console.log(isVisted, "도입부");
    console.log(`${answer} network`);
    DFS(computers, i);
  }
}
```

그러고 출력을 해서 보자.

```javascript
(3) [false, false, false] "도입부"
1 network

DFS excuted
(3) [true, false, false]
0, 0
connected

DFS excuted
0, 1
connected

DFS excuted
(3) [true, true, false]
1, 0
connected

DFS excuted
1, 1
connected

DFS excuted
(3) [true, true, false] "도입부"
2 network

DFS excuted
(3) [true, true, true]
2, 2
connected

DFS excuted
(3) [true, true, true]

=> 2
```

요런식으로 진행이 된다는거 알아두면 이득이다. 참 간결하고 보기좋다. 그럼 다른 사람의 코드 하나만 더 보자!

```javascript
let visitArr;

function otherSolution(n, computers) {
  let network = 0;
  visitArr = new Array(n).fill(false);

  for (let i in computers) {
    network += dfs(i);
  }

  function dfs(i) {
    if (visitArr[i] === true) return 0;
    else visitArr[i] = true;

    for (let j in computers[i]) {
      if (computers[i][j] === 1) dfs(j);
    }

    return 1;
  }
  return network;
}
```

위의 코드보다 가독성이 더 좋은것 같다. 그리고 dfs에 리턴값을 주고 ctr에 추가해나가는게 인상깊다. 그럼 두 코드를 융합해서 내 나름대로 코드를 또 짜보았다.

```javascript
function mySolution(n, computers) {
  let answer = 0;
  let isVisted = Array(n).fill(false);

  function DFS(i) {
    console.log("dfs executed");
    if (isVisited[i]) return 0;
    else isVisted[i] = true;

    console.log(isVisited);

    for (let j in computers[i]) {
      if (computers[i][j] === 1) {
        console.log(`${i} ${j} connected`);
        DFS(j);
      }
    }

    return 1;
  }

  for (let i = 0; i < n; i++) {
    if (!isVisted[i]) {
      answer += DFS(i);
      console.log(`${answer} network`);
    }
  }

  return answer;
}
```

크.... 나름 두개의 코드를 이해하고 내 나름대로 코드를 짜보았다. 진짜 배웠다!!

# 3. 배운점

1. 나는 글을 적을때 생각이 정리되는 편이니 이런식으로 글을 적으면서 파편적으로 흩어진 문제의 퍼즐을 정리하자. 그래서, 문제에 대한 이해도를 높이자!!
