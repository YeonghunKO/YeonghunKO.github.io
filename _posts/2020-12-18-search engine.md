---
title:  "<7> 검색엔진 추가"
excerpt: "algolia"

categories:
  - github
tags:
  - 깃헙블로그
last_modified_at: 2020-08-14T09:06:00-05:00

toc: true
toc_label: "목차"
toc_icon: "cog"
toc_sticky: true
---

# 검색엔진 추가

사실 config.yml 파일에서 `search:true` 하고 검색하면 검색 결과가 잘 나왔으나, 클릭하면 404에러가 떠서 고민했었다. 그러다 `search_provider` 를 설정해줘야 하는것을 알았고 algolia를 이용해 검색기능을 완성했다.  

1. 우선 **[aloglia](https://www.algolia.com/)** 에 접속하여 회원가입을 하고 index를 만들어주자.  

![index](https://yeonghunko.github.io/assets/img/github-blog-start/index.png){:class="img-fluid"}

2. configuration 에 들어가서 add searchable attribute 를 누르고 설정해주자.  

![configuration](https://yeonghunko.github.io/assets/img/github-blog-start/configuration.png){:class="img-fluid"}

3. 그리고 가장 상위폴더에 저장된 Gemfile(docs안에 있는 게 아니다)에 들어가서 아래의 코드를 입력해주자(alolia gem 추가)
```ruby
group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-sitemap"
  gem "jekyll-gist"
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jemoji"
  gem "jekyll-include-cache"
  gem "jekyll-algolia" # 추가!
end
```
4. 명령프롬트에 들어가서 `bundle install` 을 입력해 gem을 설치해주자  

5. config.yml 에 들어가서 아래 항목을 채워넣자
```yml
search_provider          : algolia # lunr (default), algolia, google
algolia:
  application_id         :  # YOUR_APPLICATION_ID
  index_name             :  # YOUR_INDEX_NAME
  search_only_api_key    :  # YOUR_SEARCH_ONLY_API_KEY
  powered_by             : # true (default), false
```
API 관련된 정보는 algolia 왼쪽 dashboard 에서 확인가능하다.

![api](https://yeonghunko.github.io/assets/img/github-blog-start/api.png){:class="img-fluid"}

6. 그러고 명령프롬프트에 가서 아래의 코드를 입력해주면 끝!  

```command
set ALGOLIA_API_KEY=your_admin_api_key
bundle exec jekyll algolia
```

그럼 이렇게 검색창에 입력하면 검색결과가 뜨면서 검색단어가 하이라이트까지 되는것을 볼 수 있다. 결과를 클릭해도 404가 안뜨고 문제없이 해당결과글에 접속가능하다!!  

![search](https://yeonghunko.github.io/assets/img/github-blog-start/search.png){:class="img-fluid"}
