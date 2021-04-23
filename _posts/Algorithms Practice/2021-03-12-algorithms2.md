---
title: "<2> 코딩테스트 (프로그래머스 코딩테스트-인형뽑기)"
excerpt: "claw machine solutions"

categories:
  - Algorithms Practice
tags:
  - reduce
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 인형뽑기 테스트 답안

역시나 세상은 넓다. 정말 깔끔하게 글을 적으신 분이 계셨고 그걸 보고 또 많이 배웠다.

```javascript
// soluetion 1

let board = [
  [0, 0, 0, 0, 0],
  [0, 0, 1, 0, 3],
  [0, 2, 5, 0, 1],
  [4, 2, 4, 4, 2],
  [3, 5, 1, 3, 1],
];

let moves = [1, 5, 3, 5, 1, 2, 1, 4];

function reducer(result, row) {
  console.log(result);
  console.log(row);
  // 그전에 합쳐논 result를 다 세로로 나열한다음 board 다음 row를 세로로 나열해서 합치는 작업이다.
  var line = row.map((_, i) => [...(result[i] || []), row[i]]);
  console.log(line);
  return line;
}

function transpose(matrix) {
  // matrix(board)를 이제 변형시킨다음 변형시킨 최종본을 리턴시킬거다.
  // ,[] 같은경우  row[-1]를(원래 존재할 수 없지만, 합치기 위해 편의상) [] 로 임의로 설정해주는거다.
  // 임으로 설정한 [] 와 row[0]를 다 분리해서 일일이 합치는거다
  return matrix.reduce((result, row) => reducer(result, row), []);
}

// 로직 순서
// board를 오른쪽 위 대각선 방향으로 뒤집는다고 보면 됨.
// 그리고 순서를 반대로 한다.
// 그리고 0을 제외한다.
// 그걸 stack에 담는다
// 그리고 moves 순서대로 움직이면서 pop을 통해 맨 마지막거만 빼서 basket에 담는다
// pop이 basket에 담긴 숫자중에서 마지막 수랑 같다면 그 숫자를 pop해서 없애고 result에 2를 더함

// 로직이 이해하기는 살짝 어렵지만 예술적인 느낌이 난다.

const solution = (board, moves) => {
  const stacks = transpose(board).map((row) =>
    row.reverse().filter((el) => el !== 0)
  );
  const basket = [];
  let result = 0;
  console.log(stacks);
  for (const move of moves) {
    const pop = stacks[move - 1].pop();
    // console.log(pop);
    if (!pop) continue;
    if (pop === basket[basket.length - 1]) {
      basket.pop();
      result += 2;
      continue;
    }
    basket.push(pop);
  }
  console.log(basket);
  console.log(result);
  return result;
};

solution(board, moves);

// solution 2

function solutionTwo(board, moves) {
  var count = 0;
  var stack = [];

  for (var i = 0; i < moves.length; i++) {
    var now = moves[i] - 1;
    for (var j = 0; j < board.length; j++) {
      if (board[j][now] != 0) {
        if (stack[stack.length - 1] === board[j][now]) {
          stack.pop();
          count += 2;
        } else {
          stack.push(board[j][now]);
        }
        board[j][now] = 0;
        break;
      }
    }
  }
  console.log(stack);
  console.log(count);
  return count;
}
// solutionTwo(board, moves);

// 훨씬 이해하기 쉬운 코드다 위에거 보다. 클린코드에 의하면 이게 더 좋은 코드인가?
```

2명을 선정했는데 첫번째는 코드를 이해하느라고 좀 애먹었다. 그런 측면에서 난 두번째 답안이 더 좋은 코드라고 생각한다. 내가 아직 실력이 부족한것일지도 모르겠지만 ㅎㅎ

다만 위의 솔루션 2개의 공통점은 쓸데없는 과정을 모두 생략했다. 가령 나같은 경우엔 basket에 넣은다음에 for 문을 돌려서 같은 수를 찾아서 뽑아낸다음 어디에 담고 갯수를 세었다.

그러나 위의 두 분은 basket에 넣는 순간 같은게 있으면 count에 2를 추가하는 식이다. 그렇게 끝나버린다. 불필요한 과정은 다 빼고 반드시 필요한 과정만 남기는 연습을 하자.

그리고 마지막으로 reduce에 대해서 살짝 정리하고 가려고 한다. 내가 1번째 코드를 잘 이해하지 못한 이유는 map과 reduce에 대한 이해가 부족해서 일지도 모른다.

# 2. reduce

reduce의 핵심은 이전의 결과가 변형되어 새로운 결과가 되고 그 새로운결과가 다시 넘어간다.

즉 변경사항이 쌓이는것이다.

맨처음 넘어가는 result(accumulator)는 빈 array이다.

다음은 MDN 영어 설명이다.

Your reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array, and ultimatley becomes the final, single resulting value.

아래의 코드를 보면 더 잘 이해할 수 있다.

```javascript
const numbers = [-5, 6, 2, 0];

const doubledPositiveNumbers = numbers.reduce((accumulator, currentValue) => {
  if (currentValue > 0) {
    const doubled = currentValue * 2;
    accumulator.push(doubled);
  }
  return accumulator;
}, []);

doubledPositiveNumbers;
```

debugging 툴을 사용하면 accumlator가 넘어갈때 변경사항이 반영되는 것을 볼 수 있다. currentValue는 numbers의 element를 순회한다.

# 3. map

map은 각각의 element를 변형하여 새로운 array를 뱉어낸다.

아래는 MDN의 설명이다.

The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.

아래 코드를 보자.

```javascript
var arr = [1, 2, 3, 4, 5];
var anotherArr = [10, 11, 12, 13, 14]; //

arr.map((c, i) => [anotherArr[i] + c]);

// 0: [11]
// 1: [13]
// 2: [15]
// 3: [17]
// 4: [19]
```

arr안에 ele가 anotherArr의 ele와 합쳐져서 []안에 담기고 그 새로운 `[ele+anotherArr]` 가 arr의 ele가 된다. 따라서 결과는 위와 같다.
