---
title: "<8> 미니게임으로 연습하는 바닐라 JS (event loop)"
excerpt: "event loop 의 순회"

categories:
  - Vanila JS practice
tags:
  - event loop
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. runtime 환경에 대해서

자 그럼 자바스크립트가 실제로 브라우저에서 어떻게 동작하는지 알아보자. 동작하는 환경을 일단은 runtime environment라고 한다(이하 runtime). 그리고 그곳에서 자바스크립트 엔진과 브라우저는 서로 소통을하면서 협동한다. 이때 협동할 수 있게 소통을 돕는 아이가 바로 event loop이다. event loop는 `while(true)`의 형태로 되어있어서 항상 작동하는 아이다. 그림으로 표현하면 아래와 같다.

![runtime](https://yeonghunko.github.io/assets/img/vanila_practice/runtime.png){:class="img-fluid"}

우선 각각의 용어를 먼저 살펴보자.

콜스택은 자바스크립트 엔진안에 있는 실행순서다. 그리고 web browser에는 큐스택, 마이크로스택, 랜더가 있다.(상황마다 더 추가될 수 있지만 크게 요렇게 3가지가 있다)
이벤트loop는 콜스택, 큐스택, 마이크로스택, 랜더를 순회하면서(한번 순회할때 걸리는 시간이 1ms정도 밖에 걸리지 않을 정도로 매우 빠르다) 각각의 스택에 쌓인 일들을 수행한다. 또한 어떤 스택을 먼저 실행하는지는 브라우저마다 다르다.

우선 콜스택에 있는 애들을 처리한다. 큐스택은 한번에 하나만 처리한다. 그리고 순회하고 나서 큐스택에 다음 작업을 처리한다. 마이크로스택은 큐스택과는 다르게 한번 방문하면 마이크로스택안에 있는 모든 작업을 순서대로 처리하고 나서 순회를 시작한다.또한순회하다가 16.7ms가 지나면 랜더안에서 처리해야할 애니메이션이 있는지 확인하고 있으면 한번 뿌려주고 다시 순회한다. 여기서 뿌려준다는 건 render tree -> layout(크기 위치 계산) -> paint를 말한다. (16.7ms마다 한번씩 뿌려주어야 60프레임이 되고 그래야 우리눈에 자연스럽게 보임)

만약 콜스택에 많은 작업을 해야하는 함수가 쌓여있다면 그 외에 랜더 스택이나(애니메이션) 큐스택(클릭이벤트 같은거) 에 있는 아이들이 콜스택안에 있는 모든 작업이 끝나기 전까지 실행되지 않는다. 따라서 콜스택안에서는 가벼운 기능을 수행하는 함수를 쌓아놓는게 좋다.

예를 들어 아래와 같은 코드가 있다고 해보자.

```javascript
const button = document.querySelector("button");
button.addEventListener("click", add);

function add() {
  const head = document.createElement("h1");
  document.body.appendChild(head);
  head.style.color = "red";
  head.innerText = "hello";
}
```

자바스크립트 엔진은 클릭함수를 browser web api에 저장한다음 클릭하면 add가 큐스택에 저장되어있다가 이벤트루프가 순회하면 그제서야 add가 콜스택으로 옮겨져 실행이 되고 다시 이벤트루프가 순회하면서 준비된 head가 render 되어 browser에 hello가 표시되는 것이다.

비유를 하자면 "다음 무대에 올라갈 사람은 너야!" 라고 지목된(appendChild) A 배우(element)가 백 스테이지에서 메이크업(style, innerText)을 받고 순서가 되자 무대에 올라간(Render)다.

그래서 사실상 append를 하고 스타일을 입히나 스타일을 입히고 append를 하나 차이가 없다. 메이크업을 하고 지목하나 지목하고 메이크업을 하나 똑같기 때문.

loupe라는 웹사이트에서 벡엔드에서 일어나는 이러한 과정을 시각화시켰다.

![loupe](https://yeonghunko.github.io/assets/img/vanila_practice/loupe.gif){:class="img-fluid"}
