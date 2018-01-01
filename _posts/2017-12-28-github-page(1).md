---
title:  "github page로 블로그 만들기"
date:   2017-12-27 09:04:23
categories: [etc]
tags: [github]
comments: true
---

지난주 회사 직원들과 스크린골프를 쳤다.
나 신기록 새움 ㅋㅋㅋ
무려 +3인 `75타` 음하하하!
스크린 끝나고 도란도란 술 ㅊ마시다가 우리 내년부턴 그만놀고 무언가 `생산적인 일`을 해보자란
이야기가 나왔다.

`그래 뭔가 만들어보자!`

기술적인 내용을 공유할 방법을 찾다보니 이왕이면 정성들여 각자 브랜딩할 수도 있는 블로그를 만들어서
공유하기로 맘 먹었다.(일단 나만)

티스토리, 워드프레스 등 이것저것 찾아보다 `github에서 page를 제공`해준다는 내용을 예전에 얼핏 봤던 기억이 났다.
그래 이왕이면 github ok!!! 버전 관리 시스템인 git도 적응할겸 github page로 go!

+ 먼저 github.com에 접속하여 회원가입한다.
+ 회원 가입 후 아래 이미지 처럼 Repository를 클릭.
![Alt text](/images/20171227/02.jpg)

+ Repository name에 [본인계정아이디].github.io를 입력한다.
+ Description도 입력 후 Create repository 버튼을 클릭한다.
+ 만약 Repository name에 [본인계정아이디]외 다른 단어를 입력하게 되면 Context name으로 인식한다고 한다. ex) engel.github.io를 입력하였다면 yeonkh94.github.io/engel로 인식
![Alt text](/images/20171227/03.jpg)

+ https 주소를 카피한 후 터미널에서 2번째 박스의 내용을 차례대로 입력해본다.
![Alt text](/images/20171227/04.jpg)

+ index.html파일을 추가해보기로 하자. 터미널을 열고 아래와 같이 차례대로 입력해 본다.
```ruby
# echo "Welcome to yeonkh94.github.io" >> index.html
# git add .
# git commit -m "add index.html"
# git push -u origin master
```

+ 아래와 같이 index.html파일이 Repository에 추가된것을 확인할 수 있다.
![Alt text](/images/20171227/05.jpg)

+ 브라우져에 yeonkh94.github.io를 입력하면 index.html 내용을 확인할 수 있을 것이다.
![Alt text](/images/20171227/06.jpg)

+ 만약 하나의 피씨에서 여러 계정으로 git을 사용할 경우 퍼미션 에러가 나게 된다. 이 경우에는 http://recoveryman.tistory.com/283 이 블로그를 참조하길 바란다. 나는 이게 너무 복잡해서;; 그냥 Settings > Collaborators에 협업하고자 하는 아이디를 입력하여 이메일 인증하여 사용하였다.

다음에는 jekyll(지킬)을 이용하여 블로그를 꾸며보기로 하자.
