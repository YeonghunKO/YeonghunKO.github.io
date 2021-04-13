---
title: "<9> Stacks and Queues (컨테이너와 줄)"
excerpt: "LIFO, LILO"

categories:
  - Algorithms and Data structures - Udemy
tags:
  - stacks
  - queues
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. Stacks

stacks은 쉽게 말해 상자라고 생각하면 된다. 우리가 상자에 책을 차곡차곡 넣는다고 하자. 이때 처음에 들어갔던것은 맨 마지막에 나올 수 있다. 그리고 마지막에 들어간것은 제일 처음 나온다. 그래서 일반적으로 array처럼 활용가능하다.

보통 debugging 할때 옆에 나오는 stacks이 이 stacks 이다.

그런데 헷갈릴 수 있는점은 first 와 last property가 있는데 first는 제일 위쪽에 있는 책을 가리키고 last는 제일 안쪽, 즉 바닥에 깔려 있는 책을 가리킨다. first가 제일 처음 넣은 책이 아니라는 것이다. last가 제일 처음넣은 책이다!

그걸 염두해 두고 자료구조를 만들어보자. 사실 stacks와 queues는 단일 연결 리스트이다. array/built-in method를 사용하지 않는 이유는 역시나 index가 re-arrange 되는것을 피하기 위해서이다. 다시말해서 time complexity가 O(1)을 유지하기 위함이다. 메소드도 push/pop 두개가 끝이다

그럼 메소드를 살펴보자.

A LIFO data structure. The last element added to the stack will be the first element removed from the stack.

Think about a stack of plates, or a stack of markers, or stack of ...anything. In computer, you can think of recursion stacks and Undo function by pressing ctrl + z.

Array is typical example of stacks. LIFO for pop(). So, if we add or remove something from beginning, it is inefficient as we have to shift every indices. So I built custmoized class for stacks.

## 1-1. Push/Pop

```javascript
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }

  push(val) {
    var newNode = new Node(val);
    if (!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      var temp = this.first; // node a 를 가리킴
      this.first = newNode; // this.first 는 이제 node b 를 가리킴
      this.first.next = temp; // node.b.next 는 node a를 가리킴

      // this.last는 처음처럼 node a를 그대로 유지. this.last 가 가리키는 뱡향을 바꾼 적이 없으므로

      // 항상 포인터의 끝이 어디로 향하는지를 봐라!
    }
    return ++this.size;
  }

  pop() {
    if (!this.first) return null;
    var temp = this.first;
    if (this.first === this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.val;
  }
}
```

# 2. Queues

Queues는 사람들이 늘어선 줄이라고 생각하면 된다. 제일 먼저 들어간 사람이 제일 먼저 나간다. First In First Out 이다.

다운로드 할때 queues를 사용한다. 제일 먼저 누른것이 제일 먼저 다운로드 된다. 그럼 자료구조를 만들어보자

## 2-1. enqueue/dequeue

```javascript
class Queue {
  constructor() {
    this.first = null;
    this.last = null;
    this.size = 0;
  }

  enqueue(val) {
    var newNode = new Node(val);
    if (!this.first) {
      this.first = newNode;
      this.last = newNode;
    } else {
      this.last.next = newNode;
      this.last = newNode;
    }
    return ++this.size;
  }

  dequeue() {
    if (!this.first) return null;
    var temp = this.first;
    if (this.first === this.last) {
      this.last = null;
    }
    this.first = this.first.next;
    this.size--;
    return temp.val;
  }
}
```

그럼 Binary Search Trees(BST)에 대해서 알아보도록 하자.
