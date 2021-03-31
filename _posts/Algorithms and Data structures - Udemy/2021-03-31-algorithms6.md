---
title: "<6> 정렬 알고리즘"
excerpt: "sorting"

categories:
  - Algorithms and Data structures - Udemy
tags:
  - bubble
  - merge
  - quick
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 정렬 알고리즘

무작위로 담겨있는 데이터를 어떤 기준에 의해서 정렬해주는 알고리즘을 말한다. bubble, selection, insertion, merge, quick 등 정말 많은 방법으로 정렬가능하다. 다 설명할 수 는 없고 내가 생각했을때 재밌고 유용하다는 알고리즘만 설명하겠다. 그리고 정렬 알고리즘의 과정을 시각화 시켜놓은 유용한 사이트가 있다.

`visulgo` 라는 사이트인데 한 번 가서 가지고 놀아보는 것도 좋다.

[visualgo](https://visualgo.net/en)

# 2. bubble 정렬

- A sorting algorithm where the largest values bubble up to the top. like by comparing two elements.

-- Time complexity

- Best: O(n) / Average: O(n2) / Worst: O(n2)

-- Space complexity: O(1)

가장 큰수가 떠오르는 것처럼 가장 뒤로 위치하게 된다.

```javascript
function bubbleSort(arr) {
  var noSwaps;
  for (var i = arr.length; i > 0; i--) {
    noSwaps = true;
    for (var j = 0; j < i - 1; j++) {
      // swap!
      console.log(arr, arr[j], arr[j + 1]);
      if (arr[j] > arr[j + 1]) {
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
        noSwaps = false;
        console.log("Swap");
      }
    }
    console.log("one loop pass through");
    if (noSwaps) break;
  }
  return arr;
}
// console.log(bubbleSort([2, 3, 41, 5, 2, 34, -1]));
console.log(bubbleSort([28, 1, 2, 5, 7, 34, 69]));
// if every elements are sorted , you don't need to compare again. then you can finish the loop
```

# 2. Merge 알고리즘

arr를 둘로 나눈다 길이가 1 이 될때까지. 그리고 왼쪽과 오른쪽을 정렬해서 합친다. 그리고 helper 함수를 따로 정의해서 사용하고 있다.

-- Grand scheme of merge sort

1. It’s a combination of two things - merging and sorting!

2. Exploits the fact that arrays of 0 or 1 elements are always sorted.

3. Works by decomposing an array into smaller arrays of 0 or 1 elements, then building up a newly sorted array

-- prepared action

1. In order to implement merge sort, it’s useful to first implement a function responsible for merging two sorted arrays.

2. Given two arrays which is also sorted, and consists of all of the elements in the two input arrays.

**Pseudocode. Let’s dive in!**

1. Create an empty array, take a look at the smallest values in each input array.

2. While there are still values we haven’t looked at

-- if the value in the first array is smaller than the value in the second array, push the value of the first array into our results and move on to the next in the first array.

- if the value in the first array is larger than the value in the second array, push the value of the second array into our results and move on to the next value in the second array.

- Once we exhaust one array, push in all remaining values from the other array.

-- Time complexity

-Best/Average/Worst: O(n log n)

-- Space complexity: O(n)

```javascript
function merge(arr1, arr2) {
  let i = 0;
  let j = 0;
  let result = [];
  // 왼쪽과 오른쪽을 비교해서 작은것이 먼저 result에 들어간다.
  while (i < arr1.length || j < arr2.length) {
    if (arr1[i] <= arr2[j] || j >= arr2.length) {
      result.push(arr1[i]);
      i++;
    } else if (arr1[i] >= arr2[j] || i >= arr1.length) {
      result.push(arr2[j]);
      j++;
    }
  }
  // console.log(result);
  return result;
}

function mergeSort(arr) {
  if (arr.length <= 1) return arr;
  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));
  console.log(left, right);
  // 오른쪽과 왼쪽의 길이가 1이 될때까지 분해되면 merge를 통해 합친다.
  return merge(left, right);
}
mergeSort([3, 4, 2, 12, 10, -1, 2.5, 2.5, 11]);
```

# 3. quick 정렬

가장 이해하기 어려운 정렬이다... pivot 을 일단 정해야한다. 그 pivot 보다 작은수는 왼쪽으로 큰 수는 오른쪽으로 이동시킨다. 다음 pivot을 설정한다. 과정을 반복한다.

--Grand Scheme

- Like merge sort, exploits the fact that arrays of 0 or 1 element are always sorted.

- Works by selecting one element (called the ‘pivot’) and finding the index where pivot should end up in the sorted array

- Once the pivot is positioned appropriately, quick sort can be applied on either side of the pivot.

-- PseudoCode

1. In order to implement merge sort, it’s useful to first implement a function responsible arranging elements, in an array on either side of a pivot

2. Given an array, this helper function should designate an element as the pivot

3. It should then rearrange elements in the array so that all values less than the pivot are moved to the left of the pivot and all values greater than the pivot are moved to the right of the pivot.

4. The order of elements on either side of the pivot doesn’t matter!

5. The helper should do this in place, that is, it should not create a new array

6. When complete, the helper should return the index of the pivot

-- Helper Psuedo code

1. It will help to accept three arguments: an array, a start index, and an end index(these can default to 0 and the array length minus 1, respectively)

2. Grab the pivot from the start of the array

3. Store the current pivot index in a variable (this will keep track of where the pivot should end up)

4. Loop through the array from the start until the end.

- if the pivot is greater than the current element, increment the pivot index variable and then swap the current element with the element at the pivot index.

5. Swap the starting element(I.e the pivot) with the pivot index

6. Return the pivot index.

-- Quicksort PseudoCode

1. Call the pivot helper on the array

2. When the helper returns to you the updated pivot index, recursivley call the pivot helper on the subarray the left of that index, and the subarray to the right of that index.

3. Your base case occurs when you consider a subarray with less than 2 elements.

-- Time complexity

- Best/Average: O(n log n) / Worst: O(n2)(even if array is almost sorted, it will pick first item as pivot) - it decomposes(O(n)) and it compares (another O(n))

-- Space complexity: O(log n) -- because of call stack

```javascript
function pivot1(arr, start = 0, end = arr.length - 1) {
  let pivot = arr[start];
  let swapIdx = start;
  function swap(arr, i, j) {
    let temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
  }
  for (var m = start + 1; m <= end; m++) {
    if (pivot >= arr[m]) {
      swapIdx++;
      swap(arr, swapIdx, m);
    }
  }
  swap(arr, swapIdx, start);
  // console.log(arr);
  // console.log(swapIdx);
  return swapIdx;
}

//   pivot();

function quickSort(arr, left = 0, right = arr.length - 1) {
  if (left < right) {
    let pivotIndex = pivot1(arr, left, right);
    // left / pivot을 arr의 끝으로 설정함
    quickSort(arr, left, pivotIndex - 1);
    // right / pivot을 arr의 시작으로 설정함
    quickSort(arr, pivotIndex + 1, right);
  }
  // pivot +- 하는 이유는 pivot 은 이미 정렬 되었기 때문
  // 그리고 arr는 재귀함수가 실행되면서 동시에 변형됨. obj는 reference 를 통해 참조되기 때문
  return arr;
}

quickSort([4, 8, 2, 1, 5, 7, 6, 3]);
// 와 ... 이거 좀 이해하기 힘든 분야네 ㅋㅋㅋ
// 일단 같은 arr에 parameter가 계속 바뀌니깐 헷갈리고
// 같은 arr를 return한다는 개념도 조금 헷갈리는 것 같고
// 일단 또 다시 보면서 이해해봐야겠다.

// pivot에서 swapIdx = start 라는거 유의하고.
//또한 var m = start +1 ; m <= end 라는 것을 잘 생각해보자
```

quick 정렬은 시간을 들여서 찬찬히 이해해되 된다. 한 번에 이해가 안되기 때문이다. 그럼 데이터 구조의 또 다른 종류인 연결 리스트를 배워보자.
