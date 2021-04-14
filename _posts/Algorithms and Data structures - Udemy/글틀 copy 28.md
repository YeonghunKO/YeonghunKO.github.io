---
title: "<16> Graphs(basic)"
excerpt: ""

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

# 1. Graphs 개념

**What is it?**

- Bunch of nodes or points connected together without hierarchy. they are all treated equally.

**Terminology**

- vertex: node.
- edge: connection.
- undirected graph: two-way connections, or no direction or polarity.
- directed graph: there is certain direction assigned to an edge. ex) facebook.
- unweigthed graph: no value or maginitude with each edge.
- weighted graph: it does have value associated with edge. ex) road map.

쉽게 말해서, node간의 위계질서가 없다. 그러니 시작점도 끝점도 없다. 내가 어디서 시작하느냐에 따라 끝도 달라진다. 또한 edge에 value를 설정할 수 있다. edge에 설정한 value로 인해서 최단거리를 구할 수 도 있다.(Dijsktra에서 배울라나?)

그럼 이 graph를 어떻게 나타낼 것인지 알아보자.

**Compare storing method**

1. Adjacency list

- Can take up less space(in sparse graphs)
- Faster to iterate over all edges
- Can be slower to look up specific edge

2. Adjacency matrix

- Takes up more space (in sparse graphs)
- Slower to iterate over all edges
- Faster to look up specific edge

- We choose Adjacency list because most data in the real-world tends to lend itself(to be good for a particular use. it is good enough to lend) to sparser and/or larger graphs.

![graphMatrix](https://yeonghunko.github.io/assets/img/algorithms_Udemy/graphMatrix.png){:class="img-fluid"}

![graphList](https://yeonghunko.github.io/assets/img/algorithms_Udemy/graphList.png){:class="img-fluid"}

요런식으로 그려지지만 실제로 data에 저장되는 형태는 list의 형태이다.

그럼 vtx와 edge를 추가하는 코드를 작성해보자.

# 2. Graph addVertex

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

![doubly](https://yeonghunko.github.io/assets/img/algorithms_Udemy/doubly.png){:class="img-fluid"}
