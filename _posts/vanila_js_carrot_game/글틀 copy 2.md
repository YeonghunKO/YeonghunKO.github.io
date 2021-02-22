---
title: "<1> 미니게임으로 연습하는 바닐라 JS (당근게임)"
excerpt: "객체, 함수는?"

categories:
  - Vanila JS Carrot Game
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

# 1. Week 3

```javascript
function displayAll() {
  init().then((items) => {
    //아이콘 초기화
    playField.innerHTML = "";
    // json안에 있는 data를 전달해주긴 했지만 그걸 사용하지는 않았음.
    const carrotItems = items.map(createCarrotIcon);
    const bugItems = items.map(createBugIcon);
    // console.log(carrotItems[0],typeof bugItems);
    playField.append(...carrotItems);
    playField.append(...bugItems);
    countCarrotFunc();
  });
}
function startAgain() {
  playBtnDiv.style.visibility = "visible";
  playBtn.innerHTML = `<i class="fas fa-pause"></i>`;
  audioBackground.play();
  count = 10;
  clearInterval(intervalId);
  intervalId = setInterval(decreasingCount, 1000);
  popUp.classList.add("non_display");
  displayAll();
}

function startGame(event) {
  if (playFromTheVeryStart === true) {
    activateReplayBtn();
    startAgain();
    playFromTheVeryStart = false;
  } else if (playFromTheVeryStart === false) {
    if (event.target.classList.contains("fa-pause")) {
      playBtn.innerHTML = `<i class="fas fa-play"></i>`;
      audioBackground.pause();
      clearInterval(intervalId);
      popUp.classList.toggle("non_display");
      gameResult.innerHTML = `Restart?`;
    }

    if (event.target.classList.contains("fa-play")) {
      playBtn.innerHTML = `<i class="fas fa-pause"></i>`;
      audioBackground.play();
      intervalId = setInterval(decreasingCount, 1000);
      popUp.classList.toggle("non_display");
    }

    if (event.target.classList.contains("fa-reply-all")) {
      startAgain();
    }
  }
}

//main
function init() {
  playBtnDiv.addEventListener("click", startGame);

  return fetch("./data/data.json")
    .then((response) => response.json())
    .then((json) => json.items);
}

init();
```

```javascript
x = 2;
x = x + 2;
print(x);
```

```javascript
x = 2;
x = x + 2;
print(x);
```

```javascript
x = 2;
x = x + 2;
print(x);
```

1. 사용자가 댓글을 단다.
   {: .notice--success}

2. 댓글단 사용자에게 서버가 메일을 보낸다.
   {: .notice--success}

3. 댓글이 표시된다.
   {: .notice--success}

```html
x = 2 x = x + 2 print(x)
```

```css
x = 2
x = x + 2
print(x)
```

## Week 3 영어문장 정리

- So like I said, you can do interactive in Python or you can run a script.(Interactive: You type directly to python one line at a time and it responds.)

- And you'll notice that this is indented at the same level as the print statement.

![if](https://yeonghunko.github.io/assets/img/vanila/if.png){:class="img-fluid"}
