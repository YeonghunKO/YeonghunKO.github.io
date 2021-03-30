---
title: "<2> Problem Solving Approach/Pattern"
excerpt: "문제 이해하고 접근하기"

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

# 1. 문제 이해하고 접근하기

이번에는 문제를 이해하는 방법과 이해했으면 어떻게 해답해 다가갈것인지 설명하는 챕터이다.

우선 세부사항은 빼고 핵심만 적어보려 한다. 세부사항을 확인하려면 깃헙을 확인하자.

# 2. 핵심 내용

- Understand the Problem

- Explore Examples

- Break it down

- Simplify

- Come back and refactor

정리하자면 문제를 확실하게 이해하고 그 문제를 해결하기 위해 단계를 쪼갠다. 그리고 다시 점검한다. 쉽게 그리고 꼼꼼하게 문제를 해결하는 방법이다. 다음글은 문제 이해, 그 다음단계에서 문제를 해결하는 여러가지 방법을 소개하려고 한다. 좀 더 구체적인 방법론이 될것이다.

# 3. 문제 해결 방법론

문제를 해결하기 위해서 다양한 방법이 있다.

**Multiple pointers**: Creating pointers or values that correspond to an index or position and move towards the beginning, end or middle based on a certain condition. Very efficient for solving problems with minimal space complexity as well.

So Instead of having one pointer toward one direction, we’ve got two pointers toward two directions which takes much less iteration compared to one pointer.

**Sliding window**: this pattern invovles creating a window which can either be an array or number from on position to another. Depending on a certain condition, the window either increases or closes(and a new window is created) Very useful for keeping track of a subset of data in an array/string etc.

So basically window can cover for certain position inside data. So everytime you move through the data, you all you care about is to deal with edges of the window. I think you can also think of window as scope you are looking inside data structure.

**Divide and Conquer**: This pattern invovles dividing a data set into smaller chunks and then repeating a process with a subset of data. This pattern can tremedously decrease time complexity. For example, like binary search. instead of looping through every elements, you take the middle one and compare if it is bigger than what you are looking for.
