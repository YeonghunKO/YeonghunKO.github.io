---
title:  "Python data structure - week 5(dictionary)"
excerpt: "Python for everyone - week 5"

categories:
  - python
tags:
  - 
  - 
last_modified_at: 2020-08-20T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.  
> 2. 각 개념에 따른 예문 정리.  
> 3. 그리고 중간중간 알아두면 좋겠다고 생각하는 프로그래밍 관련 영어 표현, 단어 정리


# 1. Week 5

Dictionary: list와 비슷하지만 순서가 없다. 그리고 각 원소를 key라 부르고 key에 해당하는 value값이 존재한다.  
아래의 그림처럼 말이다.

```python
purse = dict()
purse['money'] = 12
purse['candy'] = 3 # 이런식으로 key와 value의 값을 설정해준다.
print(purse)
>>>['money' : 12, 'candy' : 3]
```

dict() 함수는 key , value 두가지 정보를 담고 있기 때문에 for 문에서 두가지 동시에 loop을 돌릴 수 있다. 이것을 two iteration 이라고도 한다.

```python
for k,v in purse.item() : 
    print(k,v)

>>>money 12
>>>candy 3
```
## 1-1. 영어문장 정리



![dict](https://yeonghunko.github.io/assets/img/coursera-python/dict.png){:class="img-fluid"}

- Whereas in the list, we had to append stuff, we use the index operator on the left-hand side of an assignment statement to indicate the key. So this ends up being the value and this is the key. And so we're putting 12 into the purse , but on the way in we're labeling it with money, right? And so 12 is going in, 12 is the value and we're putting it into purse, but we're storing it under money. 

We can update these variables. Dictionary contents are mutable. So we can go grab the old value, purse['candy'], which is a 3, add 2 to it, and then put a 5 back in. And then we can print this out, and then the 3 has been modified to become 5.


![counting](https://yeonghunko.github.io/assets/img/coursera-python/counting.png){:class="img-fluid"}

- We're going to grab the old value of our count for the particular word we're looking at, or 0, add 1 to it, and stick it back in.(Counts[word] = counts.get(word,0) + 1)


![keys](https://yeonghunko.github.io/assets/img/coursera-python/keys.png){:class="img-fluid"}


- SO whatever the value of the key-value pairs are in the dictionary, if you ask for the keys and you ask for the values a moment later, they come out in corresponding order. So Chuck maps to 1 , Fred maps to 42. Even though the order is not the same as the order that you originally put them in.

![double](https://yeonghunko.github.io/assets/img/coursera-python/double.png){:class="img-fluid"}


- No other language that i know of has the ability to do more than one iteration variable. So what happens here is we've given it two iteration variables. aaa goes through the keys and bbb goes through the , simultaneously, the values. As one is bouncing, the other ones are bouncing too

![pro1](https://yeonghunko.github.io/assets/img/coursera-python/pro1.png){:class="img-fluid"}


- That just makes the histogram right? And we're going to end up accumulating these counts over the entire file.  We're going to remember what the word was that we had that, where we saw the biggest number, we're remembering the word and we're going to remember the count. And then we'll do this a bunch of times and if we find later, much later, some thing that's got a little higher number, like 8, then we will fix that as well, okay? 

- So this runs all the way through all the things. And when it comes out bigword and bigcount, the residual stuff at the end of the loop will be the largest word and how many times. (combination between dict() , if, and for loops)

![pro2](https://yeonghunko.github.io/assets/img/coursera-python/pro2.png){:class="img-fluid"}


- And in a sense, by nesting(building inside) these two loops(outer and inner 'for' loops), we're going to hit all the lines.

- And '.items' is a method inside of all dictionaries that says give me the key-value pairs, and we need two iteration variables, so this is like an assignment statement for k and v, k and v take on the successive values for the key and the value, okay? (for k,v in di.items():)



