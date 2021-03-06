---
title:  "<1> 깃헙블로그 시작하기!!"
excerpt: "깃헙블로그 기본뼈대 만들기"

categories:
  - github
tags:
  - 깃헙블로그
  - ruby
  - jekyll
last_modified_at: 2020-08-12T08:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

# 깃헙블로그 글올리기

# 깃헙블로그 ?
<p>개발자라면 , 개발자를 준비하고 있는 사람이라면 깃헙블로그 하나쯤은 갖고 있는것이 좋다. 그 이유는 그 블로그에 기록된 것을 보고 이 개발자의 능력, 성향, 습득한 기술을 파악하는 문화가 있기 때문이다. 그래서 주저리주저리 자소서를 쓰지 않고 블로그 링크하나 보낸다. 
</p> 

또한, 개발자라면 기록하는 습관은 기본이다. 그리고 유용한 정보를 다른 사람과 공유함 으로써 시너지 효과를 일으키는 것도 정말 중요하다.  

따라서 이 블로그는 오늘 배운것, 고쳐야 할 것, 자잘한 일상을 기록하고, 앞으로 필요할때마다 도서관 처럼 꺼내쓰는 공간일 뿐만 아니라 다른 개발자와 소통하는 공간이기도 하다. 

<p>또한 깃헙블로그를 만드므로써 깃헙과 마크다운문법을 자연스럽게 익힐 수 있으니 일석 이조라고 할 수 있다. 그럼 깃헙블로그를 만드는 방법을 살펴보자!</p>

## 1. 자신의 깃헙블로그에 리파지토리를 만들기

<p>이때 중요한것은 깃헙의 리파지토리 이름이 자신의 username을 차용해야한다. 아니면 404found 페이지가 뜰 수 있다. ex) username.github.io</p>

![repository](https://yeonghunko.github.io/assets/img/github-blog-start/my-repository.png){:class="img-fluid"}


## 2. 테마를 포크함

<p>Jekyll에 있는 테마를 가져온다. 그중에 가장 깃헙시스템을 잘 체험할 수 있는 minimal mistakes를 사용해보겠다.</p>

<p>구글에서 minimal mistakes를 타이핑하면 깃헙블로그가 하나 나온다. 그럼 접속해서 오른쪽 상단에 있는 fork 를 클릭한다. </p>

<p>그리고 앞서 내가 만들었던 repository를 클릭하면 그쪽으로 모든 파일이 복사된다.</p>

![fork](https://yeonghunko.github.io/assets/img/github-blog-start/fork.png){:class="img-fluid"}

## 3. 리파지토리 내컴퓨터에 복사

<p>내 컴퓨터에 복사하면 로컬서버에서 블로그에 업로드할 수 있기 때문에 거의 필수라고 할 수 있다. 복사하는 방법은 깃헙 데스크톱을 이용, 컴퓨터 자체에서 실행하는 터미널, 또는 git bash라는 툴을 사용해서 복사가능한데 필자는 깃헙 데스크톱이 더 멋져보여서 데스크톱을 사용하기로 한다.</p>

<p>우선 깃헙 홈페이지에 들어가 해당 리파지토리에 접속한다.</p>

![gitdesktop](https://yeonghunko.github.io/assets/img/github-blog-start/gitdesktop.png){:class="img-fluid"}

<p>그럼 깃헙 데스크톱이 열린다(없으면 자동 설치되기 시작한다.) </p>

<p>그 다음 깃헙 데스크톱에서 file을 누른다음 clone을 누르고 자신이 복사하고 싶은 리파지토리를 클릭하고 복사 장소를 선택한다음 확인을 누르면 그 장소에 리파지토리와 같은 이름의 폴더가 생성된것을 확인 할 수 있다.</p>

![clone1](https://yeonghunko.github.io/assets/img/github-blog-start/clone1.png){:class="img-fluid"}

<p></p>

![clone2](https://yeonghunko.github.io/assets/img/github-blog-start/clone2.png){:class="img-fluid"}

<p>사실 데스크탑을 설치하여 리파지토리를 내 컴퓨터에서 복사하여 블로그를 관리하는 이유는 변경사항을 로컬사이트를 통해서 바로바로 알 수 있게 할 뿐만 아니라, 데스크탑을 통해서 바로바로 git push 와 pull을 할 수 있기 때문</p>

<p>데스크탑이 아니라면 터미널을 통해 명령어를 입력하여 git push를 해줘야 할 거다(내가 알기로는)</p>

## 4. RUBY 와 Jekyll을 다운로드

### RUBY 와 Jekyll이란?

<p>Jekyll은 정적인 웹사이트 생성기로 ruby 라는 언어가 필요하다. 그리고 마크다운 이라는 방식으로 글쓰기가 가능하다.</p>

<p>지금 글을 작성하는 이 웹페이지도 Jekyll이라는 도구로 만들었다. 그럼 우선 ruby를 다운받자.</p>

### RUBY 와 Jekyll 다운로드하기
[루비 다운로드](https://rubyinstaller.org/downloads/)

![ruby](https://yeonghunko.github.io/assets/img/github-blog-start/ruby.png){:class="img-fluid"}

<p>ruby와 devikit(루비를 사용하는 툴)을 동시에 받는것을 추천한다. 설치란에 "<strong>Use UTF-8 as default external encoding"</strong>란에 체크하자!</p>

<p>그리고 설치가 끝났으면 Start Command Prompt with Ruby 를 실행하고 아래와 같은 명령어를 입력하여 Jekyll을 설치한다. 그리고 설치하면 Jekyll 의 버전을 확인한다.</p>

```bash
gem install jekyll bundler
```

```bash
$ bundle exec jekyll -v
jekyll 4.0.0
```

<p>Jekyll을 설치했으면 이제 Jekyll을 이용해 로컬서버를 오픈할 시간이다. 터미널을 켜서 앞서 깃헙데스크탑을 통해 형성한 폴더로 이동하자(Change Directory) 그래서 아래의 명령어를 입력해준다</p>

```bash
cd..\username.github.io
```

<p>블로그 폴더에 접속했으면 아래의 명령어를 또 다시 입력해주자</p>


```bash
bundle exec jekyll server
```


<p>그리고 웹페이지에 들어가 다음 주소를 입력하면 블로그를 로컬서버를 통해 들어갈 수 있다.</p>

<code class="highlighter-rouge">localhost:4000</code> 

<p>여기서 자잘한 변동사항을 확인한다. 그리고 블로그 수정작업이 끝나면 터미널에 'ctrl+c' 를 입력해 로컬서버를 닫는다.</p>


## 5.블로그 기본 정보 변경(_config.yml 파일 수정)

<p>자 그럼 이제 블로그의 기본 뼈대는 만들었으니 살을 붙일 시간이다. 우선 제일 개괄적인 정보부터 추가하자. 블로그 이름, 주인장의 정보, 연락처, 로고 같은 정보 말이다. 그러한 대략적인 정보는 _config.yml 파일에서 수정가능하다.(앞으로 언급하게 될 모든 파일은 에디터로 열고 수정할 수 있다. 필자가 개인적으로 추천하는 에디터는 "visual studio code" 이다.</p>

<p>config 파일을 열면 사용자가 수정하기 쉽게 설정해놓았다.</p>

```bash
# theme                  : "minimal-mistakes-jekyll"
# remote_theme           : "mmistakes/minimal-mistakes"
minimal_mistakes_skin    : "air" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise" #테마를 설정한다

# Site Settings
locale                   : "en-US"
title                    : "노력도 재능이다" #블로그 상단, 블로그 제목을 설정한다
title_separator          : "-"
subtitle                 : # site tagline that appears below site title in masthead
name                     : "Yeonghun" 
description              : "모든것을 흡수하려는 마음가짐" 
url                      : "YeonghunKO.github.io" # 리파지토리 이름을 적는다.
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : # GitHub username/repo-name e.g. "mmistakes/minimal-mistakes"
teaser                   : "https://yeonghunko.github.io/assets/img/cover.JPG" # full path를 적어준다.
logo                     : "/assets/img/tourist.png" # path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"
masthead_title           : # overrides the website title displayed in the masthead, use " " for no title
```

<p>그럼 이번엔 주인장의 세부 정보를 수정해보자. 블로그를 열면 왼쪽에 뜨는 프로필 정보를 수정하는 것이다.</p>

```bash
# Site Author
author:
  name             : "Yeonghun" 
  avatar           : "/assets/img/tourist.png" # path of avatar image, e.g. "/assets/images/bio-photo.jpg" #프로필 사진.
  bio              : "컴퓨터랑 놀고싶은 사람"
  location         : "South Korea"
  email            : "yhko1988@gmail.com"
```

<p>그럼 대충 내 블로그 다워지긴 했다. 나중에 얘기할 댓글, Table Of Contents(TOC), 글 작성 날짜 표시 같은 기능을 추가할때도 _config파일에서 수정하면 된다.</p>

## 6. 로컬서버이용하기, 그리고 깃 푸시하기

<p>앞서말한대로 변경사항이 적용되었는지 로컬 서버를 통해 바로바로 확인 할 수 있다.</p>

<code class="highlighter-rouge">bundle exec jekyll server</code> 

<p>코드를 입력한다음 웹페이지에 <code class="highlighter-rouge">localhost:4000</code> 을 입력해서 변경사항을 확인하자. </p>

<p>변경사항이 확인되었으면 이제 진짜로 공식웹사이트에 변경사항을 등록해야한다. 이때 깃헙데스크톱을 통해 깃푸시를 하는 것이다.</p>

<p>깃헙 데스크톱에 변경사항이 자동으로 업로드 된다. 그럼 업로드 된 내용을 알아 보기 쉽게 잘 요약하고 commit을 한다음 상단에 push 버튼을 누르면 깃헙 홈페이지 리파지토리에 업로드 되고, 내 깃헙블로그에 적용된다. 그리고 실제 홈페이지에 나타나기 까지 시간이 좀 걸릴 수 있으니 5분정도 기다려 보자. 그리고 에디터 툴에서 저장을 해야 깃헙 데스크톱에 업데이트되니 저장하는것을 생활화 하자!</p>

![gitpush1](https://yeonghunko.github.io/assets/img/github-blog-start/gitpush1.png){:class="img-fluid"}

![gitpush2](https://yeonghunko.github.io/assets/img/github-blog-start/gitpush2.png){:class="img-fluid"}

<p>이렇게 해서 깃헙 블로그를 만들고 수정하는 법을 얼추 배워봤다. 다음 글에서는 댓글기능 추가하는 법을 알아보자.(매우 간단하다)</p>
<p></p>




