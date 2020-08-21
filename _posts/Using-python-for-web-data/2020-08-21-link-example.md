---
title:  "Using python to access data bases example - 링크타고 들어가기 예제"
excerpt: "링크타고 들어가기 예제"

categories:
  - python
tags:
  - 
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


# 1. example

브라우저에 링크가 수십개 있다. 그중 18번째 링크를 7번 클릭하면 어떤 정보가 나오는지 코딩해야한다. 이건 프로그래밍하기 너무 어려워서. 며칠을 붙잡아도 안풀려서 stackflow를 참고하였다.

```python
import urllib.request, urllib.parse, urllib.error
from bs4 import BeautifulSoup
import ssl

ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

url = input('Enter-')
html = urllib.request.urlopen(url).read()
soup = BeautifulSoup(html, 'html.parser')

for link in range(7): # 7번 반복하도록 range() 함수를 사용함(7,6,5,...1).
    tag = soup('a') # 링크만 따로 뽑아내도록 함.
    Tg = tag[17] # 18번째 링크 클릭!
    lin = Tg.get('href',None) # 링크에서 링크만 뽑아냄
    url = str(lin) # 글자로 전환
    print(url)
    html = urllib.request.urlopen(url).read()#Get URL ready to open. 그러고는 그 url을 다시 분석하고 다듬는 작업.
    soup = BeautifulSoup(html, 'html.parser')#Activate URL(?) 그러고는 그 url을 다시 분석하고 다듬는 작업.
```



