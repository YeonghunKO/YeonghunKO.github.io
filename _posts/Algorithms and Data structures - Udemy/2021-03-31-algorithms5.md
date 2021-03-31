---
title: "<5> 재귀함수 예시 "
excerpt: "helper"

categories:
  - Algorithms and Data structures - Udemy
tags:
  - palinedrome
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 간단한 재귀함수

먼저 간단하게 팩토리얼을 구하는 함수부터 만들어 보자.

```javascript
factorial(1); // 1
factorial(2); // 2

function factorial(num) {
  if (num === 0) return 1;
  return num * factorial(num - 1);
}
```

if 문이 base case이고 num-1이 다른 인자를 입력하는 것이다. 좀더 복잡한 재귀함수를 살펴보자.

# 2. 복잡한 재귀함수

아래는 펠린드롬 함수이다. 앞뒤 어느쪽으로 읽어도 발음이 같은 단어를 뜻한다.

```javascript
//   isPalindrome('awesome'); // false

function isPalindrome(str) {
  if (str.length === 1) {
    console.log(true);
    return true;
  }
  if (str[0] === str[str.length - 1]) {
    let newString = str.slice(1).slice(0, -1);
    //   console.log(newString);
    isPalindrome(newString);
  } else {
    console.log(false);
    return false;
  }
}

// 맨앞 맨뒤를 제거
// 마지막에 남은 str의 갯수가 1개면 true 아니면 false
```

# 3. helper가 있는 재귀함수

그 전 글에서도 설명했지만 어떤 데이터를 컴파일 하기위해서 helper 함수안에 helper함수를 넣는걸 뜻한다.

홀수만 모아서 출력하는 함수이다.

```javascript
function collectOddValues(arr) {
  let result = [];

  function helper(helperInput) {
    if (helperInput.length === 0) {
      return;
    }

    if (helperInput[0] % 2 !== 0) {
      result.push(helperInput[0]);
    }

    helper(helperInput.slice(1));
  }

  helper(arr);

  return result;
}

collectOddValues([1, 2, 3, 4, 5, 6, 7, 8, 9]);
```

helper를통해서 arr안에 홀수만 컴파일하게 된다. 이로써 재귀함수에 대해서 어느정도 감이 생겼다. 그럼 다음엔 정렬 함수에 대해 알아보도록 하자.
