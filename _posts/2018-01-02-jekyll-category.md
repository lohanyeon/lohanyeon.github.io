---
title:  "jekyll 블로그 포스트 페이징"
date:   2018-01-01 09:04:23
categories: [etc]
tags: [github, jekyll]
comments: true
published: ture
---

 Ruby로 만들어져 있는 jekyll은 포스트에 대해 기본적으로 페이징, 카테고리 분류 기능이 없는것 같다.  
 페이징도 최상위 폴더의 __index.html에만(초기화면) 적용이 가능__ 하고 카테고리별로는 페이징 지원이 안된다.  
 여기저기 구글링하여 카테고리별 페이징 기능을 찾긴 하였으나 [jekyll-paginate-v2](https://pengpengto.gitlab.io/blog/tech/2017/06/08/jekyll-category_pagination.html)는 아직 github에서  지원이 되지 않는다고 한다. 

 *그래서 일단 노가다 식으로 카테고리를 구분해 보기로 한다.*

 + 블로그 루트 디렉토리 하위에 카테고리로 사용할 01.lion, 02.tiger 디렉토리를 만든다.
 + 루트디렉토리 하위의 index.html을 복사하여 ./01.lion ./02.tiger에 붙여넣기 한다.
```
 Kyuui-MacBook-Pro:yeonkh94.github.io lohan$ tree
.
├── 01.lion
│   └── index.html
├── 02.tiger
│   └── index.html
├── 404.html
├── Gemfile
├── Gemfile.lock
├── README.md
├── _config.yml
├── _posts
│   └── 2018-01-01-welcome-to-jekyll.markdown
├── _site
│   ├── 404.html
│   ├── README.md
│   ├── about
│   │   └── index.html
│   ├── assets
│   │   └── main.css
│   ├── feed.xml
│   ├── index.html
│   └── jekyll
│       └── update
│           └── 2018
│               └── 01
│                   └── 01
│                       └── welcome-to-jekyll.html
├── about.md
├── index.html
└── index.md
```

 + 붙여넣기 한 파일의 내용 중에 빨간 박스 부분을 수정한다. (/index.html의 맨 하단부분에 있던 페이징 부분은 삭제하였다.)
 + 역기서 Ruby로 작성된 오픈소스 템플릿 언어인 [Liquid](http://sungkukpark.github.io/translation/2016/03/20/liquid-tutorial-01-introduction.html)에 대해 대략 알고 넘어가면 좋다. Liquid객체인 [paginator](https://jekyllrb-ko.github.io/docs/pagination/)의 속성도 확인해보자.
 ![Alt text](/images/20180103/01.jpg)

 + /_include/header.html의 적당한 곳에 아래의 코드를 넣어두자.
 ``` html
    <ul style="list-style-type:none;margin:0">
      <li><a href="/01.lion/">lion</a></li>
      <li style="margin-bottom: 30px;"><a href="/02.tiger/">tiger</a></li>
    </ul>
 ```

+ 결과 화면 
![Alt text](/images/20180103/02.jpg)

+ 이제 메인 포스팅 화면에(/index.html) 페이징 기능을 넣어보도록 하자. 살펴보니 Jekyll-Uno 테마에는 기본적으로 메인 포스팅에 페이징 기능이 있다. `_includes/pagination.html`을 index.html에서 include하고 있다. 
_config.yml에서 __paginate: [숫자]__ 만 변경하고 개발서버를 리스타트 하면 될것 같다.


