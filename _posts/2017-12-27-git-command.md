---
title:  "git 명령어 모음"
date:   2017-12-27 09:04:23
categories: [etc]
tags: [git]
comments: true
---

지금까지는 `sourcetree`를 이용하여 `github`를 이용하였는데 command로 하는 습관일 들이고자 정리해본다.


+ 새로운 저장소 만들기
``` ruby
git init
```

+ 저장소 받아오기
``` ruby
git clone [복제할 자장소 경로]
ex) git clone https://github.com/lohanyeon/lohanyeon.github.io.git
```

+ 추가와 확정(commit) - 저장소의 디렉토리에서 실행한다.
``` ruby
git add .
또는
git add *
또는
git add [filename]
git commit -m "커밋에 대한 설명"
```

+ push하기
``` ruby
git push -u origin master
```
- 원격 저장소 연결하기 (clone하지 않고 로컬 소스를 push하고자 할때)
``` ruby
git remote add origin [원격서버주소]
```

+ 가지치기
``` ruby
git checkout -b another
```

+ master로 돌가가기
``` ruby
git checkout master
```

+ 가지 삭제
``` ruby
git branch -d another
```

+ 가지 푸쉬
``` ruby
git push origin another
```

+ 갱신
``` ruby
git pull
```

+ 병합
``` ruby
git merge another
```

+ 비교
``` ruby
git diff [원래 가지] [비교할 가지]
```

이 포스트는 *http://rogerdudler.github.io/git-guide/index.ko.html*를 참조 하였습니다.
