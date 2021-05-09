---
title: "<7> cache storage (프로그래머스 코딩테스트)"
excerpt: "컴퓨터야 일하자 일!"

categories:
  - Algorithms Practice
tags:
  - unshift
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. cache 일거리 저장

ram에다가 일거리를 저장한다. 차곡차곡 일이 저장된다. 그러다가 이미 저장된 일을 해야한다고 하면 그 일을 맨 처음으로 끌어온다.

아래 진행상태를 적어보겠다.

```javascript
일이 들어온 순서
[1,2,3,2,6]

캐시 메모리 상태 변화

10000

21000

32100

23100

62310
```

이런식으로 일거리가 들어오면 최종 ram을 리턴하면 된다.

어떻게 밀어넣으면 될까? unshift 라는 built-in을 사용해도 되지만 논리력을 끌어올리기 위해서 수동으로 할 필요도 있다.

어떻게 하면 될까? 바로 메모리 끝에서 부터 돌면서 각 숫자를 하나씩 뒤로 옮긴다음에 맨 처음에 칸에 일을 밀어넣으면 된다.

그리고 이미 있는 경우는 그 위치에서 시작해서 같은 작업을 하면 된다. 그럼 시작해보자.

```javascript
function cacheStorage(size, arr) {
  const answer = Array.from({ length: size }, () => 0);
  arr.forEach((x) => {
    let pos = -1;
    // 메모리안에 작업이 있는지 찾는 작업
    for (let i = 0; i < size; i++) {
      if (x === answer[i]) pos = i;
    }
    // 메모리 안에 작업이 없으면 맨 마지막에서 부터, 있으면 그 자리서 부터 한칸씩 뒤로 옮기기
    if (pos === -1) {
      for (let i = size.length - 1; i >= 1; i--) {
        answer[i] = answer[i - 1];
      }
    } else {
      for (let i = pos; i >= 1; i--) {
        answer[i] = answer[i - 1];
      }
    }

    // 다 옮겼으면 마지막 앞에 x를 갔다놓기
    answer[0] = x;
  });
  return answer;
}
```

크... 기분 좋은 작업이다. 명쾌하고 확실하다. 상자밖에서 생각해보자. 그리고 그림을 그려서 시각화하면 더 쉬워질거다.
