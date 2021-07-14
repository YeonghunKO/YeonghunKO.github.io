---
title: "<47> 닉네임 (프로그래머스 코딩테스트)"
excerpt: "해쉬"

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

# 1. 닉네임

유저아이디와 그에 해당되는 닉네임을 가지고 채팅방에 들어오고 나가고 닉네임을 변경한 히스토리가 pass될것이다 그럼 그 히스토리를 보고 그 유저아이디에 해당되는 닉네임을 return하면 된다.

예를 들어 보자

```javascript
let history = [
  "Enter uid1234 Muzi",
  "Enter uid4567 Prodo",
  "Leave uid1234",
  "Enter uid1234 Prodo",
  "Change uid4567 Ryan",
];

let result = [
  "Prodo님이 들어왔습니다.",
  "Ryan님이 들어왔습니다.",
  "Prodo님이 나갔습니다.",
  "Prodo님이 들어왔습니다.",
];
```

history를 보면 유저아이디가 uid1234는 최종적으로는 닉네임이 Prodo인것을 알수 있고 유저아이디가 uid4567이면 닉네임이 최종적으로는 Ryan인것을 알 수 있다.

그래서 result에 저렇게 리턴이 되는 것이다.

그럼 코드를 짜러 가볼까?

# 2. 접근방법

- pseudo code

- 닉네임과 아이디를 저장하기 위한 obj를 만듬.
- enter과 leave를 구분(change는 표시하지 않음. 다만 해당 아이디에 따른 닉네임 변경사항만 저장)(split(' ')을 써볼 것).
- record를 돌면서 최종적으로 아이디에 따른 닉네임을 저장.
- 다시 record를 돌면서 아이디에 따라서 닉네임을 구분.
- leave냐 enter에 따라서 서술어를 달리하여 answer에 push 함.

딱, 적당하고 직관적인 방법이다. 그럼 구현을 해보자!

```javascript
function solution1(history) {
  let answer = [];
  let nickName = {};

  for (let i = 0; i < history.length; i++) {
    let subArr = history[i].split(" ");
    if (subArr[0] === "Leave") continue;

    // 최종 닉네임을 해당 아이디에 저장
    nickName[subArr[1]]
      ? (nickName[subArr[1]] = subArr[2])
      : (nickName[subArr[1]] = subArr[2]);
  }

  for (let i = 0; i < history.length; i++) {
    let subArr = history[i].split(" ");
    if (subArr[0] === "Enter")
      answer.push(`${nickName[subArr[1]]}님이 들어왔습니다.`);
    if (subArr[0] === "Leave")
      answer.push(`${nickName[subArr[1]]}님이 나갔습니다.`);
  }

  return answer;
}

// 헉... level2를 이렇게 쉽게 통과하다니... 그것도 이런 상황속에서 멘탈 붙잡으면서...
// 진짜 눈물날 정도로 나의 노력과 상황과 하나님께 감동함...
```

근데 더 좀더 쌈빡한 방법으로 구현한 사람이 있다.

```javascript
function solution2(history) {
  const userInfo = {};
  const action = [];
  const stateMapping = {
    Enter: "님이 들어왔습니다.",
    Levae: "님이 나갔습니다.",
  };

  record.forEach((v) => {
    const [state, id, nick] = v.split(" ");

    if (state !== "Change") action.push([state, id]);

    if (nick) userInfo[id] = nick;
  });

  // 아래 map 에서 parameter를 []로 묶은 이유.
  // map안에 있는 원소 ['Enter','uid1234'] 를 state와 uid 변수에 각각 할당했다는 의미이다. 근데 저걸 []에 담지 않고 (state,uid) 라고 해버리면 state = array , uid = index 로 저장되어 처리된다.

  return action.map(([state, uid]) => {
    return `${userInfo[uid]}${stateMapping[state]}`;
  });
  // 위의 map을 아래와 같이 표시할 수 도 있다
  // action.map(state => {
  //   const state = state[0]
  //   const uid = state[1]
  // })
}
```

# 3. 배운점

- parameter를 `[a,b]` 로 두면 a,b에 할당되는 것을 배움
- const `[a,b,c]` = 어쩌고 라고 하면 a,b,c에 한꺼번에 할당할 수 있다는 것도 배움
