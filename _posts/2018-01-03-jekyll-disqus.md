---
title:  "jekyll 블로그 disqus 댓글달기"
date:   2018-01-03 05:00:01
categories: [etc]
tags: [github, jekyll, disqus]
comments: true
published: ture
---

jekyll은 기본적으로 댓글을 지원하지 않는다. 댓글을 사용하기 위해서 __disqus의 API를 이용__ 하여 댓글을 직접 구현하지 않고 간단히 추가하는 방법에 대해 알아보자.  
  
방법은 간단한다.   
[https://disqus.com](https://disqus.com)에 회원가입하고 가입 아이디를 _config.yml에 넣어주면 끝이다 (현재 쓰고 있는 jekyll-Uno테마에는 기본적으로 disqus셋팅이 되어 있고 주석처리 되어있다.)

+ 회원가입 후 메인화면에서 GET STARTED를 클릭.
![이미지1](/images/2018010301/01.jpg)

+ I want to install Disqus on my site 클릭
![이미지1](/images/2018010301/02.jpg)

+ 하단의 Universal Code 버튼 클릭
![이미지1](/images/2018010301/03.jpg)

+ 노란 1번의 소스는 jekyll Uno테마의 경우 _includes/disqus.html에 이미 있다. 만약 없다면 소스를 그래도 카피하여 파일을 만들자.
![이미지1](/images/2018010301/04.jpg)

+ Website URL에 github page의 url을 정확히 입력하고 기타 항목들은 알아서 입력 후 Complete Setup버튼 클릭
![이미지1](/images/2018010301/05.jpg)

+ Disqus 댓글 사용을 위한 설정이 완료 되었다.
![이미지1](/images/2018010301/06.jpg)

+ _config.yml을 열어 아래 항목을 찾아  your-disqus-name에 위에서 가입한 disqus아이디를 입력
```
# disqus_shortname: 'your-disqus-name'
disqus_shortname: 'yeonkh94'
```

+ 마지막으로 /_posts에 포스팅할 md파일을 만들고 상단에 다음과 같이 comments: true로 설정하고 편집 저장하자.
``` 
title:  "jekyll 블로그 disqus 댓글달기"
date:   2018-01-03 05:00:01
categories: [etc]
tags: [github, jekyll, disqus]
comments: true
published: ture
```

+ 아래와 같이 댓글 입력란이 나오면 성공 (가입 후 처음 댓글 등록을 하면 이메일 인증을 받아야 한다.)
![이미지](/images/2018010301/07.jpg)