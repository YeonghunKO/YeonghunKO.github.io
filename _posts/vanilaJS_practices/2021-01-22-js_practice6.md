---
title: "<6> 미니게임으로 연습하는 바닐라 JS (bubbling과 delegation(위임))"
excerpt: "bubbling이 뭔지 그리고 그게 delegation과 어떻게 연결이 되는지"

categories:
  - Vanila JS practice
tags:
  - bubbling
  - delegation
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. bubbling

bubbling은 이름 그대로 방울이 겹쳐서 연속적으로 무엇인가가 올라가는 그림을 그리면 된다. 부모태그와 자식태그에 설정된 이벤트가 같다고 했을때 자식태그에 있는 이벤트가 실행되면 상위에 있는 부모태그 모두가 다같이 실행되는 현상이 bubbling이다. 설정된 이벤트가 방울처럼 부모쪽으로 퍼져나간다고 생각하면 더 이해하기 쉬울 것 같다. 예시를 통해 살펴보자.

![bubbling_click](https://yeonghunko.github.io/assets/img/vanila_practice/bubbling_click.png){:class="img-fluid"}

outer > middle > button 순으로 위계질서가 형성되어있고 각각의 태그에 click 이벤트가 설정되어있으며 클릭했을때 `현재 위치해있는 태그, 이벤트가 실행된 위치` 가 출력되도록 했다. 이때 button을 클릭하니 middle / outer 의 이벤트 까지 실행된것을 볼 수 있다.

만약 button에다가 두개의 이벤트를 등록한다면 어떻게 될까? 화면상에서 먼저 설정된것이 실행될 것이다.

그럼 부모태그에 있는 이벤트가 실행되지 않게 하려면 어떻게 해야할까?

로직을 생각해보면, `event.target !== currentTarget` 이라는 명령을 추가해주면 된다.

```javascript
outer.addEventListener('click', event => {
  if (event.target !== event.currentTarget) {
    return;
  }
  // 그게 아니면
  console.log(~~~)
})
```

# 2. 이벤트 delegation(위임)

따라서, 이벤트를 등록해야할 대상이 너무 많다면은 그 대상을 다른 부모태그로 감싼 다음 부모 태그에 이벤트를 설정해주면 bubbling 현상으로 인해서 부모안에 있는 모든 자식태그들에 부모와 동일한 이벤트가 등록된다. 아주 깔끔해진다. 일일이 이벤트를 등록하지 않아도 되서. 그리고나서 자식태그를 클릭하면 부모태그에 등록된 이벤트 콜백함수가 실행된다. 그렇기 때문에 mini_shopping_game 에서 section 부모태그에만 이벤트를 등록한것이다.
