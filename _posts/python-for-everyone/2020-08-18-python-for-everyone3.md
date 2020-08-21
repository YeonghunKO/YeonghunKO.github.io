---
title:  "Python for everyone - week 5, week 6(if, try and except, def 함수)"
excerpt: "Python for everyone - week 5, week 6"

categories:
  - python
tags:
  - if
  - 
  - 
last_modified_at: 2020-08-18T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

# 1. Week 5

If 문을 배웠다. 말그대로 조건이 부합할때 indent된 코드를 실행하고 아니면 if 문 밖으로 나가 그 밑에 있는 코드를 실행한다. 아래의 코드를 살펴보자 

```python
x = 5 
if x < 10:
   print('Smaller')
if x > 20:
   print('Bigger')

print('Finis')
```

x가 5라고 하자. 그리고 컴퓨터는 밑에 있는 코드를 자동으로 읽어내려 갈 것이다. x가 10보다 작으면 smaller 라고 입력하고 20보다 크면 bigger라고 입력하라는 if 문이 두가지 연달아 적혀는것이다.  

그 다음 배울것은 elif 라는 기능이다. else 와 if의 합성어라고 보면된다. 앞의 조건문이 거짓일 경우 elif가 발동된다. 만약 elif에서 참이라면 그 뒤의 조건문은 작동하지 않는다. 

```python
x = 15
if x < 2:
   print('Smaller')
elif x < 10:
   print('Medium')
elif x < 20:
   print('Big')
elif x < 40:
   print('Large')
else :
    print('Ginormous')

```

이번에는 try , except 문을 알아보자. 이것도 말그대로 try 뒤의 코드를 실행하되 traceback 이 나오면 except 뒤에 있는 코드를 실행하라는 말이다. 

```python
num = input('Enter the number: ')
try:
   istr = int(num)  # int는 괄호안에것을 정수로 바꾸어 계산되게끔 준비하게 해준다. 
except:
   istr = -1

```

## 1-1. 영어문장 정리

![if](https://yeonghunko.github.io/assets/img/coursera-python/if.png){:class="img-fluid"}

- Then it comes back and says, if x is greater than 20, this one evaluates to false, and so that skips it.(If x > 20: print('Bigger)

- Remember 'Equals(=)' is an assignment statement, it has kind of direction. X = 1, right? X = 1. That puts 1 in X. This, if you say x == 1, you're asking the question. Is X equal to 1 and it doesn't harm X. So that's probably , it takes while.

- We always use indentation in other programming languages to mentally keep track of blocks of text, but it's not where the programming language will complain if you get it wrong. So you have to sort of think why did you increase the indent, which is like if, after an 'if' or a 'for' or a 'while' statement, which we'll see in a bit. You maintain the indent, which means you stay the same, or then you de-indent or you reduce the indent back, and that is the way to end a block.


![elif](https://yeonghunko.github.io/assets/img/coursera-python/elif.png){:class="img-fluid"}

- As soon as one of the block is triggered, it executes the block right away. And the next thing to do is exit right out of the block.(If loop)


![try](https://yeonghunko.github.io/assets/img/coursera-python/try.png){:class="img-fluid"}


- And so this is a way to eliminate or catch a traceback. Something that would otherwise be a traceback.(Try and except)

- And then we put the dangerous line in there, and then we put 'except'. And then the except is kind of like an else, an if-then-else, but what it really is 'The code' that Python will execute if something goes wrong. 
	


# 2. Week 6

Def 함수를 배웠다. definition의 약자로 내가 정의한 함수이다. 내가 나름대로 코드를 프로그래밍해서 이름을 붙이는것이다. 

```python

def thing():
    print("Hello world")
    print("This is python")
thing()
```

그리고 정의한 이름을 입력하면 그 밑에 딸린 코드를 기억해내서 자동으로 실행되는 것이다.  

max와 min 기능도 있다. 최대와 최소값을 찾아주는 것이다.

```python
x = [1,4,3,5,6,4674,]

max(x)
min(X)
```

이번엔 def 와 elif를 조합해서 코드를 짜보겠다. 그리고 parameter 라는 개념도 같이 알아보겠다.

```python
def greet(lang):
    if lang == 'es':
       print('Hola')
    elif lang == 'kr':
       print('안녕하세요')
    else:
       print('Hello')
>>> greet('es')
Hola
>>> greet('kr')
안녕하세요
```

여기서 lang 이 parameter이고 es 를 argument 라고 한다. 

## 2-1. 영어문장 정리

![def](https://yeonghunko.github.io/assets/img/coursera-python/def.png){:class="img-fluid"}


- So the new keyword that we've got is 'def', d-e-f, which stands for start the definition of a function, define the function. Def is the keyword, it ends in a colon, just like lots of things that start an indented block. You get the name the thing that you're storing, I call it thing for now. So next time we invoke 'the thing', computer will print out what's inside the def function. 

- Max function: So here's the function we haven't played with yet . It is called 'max function. It's also another one of Python's built-in functions and this is an example of an argument. We're passing in a string and we're asking max finds the largest of something and in this case, it's going to scan through this string and find the largest letter.\

- There's some code inside here that runs, reads through the argument, comes in and then it reads through and looks at that stuff, reads some stuff and then sends us back the answer, which is 'w', which is this is called return. The w is the residual value, once the max function is executed


![string](https://yeonghunko.github.io/assets/img/coursera-python/string.png){:class="img-fluid"}


- Here's the code called 'int' function. We pass sval in, which is 1-2-3 the string and we get back 123 the integer then that replaces this in the function and then 123 integer is assigned into ival. 

![hello](https://yeonghunko.github.io/assets/img/coursera-python/hello.png){:class="img-fluid"}

- Now this print does a de-indent, so that sort of blocks this off. That little bit inside the blcok is the function, that stuff's been copied up to there, and now it continues on and it prints Yo.  Then programm is done. What happened to these lines of code? And the answer is they never executed, they never executed. And that's because the def statement doesn't automatically run the code. You must invoke.

![parameter](https://yeonghunko.github.io/assets/img/coursera-python/parameter.png){:class="img-fluid"}


- We expect that when this is invoked or called, we want one parameter. So then we call greet, and again, Python remembers to comeback to here. And the it fires up to here and starts this line of code. So running through first line of code which is greet(en), it's like lang is not es, lang is not fr, so this code runs, out comes Hello, and then we're done. Whatever the first parameter is, I will use lang within here, I'll use lang to refer to the first parameter.  
 
Lang itself is not really a variable in that there is no piece of memory that lang belongs in. It is really sort of an alias of something else.
