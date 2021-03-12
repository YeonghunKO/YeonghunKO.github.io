---
title: "<1> 코딩테스트 (프로그래머스 코딩테스트-인형뽑기)"
excerpt: "claw machine"

categories:
  - Algorithms
tags:
  - splice
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 코딩테스트 연습

프로젝트를 몇개 하다보니 이제는 좀 더 코드의 퀄리티를 높이기 위해 알고리즘과 자료구조를 공부하기로 했다. 필수라는 사람도 있고 아니라는 사람도 있지만 , 난 개인적으로 어설프게 하는건 싫어하기에 , 그리고 이왕하는거 뭐든지 제대로 해야한다고 생각하기에 공부하기로 한것이다. 이와 더불어 나중에 CS지식과 C언어를 공부해서 기본기를 좀 더 탄탄하게 할 생각이다.

아직 알고리즘에 관해서는 거의 문외한이다. 그냥 겁도 없이 프로그래머스에서 제일 쉬운 코딩테스트를 보았다.

인형뽑기 테스트이다. 우선 설명을 보자.

![doll](https://yeonghunko.github.io/assets/img/algorithms/doll.png){:class="img-fluid"}

그래서 없어지는 최종 인형의 갯수 구하면 된다.

글을 처음 읽었을때 그냥 막막했다. 뭐 부터 손대야 할지 몰랐다. 그래서 제일 쉬운것 부터 차근차근 해나가기로 했다. board를 순회도 해보고 moves 를 토대로 뽑아보기도 하고.

그렇게 쉬운거 부터 해나가니까 길이 신기하게도 뚫리기 시작했다. 그렇게 3일동안이나...(이렇게 오래걸리면 안된다.. 그래도 해낸것에 의의를 둔다.) 아무 도움도 받지 않고 힌트도 안보고 외곬수같이 붙잡고 늘어지다보니깐 해냈다! 코드를 공개하겠다!

```javascript
let first = [];

let rearrangedBoard = [];

let basket = [];

let same = [];

let board = [
  [0, 0, 0, 0, 0],
  [0, 0, 1, 0, 3],
  [0, 2, 5, 0, 1],
  [4, 2, 4, 4, 2],
  [3, 5, 1, 3, 1],
];

let moves = [1, 5, 3, 5, 1, 2, 1, 4];
// moves가 7이상이면 버그 발생함 일단 디버거로 차근차근 훑어보면서 확인해보자

function solution(board, moves) {
  pickUpDolls(board, moves);
  sameElementExtractor();
  return same.length;
}

const result = solution(board, moves);
console.log(board);
console.log(basket);
console.log(same);
console.log(result);

// rearragne board sequence to get dolls ready to be picked up.(but not necessary anymore due to picupDolls)
function rearrangeBoard(board) {
  // let boardContents = board[0];
  let whileLoopNum = board[0].length;
  let num = 0;
  while (num < whileLoopNum) {
    for (var i = 0; i < board.length; i++) {
      let boardFirstNum = board[i][0];
      first.push(boardFirstNum);
      let index = board[i].indexOf(boardFirstNum);
      board[i].splice(index, 1);
    }
    rearrangedBoard.push(first);
    first = [];
    num++;
  }
}

// Picking up dolls according to moves
function pickUpDolls(board, moves) {
  // let boardContents = board[0];
  for (var m = 0; m < moves.length; m++) {
    for (var i = 0; i < board.length; i++) {
      let movesNum = moves[m] - 1;
      let boardLine = board[i][movesNum];
      if (boardLine !== 0) {
        basket.push(boardLine);
        board[i].splice(movesNum, 1, 0);
        break;
      }
    }
  }
}

// Extract same dolls and put them in the array called 'same'
function sameElementExtractor() {
  while (true) {
    let isThereAnySameThing = sameElementsDetector(basket);
    if (!isThereAnySameThing) {
      break;
    }
    console.log(basket);
    for (var m = 0; m < basket.length; m++) {
      if (basket[m] === basket[m + 1]) {
        same.push(basket[m], basket[m + 1]);
        console.log(basket[m], basket[m + 1]);
        basket.splice(m, 2);
        break;
      }
    }
  }
}

// shows Whther there are any same dolls left in a raw in the basket
function sameElementsDetector(array) {
  for (var n = 0; n < array.length; n++) {
    if (array[n] === array[n + 1]) {
      return true;
    }
  }
}

// 일단 답을 구하긴 했다. 근데 노가다로 구한거다 진짜...
// 기능을 더 추가해서 확장성을 높이자 (class clawMachine)
// 인형뽑기가 끝나고 나서 기계에 남아있는 인형들 보여주기(showDollsInMachine)
// 인형뽑기가 끝나고 나서 바구니에 남아있는 인형들 보여주기(showDollsInBasket)
// 인형뽑기가 끝나고 나서 어떤 인형이 없어졌는지 보여주기(showDisappearedDolls)
// 인형뽑기가 끝나고 나서 없어진 인형의 갯수 보여주기(showNumberOfDisappearedDolls)
```

그렇게 구현이 끝났다. 질문을 맨처음에 시작했고 답을 달아가면서 가이드라인을 시각화했다.

# 2. 질문과 답. 풀어나가는 과정

**질문:**
정말 어떻게 풀어가야 할까? 일단 첫번째 원소만 다 추출해서 따로 모아놔야하나? 뭐부터 시작해야하나? 막막하다
다 모아놓고 뽑아야 하나 아님, board를 순회하면서 동시에 뽑아야 하나?

**답**

rearrangeBoard(board)

**1** board를 순회하면서 첫번째 원소를 first에 넣고 첫번째원소 지움. 그다음 줄로 넘어감

**2** 그렇게 해서 first array를 rearrangedBoard에 넣고 first를 초기화시킴.

**3** 위의 과정을 반복 board 안에 있는 array 길이만큼

**4** 새로운 array를 기존 array에 덮어씌운다음 LS에 저장한다.

pickUpDolls(moves)

**1.** rearrangedBoard안에서 moves 숫자대로 움직임.

**2.** claw가 moves숫자를 이해해서 그 숫자번째에 도착하면 0은 그냥 지나치면서 마주친 첫번째 숫자를 뽑음

**3.** basket에 넣음

**4.** basket에 넣은 숫자는 rearrangedBoard에서 0으로 만듬

**5.** 위의 과정을 반복 moves 길이 만큼

sameElementExtractor(basket)

**1.** basket에 담긴 숫자를 순회하다가 연속되는 똑같은 숫자가 있으면 그 숫자를 same에 담는다.

**2.** 그리고 그 숫자들은 basket에서 지운다. filter를 사용해서

**3.** 연속된 숫자들이 없을때 까지

이게 최선인가 여기서 더 발전 할 수 는 없을까? 고민했다.

**수정된 답안**

board를 순회하면서 동시에 moves 순서대로 다가가서 숫자를 뽑으면 된다. 해냈다!! 대박이다.

pickUpDolls(moves)

**1.** board안에서 moves 숫자대로 움직임.

**2.** claw가 그 숫자번째에 도착하면 0은 그냥 지나치면서 계속 순회하다가 마주친 첫번째 숫자를 뽑음

**3.** 뽑은 숫자를 basket에 넣음

**4.** basket에 넣은 숫자는 board에서 0으로 만듬

**5.** 위의 과정을 반복 moves 길이 만큼

다만 filter를 쓰면 같은 원소 2개 포함해서 그 앞, 뒤에 있는 같은 원소까지 다 없어진 array를 리턴한다
따라서, 연속되어있는 같은 원소 딱 2개만 없애려면 splice(index,2) 를 써야한다.

그뒤의 로직은 이전 답안과 같다.

**버그**

moves가 [1, 5, 2, 3, 5, 3, 5, 6, 2]; 라고 가정하고 board가

let board = [
[
[0, 0, 0, 0, 0, 0],
[0, 0, 1, 0, 3, 0],
[0, 4, 5, 0, 1, 5],
[4, 2, 4, 4, 2, 8],
[3, 5, 1, 3, 1, 1],
[3, 5, 1, 3, 1, 1],
],
];
라고 한다면 7번째(5째줄에 있는 인형뽑을 때) 뽑을때 오류가 발생한다. 무슨 오류냐면 basket에 담긴 결과가 [4, 3, 4, 1, 1, 5, 2, 5, 5] 것이다.
마지막 숫자가 2가되어야 하는데 5가 되었다
그리고 그렇게 되면 same에 [1,1,5,5] 가 되어야 하는데 [1,1,5,5,5,5] 가 되는것이다....
도대체 뭐가 문제야..디버깅을 통해 하나하나씩 실행되는 걸 보고 깨달았다.

**디버깅**

바로 moves에서 7번째로 인형을 뽑으려 할때(5번째 줄에 있는걸 뽑음) 2를 뽑게 된다. 그럼 4번째 줄 5번째 인형을 없애야 하는데 4번째 줄 2번째 인형을 없앤것이다.

왜냐면 앞에서 부터 2을 찾아가는데 2번째에 2가 있기 때문에 여기서 걸리는 것이다. 그래서 마지막 인형뽑을때 5뽑히게 되는것 same에서도 마찬가지다. basket에서 같은수가 있으면 그 수를 앞에서 부터 훑다가 처음 걸리는것에서 2개를 지우되기 때문에 5,5가 안지워지고 5,2가 지워진것이다.

그래서 splice()안에서 지워야 하는 위치를 indexOf가 아닌 movesNum이랑 m을 사용했다.
좀더 명확하게 명령을 내리는 것이다.

대박 진짜 찢었다. 아무것도 모르는 무의 상태에서 온갖 더럽고 멍청한 방법으로 코딩하면서
수없는 시행착오를 겪다가 찾아보고 하면서 결국엔 깔끔하게 해답을 찾아냈고 리팩토링까지 하고 네이밍도 어느정도 깔끔하게 수정했다.

처음엔 그냥 아무렇게나 적어라 그냥 생각나는대로 진짜 아무렇게나 해도 된다.
그럼 거기서 길이 보인다. 그렇게 하나하나 파고들어서 해결해나가면 진전을 하게 된다.
프로그래밍에서 인생을 배웠다. 직인다.

그리고 테스트에 통과했고 다른사람들 답안을 보게 된다. 어쩌면 통과보다 더 중요한 과정일 수 있다.
