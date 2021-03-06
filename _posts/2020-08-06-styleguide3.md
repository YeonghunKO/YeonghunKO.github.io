---
title:  "깃헙포스트 어떻게 작성하는지 예시 3"
excerpt: "카테고리, 태그"

categories:
  - github
tags:
  - style guide
  - 
  - 
last_modified_at: 2020-08-13T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---
{% include toc %}

이번 포스팅은 나중에 글 쓸때 참고할 용도로 작성하는 포스팅입니다.

다양한 마크다운 문법과 테마에서 지원하는 기능들을 간단하게 미리볼 수 있습니다.

본 포스팅은 지속 업데이트 될 수 있습니다.
{: .notice--info}

## 제목

# # H1
{:.no_toc}
## ## H2 
{:.no_toc}

### ### H3
{:.no_toc}
#### #### H4
{:.no_toc}
##### ##### H5
{:.no_toc}
###### ###### H6
{:.no_toc}
## 인용

> `>`
>> `>>`
>>> `>>>`
>>>> `>>>>`  

...

## 리스트

1. 1번
2. 2번
3. 3번

```markdown
* 항목
* 항목
  * 요소
  - 요소
  + 요소
    * 요소 안에 또 요소
      * 안에 한개더
```

* 항목
* 항목
  * 요소
  - 요소
  + 요소
    * 요소 안에 또 요소
      * 안에 한개더

## 코드 강조

~~~md
```python

for i in data:
  print(i)
  
def add(a,b):
  return a+b
  
print('hello world!')

```
~~~

```python
for i in data:
  print(i)
  
def add(a,b):
  return a+b
  
print('hello world!')
```

## 강조

**\*\*Bold\*\***

\_\___Bold2__\_\_

\~\~~~취소선~~\~\~

\__기울임_\_

\**기울임2*\*

## 링크  

`<http://facebook.com/>`
<http://facebook.com/>

`[googlelink](https://google.com)`
[googlelink](https://google.com) 

## 이미지

`![alt text](\assets\img\github-blog-start\sky.JPG)`
![alt text](\assets\img\github-blog-start\sky.JPG)

## 표

```md
| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
```

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |

## 버튼

[Default Button](#){: .btn}
[Primary Button](#){: .btn .btn--primary}
[Success Button](#){: .btn .btn--success}
[Warning Button](#){: .btn .btn--warning}
[Danger Button](#){: .btn .btn--danger}
[Info Button](#){: .btn .btn--info}
[Inverse Button](#){: .btn .btn--inverse}
[Light Outline Button](#){: .btn .btn--light-outline}

```markdown
[Default Button Text](#link){: .btn}
[Primary Button Text](#link){: .btn .btn--primary}
[Success Button Text](#link){: .btn .btn--success}
[Warning Button Text](#link){: .btn .btn--warning}
[Danger Button Text](#link){: .btn .btn--danger}
[Info Button Text](#link){: .btn .btn--info}
[Inverse Button](#link){: .btn .btn--inverse}
[Light Outline Button](#link){: .btn .btn--light-outline}
```

[X-Large Button](#){: .btn .btn--primary .btn--x-large}
[Large Button](#){: .btn .btn--primary .btn--large}
[Default Button](#){: .btn .btn--primary }
[Small Button](#){: .btn .btn--primary .btn--small}

```markdown
[X-Large Button](#link){: .btn .btn--primary .btn--x-large}
[Large Button](#link){: .btn .btn--primary .btn--large}
[Default Button](#link){: .btn .btn--primary }
[Small Button](#link){: .btn .btn--primary .btn--small}
```

## Notice

```markdown
**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice}` class.
{: .notice}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--primary}` class.
{: .notice--primary}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--info}` class.
{: .notice--info}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--warning}` class.
{: .notice--warning}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--success}` class.
{: .notice--success}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--danger}` class.
{: .notice--danger}


{% raw %}{% capture notice-text %} {% endraw %}
You can also add the .notice class to a div element.

* Bullet point 1
* Bullet point 2
{% raw %}{% endcapture %}{% endraw %}

<div class="notice--info">
  <h4>Notice Headline:</h4>
  {% raw %}{{ notice-text | markdownify }} {% endraw %}
</div>
```


**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice}` class.
{: .notice}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--primary}` class.
{: .notice--primary}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--info}` class.
{: .notice--info}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--warning}` class.
{: .notice--warning}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--success}` class.
{: .notice--success}

**Watch out!** This paragraph of text has been [emphasized](#) with the `{: .notice--danger}` class.
{: .notice--danger}


{% capture notice-text %}
You can also add the `.notice` class to a `<div>` element.

* Bullet point 1
* Bullet point 2
{% endcapture %}

<div class="notice--info">
  <h4>Notice Headline:</h4>
  {{ notice-text | markdownify }}
</div>

## 정의
사과 나무
: 사과나무는 장미목 장미과 배나무아과 사과나무속에 딸린 종이다. 4월에서 5월 사이에 꽃을 피운다. 열매는 8~9월에 꽃받침이 자라면서 녹색 또는 붉은색으로 생긴다. 70~100여 년간 살고 경제적 가치가 있는 열매를 생산하는 시기는 40~50살 쯤이다. 그 열매는 사과라 하며, 세계적으로 가장 널리 재배되는 과일 품종 가운데 하나이다. 평과라고도 한다.

## 수평선

`---`
---
{:.no_toc}

## (축)약어



```
HTML은 하이퍼텍스트 마크업 언어(HyperText Markup Language, 문화어: 초본문표식달기언어, 하이퍼본문표식달기언어)라는 의미의 웹 페이지를 위한 지배적인 마크업 언어다.

*[HTML]: HyperText Markup Language
```
HTML은 하이퍼텍스트 마크업 언어(HyperText Markup Language, 문화어: 초본문표식달기언어, 하이퍼본문표식달기언어)라는 의미의 웹 페이지를 위한 지배적인 마크업 언어다.

*[HTML]: HyperText Markup Language

## 주석
```
{::comment}
이곳은 표시되지 않습니다.
{:/comment}

{::comment}이곳 또한 표시되지 않습니다.{:/}
```

{::comment}
이곳은 표시되지 않습니다.
{:/comment}

{::comment}이곳 또한 표시되지 않습니다.{:/}

## 각주
페이지 최하단에 표시되어집니다.

각주1 [^1], 각주2 [^2]
 
[^1]: 각주 내용 1
[^2]: 각주 내용 2