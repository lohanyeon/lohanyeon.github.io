---
title:  "ECMAScript에 대하여"
date:   2018-01-04 05:00:01
categories: [javascript]
tags: [javascript, js, ecmascript]
comments: true
published: ture
---

![자바스크립트](/images/common/javascript-myths-and-its-evolution-12-638.jpg)

아직도 혼돈의 세상인 `자바스크립트` 에 대한 표준 및 새로운 버전들이 나오면서 그 버전들에 대해 정리해보고자 한다.  

+ __ECMAScript란?__   
    1. 풀네임은 European Computer Manufacturers Association Script이다.
    2. ECMAScript를 줄여서 보통 __ES__ 라고 부름
    3. 보통 javascript라고 하면 ES5까지를 이야기 한다. (ES3, ES5)
    4. 초창기 브라우져가 난립하던 시절 넷스케이프는 javascript, ie는 jScript를 브라우져에   탑재하였는데 시간이 갈수록 서로간의 기술적 갭이 커져서 ECMA라는 협회에서 표준안을 제시하였다.

+ __버전별 특징__ 
    1. ES1
        * 1997년 발표
        * 첫번째 버전이다.
    2. ES2
        * 1998년 발표
    3. ES3 
        * 1999년 발표
        * 정규식 추가, 향상된 문자열 처리, 새로운 제어문, try/catch예외처리, 오류 정의 강화, 숫자 출력 형식 지정 및 기타 향상된 기능
    4. ES4 
        * 한것도 없이 팽당함-_-
    5. ES5
        * 2009년 발표
        * strict mode제공 (오류가 발생하기 쉬운 구조를 피하기 위해서)
        * getter및 setter, JSON(Javascript Object Notation)에 대한 라이브러리 지원 및 객체 속성에 대한 보다 완벽한 반영과 같은 몇 가지 새로운 기능을 추가
    6. ES5.1
        * 2011년 발표
    7. ES6
        * 2015년 발표
        * ES2015라고도 부름
        * 클래스 및 모듈을 비롯한 복잡한 응용 프로그램을 작성하는 데 중요한 새로운 구문을 추가
        * 반복자 및 for / of루프, Python 스타일 생성기 및 생성자 표현식, 화살표 함수등 추가
        * 최초의 'ECMAScript Harmony' 사양으로 ES6하모니 라고도 한다.
    8. ES7
        * 2016년 발표
        * ES2016라고도 부름
        * ES2015에서 언어 개혁, 코드 분리, 효과 제어 및 라이브러리/도구 사용을 계속하기 위한 (**)밑 Array.prototypes.includes를 포함(아직 뭔 얘긴지 모르겠다;;)
    9. ES8
        * 2017년 발표 
        * 메타 프로그래밍, 클래스 및 인스턴스 속성, 연산자 오버로딩, 레코드, 튜플, traits등 추가(이것 또한 잘 모르겠음;;)

+ __보통 우리가 말하는 javascript라 함은 ES3, ES5를 이야기 한다고 보면 될것 같다.__