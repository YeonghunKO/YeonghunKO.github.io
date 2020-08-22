---
title:  "Python for everyone - week 7(while,if,for 문의 조합)"
excerpt: "Python for everyone - week 7"

categories:
  - python
tags:
  - for loop
  - 
last_modified_at: 2020-08-18T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

> 1. 나름대로 개념 정리.  
> 2. 각 개념에 따른 예문 정리.  
> 3. 그리고 중간중간 알아두면 좋겠다고 생각하는 프로그래밍 관련 영어 표현, 단어 정리


# 1. Week 7

## continue and break

continue/break 기능이다. continue 는 반복문의 처음으로 돌아가 다시 반복문을 진행한다. break는 반목문을 빠져나가는 기능을한다. 

```python
while True:
    line  = input(':  ')
    if line[0] == '#' :
        continue
    if line == 'done' :
        break
    print(line)
print('Done!')
```

## index , for 문

`line[0]` 은 첫번째 글자나, 덩어리를 말한다. 만약 `x = [345,25,345,아,2]` 라고 할때 각 자리의 index는 0,1,2,3,4,5 이다. 따라서 `x[2] = 345` 이다

따라서 input의 값이 맨처음 #을 입력한 값이 나온다면 다시 위로올라가 input을 입력하고 그게 아니면 if 문이 거짓이 되어  print(line) 으로 프로그래밍의 타겟이 이동한다. 그라고 `done` 을 누르면 바로 break 되어 `print('Done!')` 으로 이동한다.

For 문이다. 리스트안에 있는 원소하나하나를 일일이 읽어나가며 원소를 수정한다. 

```python
for i in [5,4,3,2,1] :
    print(i)
print('Blast off!')
```

`i`는 임의로 정해도 된다. 근데 네이밍은 의미있는것으로 정의해야한다. 누가보더라도 이해가 되게끔 말이다. 그래서 `count` 정도가 낫겠다.  
 그리고 `in` 안에 있는 숫자들을 차례대로 프린트한다. 사람손으로 일일이 하기 힘든것을 자동으로 처리한다. 그리고 더이상 처리할 원소가 없을때 반복문을 나가 밑에 있는 `blast off`를 실행한다.


## for, if, elif 의 조합. 그리고 None

그럼 이번엔 `for`, `if`, `elif` 그리고 `None`(無, 값이 없는 빈 공간이다.) 를 조합하여 가장 작은 수를 찾아내는 프로그램을 만들어보자.

```python
smallest = None
print('Before')
for value in [9, 41, 12, 3, 74, 15]
     if smallest is None :
          smallest = value
     elif value < smallest :
         smallest = value
     print(smallest, value)
print('After', smallest)

>>>After 3
```

맨처음 smallest 는 None이니 처음 원소 9가 자동으로 smallest가 된다. 이후 41 부터는 elif의 조건을 거치게 된다. 그래서 smallest = 9이므로 3을 거치기 전까지는 아무런 변화도 일어나지 않게 된다. 

</br>

# 1-1. 영어문장 정리

- repeated steps(while): And as long as n greater than 0 remains true, it will dive in and do this again. So it dives in and prints out 4, and then it subtracts to 3 and goes up(While loop

![continue](https://yeonghunko.github.io/assets/img/coursera-python/continue.png){:class="img-fluid"}

- So it skips out of the loop, but it doesn't skip to the line beyond it, it skips back up to the top(continue method). So break says get out and continue says don't do the rest of this iteration but go up and do the next iteration.	


![for](https://yeonghunko.github.io/assets/img/coursera-python/for.png){:class="img-fluid"}

- And it just guarantees that it's going to run this once, code once, for each of these five variables. Or that's another way to draw that would be, you know, run it once for 5, run it once for 4, run it once for 3, …(for loop)


![largest](https://yeonghunko.github.io/assets/img/coursera-python/largest.png){:class="img-fluid"}

- And I'm going to set it to -1 at the beginning. And before the loop starts, remember I said there's stuff we do at the beginning of the loop , and then stuff we do during the loop. And then our payoff is after the loop, after the loop Okay? So Before the loop we set the largest we've seen so far, which we've seen nothing, so we say -1, then we print out. Then we have an iteration variable, the_num is going to go through successively 9,41,12,3,74 (Largest_so_far = - 1 . For loop)


![smallest](https://yeonghunko.github.io/assets/img/coursera-python/smallest.png){:class="img-fluid"}

- We think of None as the absence of a value. So None types have one thing, None. The lack of a value, okay? And so, what we're going to do instead, is in our smallest variable, that we're going to do. We're going to say, you know what, before this loop starts, the smallest number we've seen is nothing. We've seen no numbers whatsoever. Before this loop starts, the smallest number we've seen is nothing. And that's going to be our marker to indicate that we've seen no numbers. Okay? This is kind of like the found code where we set found to be False and then later we set found to be True.(Use 'None')  

- To use this None and then have a little bit of code that triggers the first time through the loop to get your sort of loop-carried variable setup.(반복문 이 돌아가면서 알아서 형성되는 값들이다.)
