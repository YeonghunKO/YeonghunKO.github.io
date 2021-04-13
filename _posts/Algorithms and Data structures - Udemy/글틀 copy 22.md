---
title: "<10> 이진탐색트리(Binary Search Trees)"
excerpt: "나무"

categories:
  - Algorithms and Data structures - Udemy
tags:
  - insert
  -
last_modified_at: 2020-08-27T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.
> 2. 각 개념에 따른 코드 정리.

# 1. 이진검색트리

이름만 들어서는 무슨 말인지 잘 모르겠다. 이 자료구조의 경우에는 영어가 더 편한것 같다.(이하 BST)

BST에 대해서 간략하게 개념을 정리해 보았다.

-- Terminology

- Root / Child / Parent / Siblings / Leaf / Edge(arrow)

-- Application

- HTML DOM

- Artificial Intelligence

- Computer file systems

**Binary Search Trees (BST)**

- Every parent node has at most two children
- Every node to the left of a parent node is always less than the parent
- Every node to the right of a parent node is always greater than the parnent

뿌리가 있고 그 밑으로 자료들이 뻗어가는 형태를 띄고 있다. tree는 다양한 형태가 있는데 그중에 BST는 큰게 오른쪽 작은게 왼쪽에 위치해있다. 그래서 이름처럼 검색에 매우 유용한 구조이다.

그럼 insert부터 알아보자.

## 1-1. Insert

**BST insert pesudocode**

-- Create a new node.

-- starting at the root.

- check if there is a root, if not – the root now becomes that new node.

- If there is a root, check if the value of the new node is greater than or less than the value of the root.

- keep comparing until you found the sweet spot for the new node! good luck.

newNode가 크면 계속 오른쪽으로 가다가 null을 만나면 그자리에 정착. 작은경우도 마찬가자!

```javascript
class Node {
  constructor(val) {
    this.val = val;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTrees {
  constructor() {
    this.root = null;
  }

  insert(val) {
    var newNode = new Node(val);
    if (!this.root) {
      this.root = newNode;
      return this;
    } else {
      var newNodeVal = newNode.val;
      var currentNode = this.root;

    while (true) {
      if (newNodeVal > currentNode.val) {
        if (currentNode.right) {
          currentNode = currentNode.right;
        } else {
          currentNode.right = newNode;
          break;
        }
      } else if (newNodeVal < currentNode.val) {
        if (currentNode.left) {
          currentNode = currentNode.left;
        } else {
          currentNode.left = newNode;
          break;
        }
      } else {
        return 'invalid num';
      }
    }
    return this;
  }
}
```

# 1-2. Find

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

![if](https://yeonghunko.github.io/assets/img/coursera-python/if.png){:class="img-fluid"}
