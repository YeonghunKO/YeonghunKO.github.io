---
title:  "Python data structure - week 1, 3, 4(for, while 문 그리고 파이썬의 기본 개념)"
excerpt: "Python data structure - week 1, 3, 4"

categories:
  - python
tags:
  -
  - 
last_modified_at: 2020-08-19T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.  
> 2. 각 개념에 따른 예문 정리.  
> 3. 그리고 중간중간 알아두면 좋겠다고 생각하는 프로그래밍 관련 영어 표현, 단어 정리


# 1. Week 1, 3, 4

## string library(소문자)

string library 라는게 있다. 도서관처럼 꺼내어 쓸수 있는 built-in 기능입니다. 특정 기능을 수행하기위해 코드를 짤필요가 없습니다. 


```python
greet = 'Hello Bob'
lo = greet.lower() # 자동으로 소문자로 바꾸어주는 라이브러리 기능이다.
print(lo)
>>>hello bob 
print(greet)
Hello Bob
```

## file handle

file handle 이라는게 있다. 그건 어떤 파일로 통하는 관문이라고 보면 된다. file handle 안에 정보가 들어있지는 않고 정보를 여는 열쇠이다. 

```python
xfile = open('mbox.txt')
for cheese in xfile: # xfile을 열쇠로 사용해 for 문을 돌릴 수 있다.
    print(cheese)
```

## list 를 이용해서 평균 구하기

다음은 list 객체를 이용해 평균을 구해보자. 

```python
numlist = list()
while True :
    inp = input('Enter a number:')
    if inp == 'done' : break
    value = float(inp) # 입력한 숫자들을 소수점 정수로 바꾸어줌
    numlist.append(value) # 그 숫자들을 리스트에 추가하는 method

average = sum(numlist)/len(numlist)
print('Average:', average)
```

## 영어문장 정리

- So like I said, you can do interactive in Python or you can run a script.(Interactive: You type directly to python one line at a time and it responds.)  


![library](https://yeonghunko.github.io/assets/img/coursera-python/library.png){:class="img-fluid"}

- This is, this is run a function lower() that's part of the string object, of the string class, that is going to give us back a lowercase copy. So what this functionally does, it says, make a copy of greet but all lowercase and return it to us without changing or harming the string, and then we're going to store that into zap. Because string is immutable 


![handle](https://yeonghunko.github.io/assets/img/coursera-python/handle.png){:class="img-fluid"}

- So that just says treat a file handle as a sequence of lines, and allow us to iterate through it automatically using 'for' loop. 

![average](https://yeonghunko.github.io/assets/img/coursera-python/average.png){:class="img-fluid"}

- So what i would do then is i would accumulate these values in a list. So I'm using a data structure now rather than just logic. So this is kind of an algorithm that's carefully constructed to produce the count and the sum when it's all said and done.  Now what we're going to do is we're going to use the data structure to solve that same problem. And so we'll say hey, let's make an empty list because we're going to accumulate some numbers.

