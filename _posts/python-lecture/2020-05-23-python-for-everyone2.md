---
title:  "Python for everyone - week 3, week 4"
excerpt: "Python for everyone - week 3, week 4"

categories:
  - python
tags:
  - while loop
  - 
last_modified_at: 2020-08-17T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.  
> 2. 각 개념에 따른 예문 정리.  
> 3. 그리고 중간중간 알아두면 좋겠다고 생각하는 프로그래밍 관련 영어 표현, 단어 정리


# 1. Week 3

프로그래밍은 내가 글을 적는 것이랑 비슷하다. 글과 다른점이 있다면, 컴퓨터가 그 글을 한 문장 한 문장 빠짐없이 정독하고 그것을 해석하여 결과를 창에 나타내는 것이다. 예를 들어보자.

```python
x = 2
x = x + 2
print(x)
```

맨 처음엔 x = 2 라는 변수를 정한다고 글을 적었고. 그 밑에 다시 정보를 추가한다. x 에 2를 더한 값이 새로운 x 라고. 그럼 전에 x 는 overwritten 되어 사라지고 새로운 x 가 탄생한다.  
그리고 x 값을 나타내라고 적는것이다. 이렇게 기존의 글로 이루어진 문장과는 완전 다른 형태의 방식으로 의미를 표현하게 된다. 굉장히 함축적이고 논리적이며 간결하다. 또한, 만국공통어라는 점이 차이다.   

그 다음엔, While 문을 배웠다. While 문은 들여쓰기 된 코드가 계속 반복되는 코드이다. 그리고 어떤 조건을 달게 되면 그 조건이 참을 유지하는 한 계속 들여쓰기 된 코드를 반복한다. 

```python
n = 5
while n > 0 :
    print(n)
    n = n - 1
print('Blast off')
```

위의 while 문은 무슨 뜻이나면, n 이 0 보다 크다면 무조건 아래의 코드(n = n - 1) 를 반복한다. 그리고 0보다 크기 않으면 while 문을 빠져나와 그 밑의 코드 print 문을 실행하게 되는 것이다. 역시나 컴퓨터는 내가 적은 글을 차례대로 해석한다. 쌍방으로 소통하는 느낌이다.

## 1-1. Week 3 영어문장 정리

- So like I said, you can do interactive in Python or you can run a script.(Interactive: You type directly to python one line at a time and it responds.)  

- And you'll notice that this is indented at the same level as the print statement.


![sentence](https://yeonghunko.github.io/assets/img/coursera-python/sentence.png){:class="img-fluid"}



- Each one of these is like a sperate line and we've got to get them right. And then we construct a paragraph out of a series of lines. And so in this particular example, we have another assignment statement that's sticking the number 2 into the variable x, retrieving that 2 back in, adding 2 to it and sticking that sum back into x. Print is a function and there is parameter x and that's going to cause 4 to be printed out.


![while](https://yeonghunko.github.io/assets/img/coursera-python/while.png){:class="img-fluid"}


- Now it comes up and asks this question - is zero greater than zero? Because n has become zero by the successive iterations through this loop(Using 'While loop' to count numbers until it blasts off.)


![wow](https://yeonghunko.github.io/assets/img/coursera-python/wow.png){:class="img-fluid"}

- This second paragraph says oh, as we read through the file, create a histogram that maps the number of words to the frequency of the words and each time you see a word, update the histogram so that we have a running total of all of the words, using a thing that we'll learn later called dictionaries.(위의 코드는 어떤 글이 적힌 파일을 입력하고 그 파일안에서 가장 많이 언급된 단어를 찾아내는 코드인데 나중에 다 이해하게 될 것이므로 걱정하지 말자.  그냥 파이썬을 통해 이러한 문장을 결합하여 이러한 기능을 가능하다는 것 정도만 알고 있으면 된다)

# 2. Week 4

input 기능을 배웠다. 말 그대로 어떤 정보를 직접 입력하게 하는 기능이다. 

```python
nam = input('Who are you?')
print('Welcome', nam)
```

'Who are you?' 라는 질문이 나오고 그때 내가 정보를 입력하면 'Welcome input 결과' 가 나온다.  

그 다음은 계산기능이다. 실제 파이썬은 간단한 계산기능을 수행 할 수 있다. 

```python
$ print(10 / 2)
>> 5.0
print(9 / 2)
>> 4.5
$ print(99 / 100)
>> 0.99
```

## 2-1. 영어문장 정리

- input 예시: And when Python comes running in here, it starts the input function, and the parameter to the input function is what's called a prompt.


- 계산 예시: Think about if you'd put in 9 divided by 2 in a calaulator, you wouldn't expect it to say 4. And it Python 2, it said 4, it actually truncated(shorten it by cutting off edge or top) , it actually threw this bit away. It didn't even round the numbers, it chopped them off.

- We've mostly seen print being printing one thing, but you can have as many things as you want with commas in print, and every comma adds a space, and so, it's kind of friendly.
