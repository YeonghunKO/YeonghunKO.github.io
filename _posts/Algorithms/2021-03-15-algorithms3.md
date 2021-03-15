---
title: "<3> 코딩테스트 (프로그래머스 코딩테스트-아이디 추천)"
excerpt: "replace"

categories:
  - Algorithms
tags:
  - regular expression
  - replace
  - slice
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. id 필터링

id가 들어오면 그 아이디를 여러 단계의 조건들을 통과하면서 다듬는 작업이다. 그 단계들은 이러하다.

**1.** new_id의 모든 대문자를 대응되는 소문자로 치환합니다.파일들 (css/js)을 받아온다.
{: .notice--success}

**2.** newid에서 알파벳 소문자, 숫자, 빼기(-), 밑줄(\_), 마침표(.)를 제외한 모든 문자를 제거합니다.
{: .notice--success}

**3.** new_id에서 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환합니다.
{: .notice--success}

**4.** new_id에서 마침표(.)가 처음이나 끝에 위치한다면 제거합니다.
{: .notice--success}

**5.** new_id가 빈 문자열이라면, new_id에 "a"를 대입합니다.
{: .notice--success}

**6.** new_id의 길이가 16자 이상이면, new_id의 첫 15개의 문자를 제외한 나머지 문자들을 모두 제거합니다.
{: .notice--success}

**6-1.** 만약 제거 후 마침표(.)가 new_id의 끝에 위치한다면 끝에 위치한 마침표(.) 문자를 제거합니다.
{: .notice--success}

**7.** new_id의 길이가 2자 이하라면, new_id의 마지막 문자를 new_id의 길이가 3이 될 때까지 반복해서 끝에 붙입니다.
{: .notice--success}

# 2. 구현

여기서 정규식(regular expression)이라는것을 배워야 한다. 정규식은 character의 패턴을 의미하는 일종의 공식인데 search/replace 같은 API와 같이 활용할 수 있다. 정규식 문법은 검색하면 쉽게 나오니깐 여기서 자세히 서술하지는 않겠다.

```javascript
function stageFour(newId) {
  if (newId[0] === ".") {
    newId = newId.slice(1);
  }

  if (newId[newId.length - 1] === ".") {
    newId = newId.slice(0, -1);
  }
  return newId;
}

function solution(new_id) {
  var stage2Reg = /[-_.\w]/gi;
  var stage3Reg = /\.\./g;

  // 1단계
  let newId = new_id.toLowerCase();

  // 2단계
  newId = newId.match(stage2Reg).join("");

  //3단계
  while (stage3Reg.test(newId)) {
    newId = newId.replace(stage3Reg, ".");
  }

  // 4단계
  newId = stageFour(newId);

  // 5단계
  if (newId === "") {
    newId = "a";
  }

  // 6단계
  if (newId.length >= 16) {
    newId = newId.slice(0, 15);
    newId = stageFour(newId);
  }

  // 7단계
  while (newId.length < 3) {
    newId += newId[newId.length - 1];
  }

  return newId;
}
solution(test1);
```

# 3. 쌈빡한 답안

역시나 고수분들이 계셨고 이번에도 많이 배웠다. 체이닝을 이용해서 매우 깔끔하게 코드한 분이 계셨다.

```javascript
function solution(new_id) {
  const answer = new_id
    .toLowerCase() // 1
    .replace(/[^\w-_.]/g, "") // 2단계: []안에거 제외한 모든 글자 ''로 치환
    .replace(/\.+/g, ".") // 3단계: ..2개이상 이어져있는거 .로 치환
    .replace(/^\.|\.$/g, "") // 4단계: 맨 앞 or 맨 뒤에 .있으면 ''로 치환
    .replace(/^$/, "a") // 5단계: 아무것도 없으면 'a' 로 치환
    .slice(0, 15) // 6단계: 글자 길이가 16자 이상이면,첫 15글자만 남기기.
    .replace(/\.$/, ""); // 6-1단계: 마지막에 .로 끝나면 ''로 치환
  const len = answer.length;
  // 7단계: 글자 수가 3이상이면 answer 그대로 리턴. 아니면 answer 마지막 글자를 (3-len) 만큼 반복해서 answer뒤에 붙여서 리턴
  return len > 2 ? answer : answer + answer.charAt(len - 1).repeat(3 - len);
}
```
