---
title: "<7> 단일 연결 리스트 "
excerpt: "Singly Linked List"

categories:
  - Algorithms and Data structures - Udemy
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

# 1. 단일 연결 리스트

array 와 같이 정보를 담는 그릇이다. 그러나 array 많은 점이 다르다. 포인터를 통해 연결되어있고(맞다. 그 유명한 포인터다.) index가 없다. 자세한 내용은 아래 정리되어있다.

단일 연결 리스트도 정렬과 마찬가지로 `visualgo` 에서 확인가능하다.

Linked list: a data structure that contains a head , tail and length property. it consists of nodes, and each node has a value and a pointer to another node or null.

1. Lists

- Do not have indices

- Connected via nodes with a next pointer

- Random access is not allowed

- No need to re-index when new element is inserted or deleted

---So it is sort of like a skyscrapper with no lift. If you want to locate 5th floor, You have to start from the beginning and go up the stairs only to get there.

2. Arrays

- indexed in order

- Insertion and deletion can be expensive - cascading ripple effect, everything should be re-indexed

- Can quickly be accessed at a specific index

그리고 클래스를 만들어서 단일 연결 리스트를 관리해보겠다.

# 2. 단일 연결 리스트를 위한 노드 클래스

우선 정보가 담길 node 클래스를 만들어주자.

```javascript
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
  }
}

var first = new Node("hi");
first.next = new Node("How are");
first.next.next = new Node("you?");
```

우리가 하려는 것은 저렇게 node를 만들고 val안에다가 정보를 저장하고 next안에 다음 정보를 저장한다. 그리고 같은 작업을 반복한다. 그럼 아래와 같이 단일 연결 리스트가 만들어진다.

![firstNode](https://yeonghunko.github.io/assets/img/algorithms_Udemy/firstNode.png){:class="img-fluid"}

하지만 이렇게 손으로 적으면 너무 불편하다 따라서 SinglyLinkedList 클래스안에 push 메소드를 만들어주려고 한다.

# 3. Push 메소드

우리의 목적은 push 메소드에다 인자를 전달하면 그 인자가 새로운 노드를 만들어내고 next에 연결되게 하는것이다.

```javascript
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }
  push(val) {
    var newNode = new Node(val);
    if (!this.head) {
      this.head = newNode;
      this.tail = newNode; //this.head 라고 해도 무방. 어찌되었든 같은 곳을 참조하게 하면 됨.
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
    this.length++;
    return this;
  }
}
```

head가 없으면, 즉 노드를 처음 만드는 것이라면 head와 tail은 같게된다. 그게 아니라면 tail.next 즉 tail이 최종적으로 가리키는 곳이 newNode가 되고 tail은 newNode로 탈바꿈한다.

그럼 질문! 'tail.next에서 tail의 next 가 바뀌는 것인데 왜 head도 바뀌냐?' 라고 물을 수 있다. 그 이유는 변수에 obj를 선언할때 obj가 복사되는게 아니고 obj를 가리키는 주소가 복사된다. head 와 tail은 같은 곳을 가리키고 있다.맨처음 생성한 newNode를 가리키는 주소가 복사되어있는것이다.

따라서 tail을 편집하면 newNode를 편집하는 것이 되고 그럼 newNode를 가리키는 head를 편집하는게 되는것이다. 정확히 말하면 newNode가 편집되었기 때문에 head를 들여다 보면 편집된 newNode를 들여다 볼 수 있는것!

obj의 reference address는 따로 'javascript reference' 워드파일로 정리해서 깃헙에 올려놓았으니 참고할것!

그럼 다시 push 돌아와서, push를 통해 node가 계속 연결이 되게 되는것이다. 글로는 이해하기 쉽지 않아서 따로 종이에 정리했다.

![push](https://yeonghunko.github.io/assets/img/algorithms_Udemy/push.png){:class="img-fluid"}

push 외에 pop,insert,shift,get,set 과 같은 다양한 메소드가 있지만 그중에서 이해하기 어려웠던거 마지막으로 한가지만 설명하고 단일 연결 리스트를 끝내려고 한다. 바로 `reverse()` 이다

# 4. reverse 메소드

node의 순서를 말그대로 뒤집는것이다. 근데 로직이 조금 복잡해서 설명하려고 한다.

```javascript
reverse() {
  var count = 0;
  var node = this.head;
  this.head = this.tail;
  this.tail = node;

  var next;
  var prev = null;

  for (var i = 0; i < this.length; i++) {
    next = node.next;
    node.next = prev;
    // console.log(node);
    // 여기부터는 node 가 바뀌어있다. node = start -> null 로 바뀌어 있다.
    // 참고로 for문 맨위에 next 에 담겨진 노드는 바뀌기전 노드, 즉  a -> b -> end -> null 이다.
    prev = node;
    node = next;
    // node를 하나씩 잘라서 next에 저장.
    // 그리고 node의 next를 prev에 연결
    // prev는 연결된 노드를 이어받음
    // next에 백업했던 걸 node 가 이어받음

    // 와따 쪼까 복잡한 로직이구먼. 노트에 그린거 참고하기

    // console.log(prev);
    // console.log(next);
  }
}

```

우선 head와 tail을 먼저 교체한다.

next에 바뀌기전 node.next를 저장해놓고는 node를 바꾸고 prev에 할당한다. 그리고 노드는 next것을 물려받고 다음 loop에서 node는 하나씩 잘려서 next에 저장된다.

역시 글로 이해가 어려워서 노트에 그림으로 정리해봤다.

![reverse](https://yeonghunko.github.io/assets/img/algorithms_Udemy/reverse.png){:class="img-fluid"}

다음글은 doubly linked list이다!
