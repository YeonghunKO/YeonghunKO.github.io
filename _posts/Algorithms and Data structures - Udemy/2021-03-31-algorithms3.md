---
title: "<3> Problem Solving Pattern - different solutions"
excerpt: "목적지로 향하는 길은 여러가지"

categories:
  - Algorithms and Data structures - Udemy
tags:
  - multi pointer
  - sliding windows
  - divide and conquer
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. Multi pointer

값을 tracking할때 변수를 두가지 이상 사용하는 것을 뜻한다. 몇가지 종류의 숫자가 있는지 구하는 함수를 만들어보자

```javascript
function countUniqueValues2(arr) {
  if (arr.length === 0) return 0;
  var i = 0;
  var j = 1;
  while (j < arr.length) {
    if (arr[i] !== arr[j]) {
      i++;
      arr[i] = arr[j];
    }
    j++;
  }
  return i + 1;
}

// for loop으로도 할 수 있다. 근데 while연습한다고 while 로 적어봤다.
// 포인터 i / j 가 왼쪽에서 부터 시작해서 오른쪽으로 간다.
countUniqueValues2([-1, -3, -3, 0, 6, 7, 8, 8]);

// [-1, -3, 0, 0, 6, 7, 8, 8]
//   i   j

// i = 0
// j = 1
```

i, j가 왼쪽으로 이동한다. 이동하면서 숫자가 같으면 i를 한칸 오른쪽으로 옮긴후에 j로 바꾼다. 그리고 j를 오른쪽으로 한칸 옮기고 비교를 계속한다. 일종의 손가락 두개를 짚어가면서 비교한다고 보면된다. 요런식으로 문제를 해결 할 수 있다.

# 2. Sliding window

창문을 열듯이 data 의 하위부분을 들여다 본다. 하위부분을 커버하는 scope의 크기가 일종의 창문의 크기이다. 창문을 많이 열면 그만큼 scope의 범위도 넓어진다. 그럼 아래 하위 data 의 합 중 가장 큰 합을 뽑아내는 함수를 보도록 하자.

```javascript
function maxSubArraySum(arr, num) {
  let tempMax = 0;
  let finalMax = 0;
  if (arr.length < num) return null;
  for (var m = 0; m < num; m++) {
    tempMax = tempMax + arr[m];
  }

  finalMax = tempMax;
  console.log(tempMax, finalMax);
  for (var m = 0; m < arr.length - num; m++) {
    // 오른쪽으로 창문이 이동한다. 정확히 말하면 왼쪽은 한 칸 줄어들고 오른쪽은 한 칸 늘어난다(num이 2일경우에)
    tempMax = tempMax - arr[m] + arr[m + num];
    // 창문을 이동시키면서 새로 갱신된 TEMP와 FINAL을 비교한다
    finalMax = Math.max(tempMax, finalMax);
    console.log(tempMax, finalMax);
  }
}

maxSubArraySum([2, 3, 4, 5, 1, 2, 3, 4, 5, 2, 5, 6, 3, 2, 3, 4, 2], 2);
```

# 3. Divide and Conquer

"나누어서 정복하라" 모든것을 샅샅이 파헤쳐서 정복하지 말고 구간을 나누고 한번에 정복하라는 말이다. 대표적인게 이진 검색이 있다. ARRAY안에서 2라는 숫자를 찾는다고 하자. 이때 ARRAY의 처음부터 끝까지 다 훑는 경우도 있지만(linear search) 속된말로 무식한 방법이다.

ARRAY를 반으로 나누는 수를 정하고 그 숫자보다 2가 작으면 다시 왼쪽 부분을 반으로 나누고 크면 오른쪽 부분을 반으로 나누는 방법이다. 차근차근 야금야금 점령해 나간다. linear search 보다 시간이 훨씬 덜 걸릴 수 있다.

참고로 binary search는 arr가 정렬되어있어야 한다.

```javascript
function binarySearch(arr, val) {
  // 3개의 포인터를 가진다. 처음, 중간, 끝
  let mid = Math.ceil(arr.length / 2);
  let start = 0;
  let end = arr.length - 1;
  let result = -1;

  while (start <= end) {
    if (arr[mid] === val) {
      result = mid;
      break;
    } else if (arr[mid] > val) {
      end = mid - 1;
      mid = Math.ceil((start + end) / 2);
    } else {
      start = mid + 1;
      mid = Math.ceil((start + end) / 2);
    }
  }
  // mid +-1하는 이유:이미 mid 변경하기전에 mid는 이미 check 되었으므로 제외하기 위해 더하거나 빼는것이다
  return result;
}
binarySearch([1, 2, 4, 5, 6, 7, 8, 9, 12, 13, 16, 25, 36, 47, 58, 78], 4);
```

어떻게 보면 window를 좁혀나가는 것일 수도 있겠다. while의 조건과 end , start포인트를 잘 설정하도록 하자.

이로서 문제 접근 방법과 해결 방법을 살펴보았다. 다음은 재귀함수에 대해서 배워보도록 하자.
