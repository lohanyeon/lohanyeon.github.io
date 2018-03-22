---
title:  "Django Apache 연동"
date:   2018-03-20 01:04:23
categories: [python]
tags: [python, django, apache, httpd, mod_wsgi.so]
comments: true
published: true
---

AWS(Amazone Web Service)를 사용해보기 위해 지난해 python django와 vue.js로 만든 회사 홈페이지를 AWS로 포팅하기로 했다. 역시 오래간만에 하니깐 모든 과정이 가물가물하다. 그래서 정리를 해보았다. 
`관리툴은 Django를 이용하였고 프론트는 Vue.js를 이용하여 개발하였다.`

#### __AWS 인스턴스 신청 및 LAMP 셋팅__
+ 인스턴스는 Amazon Linux AMI로 선택하였다. 
+ Red Hat기반으로 Amazon에서 배포한다고 한다.
+ 아래 url을 열어보면 자습서가 나온다. 아주 쉽게 LAMP셋팅에 대해 나와있다.
+ https://docs.aws.amazon.com/ko_kr/AWSEC2/latest/UserGuide/install-LAMP.html

#### Python, Django 설치
+ python 설치 (python은 기본적으로 2.7버전이 설치되어 있다.)

+ pip 설치
```
$ yum install python-pip
```

+ Django 설치 및 버전 확인
```
$ pip install django==1.9.6
$ python -m django --version
```

+ mod_wsgi 설치
```
# os와 python버전에 맞는 wsgi를 찾아 install한다.
$ yum search wsgi
$ yum install mod24_wsgi-python27.x86_64
```

+ cors, mysql등 장고 어플리케이션에서 사용한 모듈을 설치한다.
```
# os와 python버전에 맞는 모듈을 찾아 install한다.
$ yum search MySQLdb
$ yum install MySQL-python27.x86_64 
$ yum install django-cors-headers
```

+ Django소스를 관리툴용 [PROJECT_PATH] 위치에 카피한 후 apache설정을 추가한다. (관리툴)

```
$ vi /etc/httpd/conf.d/vhost-homepage-admin.conf

<VirtualHost *:80>
        WSGIScriptAlias / [PROJECT_PATH]/[APP_PATH]/wsgi.py

        DocumentRoot [PROJECT_PATH]
        ServerName [ADMIN_DOMAIN]

        <Directory [PROJECT_PATH]/[APP_PATH]>
                <Files wsgi.py>
                        Order deny,allow
                        Allow from all
                </Files>
        </Directory>

        <Directory [PROJECT_PATH]>
                Options FollowSymLinks
                AllowOverride FileInfo
                Order allow,deny
                Allow from all
        </Directory>

        Alias /assets/ [PROJECT_PATH]/staticfiles/
        <Directory [PROJECT_PATH]/staticfiles>
                Allow from all
        </Directory>

        Alias /media/ [PROJECT_PATH]/media/
        <Directory [PROJECT_PATH]/media>
                Allow from all
        </Directory>

</VirtualHost>
```

+ Vue.js소스를 프론트용 [PROJECT_PATH] 위치에 카피한 후 apache설정을 추가한다. (프론트)

```
$ vi /etc/httpd/conf.d/vhost-homepage-front.conf

<VirtualHost *:80>
        DocumentRoot [PROJECT_PATH]
        ServerName [FRONT_DOMAIN]

        ProxyRequests On
        ProxyPass [PATH] [DOMAIN/PATH]

        <Directory "[PROJECT_PATH]">
                RewriteEngine On
                RewriteBase /
                RewriteRule ^index\.html$ - [L]
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteRule . /index.html [L]
        </Directory>

        <Directory "[PROJECT_PATH]">
                Options FollowSymLinks
                AllowOverride FileInfo
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>
```

+ apache restart
```
$ service httpd restart
```

+ 만약 Django에서 wsgi를 로드 못하였다는 에러가 발생한다면 아래와 같이 소스를 추가해보자

```
$ vi [PROJECT_PATH]/[APP_PATH]/wsgi.py
import os, sys

path = os.path.abspath(__file__+'/../..')   

if path not in sys.path:

    sys.path.append(path)                                       
```

이제 잘 돌아가는가? 잘 안된다면 아파치의 error_log를 확인하면서 하나하나 해결해보도록 한다. ㅠ