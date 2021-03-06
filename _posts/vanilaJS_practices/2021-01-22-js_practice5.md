---
title: "<5> 미니게임으로 연습하는 바닐라 JS (디버깅하는 방법)"
excerpt: "재밌는 디버깅"

categories:
  - Vanila JS practice
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

# 1. 개발자 도구를 통해 디버깅 하는 법

진짜 신기한 기능을 알았다. 클릭 할때 마다 모든 과정이 순차적으로 실행되고 과정마다 어떤 일이 일어나는지 상세히 설명해주는 기능이다. 우선 개발자 도구에서 sources 에 들어간다. 그리고 왼쪽에 자바스크립트를 클릭한다음 오른쪽 상단에 pause를 클릭한다. 그리고 watch를 통해서 내가 특정 영역의 변화상황을 자세히 관찰할 수 있다.

예를들어 submit 했을때 event의 target이 무엇인지 확인하고 싶다고 한다면 console.log(event)라고 하고 콘솔창을 봐도 되지만, watch를 통해 곧바로 확인 가능하다. watch에 + 버튼을 클릭한다음 event를 등록하자. 지금은 undefined라고 되어있지만 나중에 monitoring이 실행되면 event가 활성화 되면서 안에 있는 정보가 나타날 것이다.

![ready](https://yeonghunko.github.io/assets/img/vanila_practice/ready.png){:class="img-fluid"}

그럼 이제 monitoring할 준비가 끝났다. 웹페이지에서 어떤 기능을 실행한다. 이번 경우에는 shopping_list 프로젝트를 실행해보았다. submit을 하자마자 submit event가 실행이 되고 오른쪽에 watch에 특정 event가 출력이 된다.

![start](https://yeonghunko.github.io/assets/img/vanila_practice/start.png){:class="img-fluid"}

그리고 JS 파일안에서 현재 어떤 단계에 위치해있는지 초록색으로 표시가 된다. 그러고 나서 오른쪽 상단에 아래쪽으로 향하는 화살표를 클릭하면 로직이 차례대로 실행이 된다. 더 신기한것은 로직 옆에 그 로직이 실행될때 PASS 되거나 생성되야하거나 하는 등등의 결과들이 작게 빨간색으로 표시가 된다.

그와 동시에 scope를 보면 지금 해당 단계에서 작동하는 함수라던가 parameter같은 정보들을 상세히 설명하고 있다.

![processing](https://yeonghunko.github.io/assets/img/vanila_practice/processing.png){:class="img-fluid"}

![processing_almost](https://yeonghunko.github.io/assets/img/vanila_practice/processing_almost.png){:class="img-fluid"}

모든 로직이 처리가 되면 마침내 input에 입력되었던 값이 list에 출력이 되면서 monitoring은 끝난다.

![processing_finished](https://yeonghunko.github.io/assets/img/vanila_practice/processing_finished.png){:class="img-fluid"}

이 얼마나 친절하고 편리한 기능인가!! 일일이 로그를 통해 확인하지 않아도 되고 어디서 어떤일이 일어나는지 차근차근 선택하며 확인할 수 있기에 디버깅을 하는데 매우 유용하게 쓰일 것 같다.

# 2. 콘솔로그에서 queryselector('선택자') 를 통해서 원하는 노드를 찾아내는 방법

이건 콘솔 로그에서 이런 기능이 있다는게 신기해서 포스팅한다. 디버깅할때 어느정도 도움이 될 수 도 있을 거 같다. 만약에 `사과` 라는 class를 찾고 싶다고 할때 콘솔창에 `document.querySelector('.사과')` 라고 입력하면 아래와 같은 결과가 나온다.

```html
<li class="사과 list">
  <span>사과</span>
  <button class="delete_btn">🗑</button>
</li>
```

JS에서 입력할때 처럼 똑같이 입력하면 된다. 그럼 다음 포스팅에서는 미니쇼핑 프로젝트 진행할때 이벤트 위임을 통해 모든 자식 태그에 click이벤트를 위임할 수 있었다. 그 원리가 무엇이었는지 알아보겠다.
