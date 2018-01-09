---
title:  "Python 가상환경 virtualenv"
date:   2018-01-08 04:04:23
categories: [python]
tags: [python, virtualenv]
comments: true
published: true
---

파이썬을 사용하다보면 pip등을 사용하여 많은 패키지를 손쉽게 사용할 수가 있다. 하지만 손쉽게 사용할 수 있는 만큼 패키지간 또는 파이썬과 패키지간의 의존성에 대해 고민할 수 밖에 없는 순간이 온다. 내 피씨에 프로젝트 하나만 달랑 돌아간다면야 시스템에 global하게 설치해서 사용해도 되겠지만 파이썬 버전이 틀린 여러 프로젝트를 돌린다면 문제가 심각해질 수 있다. 이런 경우를 위해 `디렉토리마다 가상으로 격리된(isolated) 개발환경`을 구축하여 실행 할 수 있도록 한것이 `virtualenv`이다.        

> 모든 내용은 OSX Sierra를 기준으로 기술 되었습니다.
  
#### __python, pip 설치__

+ OSX에는 기본적으로 python2.7이 설치되어 있다. 버전을 확인해보자.
```
$ python -V
$ which python
```

+ OSX의 패키지 매니저격인 Homebrew가 설치해보자. (아래 코드를 그래도 복불하자.)
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

+ Homebrew를 이용하여 python3를 설치하고 버전과 설치 위치를 알아보자.
```
$ brew install python3
$ python3 -V
$ which python3
```

+ 이제 python2.7, python3.5와 pip, pip3를 모두 설치하였다.
![pythoninstall](/images/20180108/01.jpg)

+ 만약 pip또는 pip3가 없다면 easy_install로 설치하자  
```
$ python easy_install pip
$ python3 easy_install pip3
```

+ 이제 virtualenv와 virtualenvwrapper 설치한다.  
```
$ pip install --user virtualenv virtualenvwrapper
# python2인 경우
$ pip3 install --user virtualenv virtualenvwrapper
# python3인 경우
# 만약 permission error가 발생한다면 sudo로 실행하자
```

#### __virtualenv로 가상환경을 만들기, 사용__
+ virtualenv 명령으로 가상 환경을 만들자
``` 
# 사용방법 : virtualenv --python=파이썬버전 가상환경이름
$ virtualenv --python=python2.7 hello_python2.7
# python2.7인 경우
$ virtualenv --python=python3.6 hello_python3.6
# python3.6인 경우
```

+ 위에서 생성한 가상환경에 진입해 보자.
```
$ source hello_python2.7/bin/activate
# python2.7환경의 hello_python2.7 가상환경 진입
$ deactivate
# python2.7환경의 가상환경 빠져 나오기
# source hello_python3.6/bin/activate
# python3.6환경의  hello_python3.6 가상환경 진입
$ deactivate
# python3.6환경의 가상환경 빠져 나오기
```

#### __virtualenvwrapper 사용하기__
+ 가상환경을 특정 디렉토리에서 사용할 수 있게 랩핑해주는 명령이다.
```
$ cd ~ #홈디렉토리로 이동
$ mkdir ~/.virtualenvs
```

+ vi편집기로 ~/.bash_profile에 아래 코드를 복불하자.
```
# python virtualenv settings
export WORKON_HOME=~/.virtualenvs
export VIRTUALENVWRAPPER_PYTHON=`$(command \which python3)`  # Usage of python3
source /usr/local/bin/virtualenvwrapper.sh
```

+ 만약 /usr/local/bin/virtualenvwrapper.sh를 찾을 수 없다면 find명령으로 찾아 위치를 변경하자.
```
$ find . -name virtualenvwrapper.sh
```

+ source 명령을 이용해 적용 또는 터미널 재시작
```
$ source ~/.bash_profile
# 만약 permission error가 발생한다면 해당 위치에 owner를 사용자로 변경하자.
$ chown -R [사용자계정이름] [디렉토리 위치]
```

+ 가상환경 만들기
```
$ mkvirtualenv [가상환경이름]
```

+ 가상환경 삭제
```
$ rmvirtualenv [가상환경이름]
```

+ 가상환경 리스트
```
$ workon
```

+ 가상환경 진입
```
$ workon [가상환경 이름]
```

+ 가상환경 빠져나오기
```
$ deactivate
```