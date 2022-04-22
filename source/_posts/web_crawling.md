---
title: "웹 크롤링"
author: "HS"
date: '2022-04-22'
categories: 'Python'
---
## 웹 크롤링 입문

VS 코드로 진행
<!-- more-->
- 파이참으로 가상환경 만들기

[https://beelinekim.tistory.com/64](https://beelinekim.tistory.com/64)

- beautifulsoup4 설치

[https://www.crummy.com/software/BeautifulSoup/bs4/doc/#installing-beautiful-soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#installing-beautiful-soup)

- 라이브러리 설치 (다 쓸지 안 쓸지 모르지만)

pip install beautifulsoup4

pip install numpy

pip install matplotlib

pip install pandas

pip install seaborn

pip install requests

## 크몽 : 나무위키

- 대한민국 1위 **[프리랜서](https://namu.wiki/w/%ED%94%84%EB%A6%AC%EB%9E%9C%EC%84%9C)/아웃소싱 플랫폼**
. ‘전문성'이라는 무형의 서비스를 제품화하는 비즈니스 모델로, 디자인, IT, 콘텐츠 제작, 마케팅 등 300개 이상의 카테고리를 보유하고 있다. 즉 [투잡](https://namu.wiki/w/%ED%88%AC%EC%9E%A1)
(부업)을 구할수 있는 사이트다.
- 크롤링 아웃소싱 홈페이지

[https://namu.wiki/w/크몽](https://namu.wiki/w/%ED%81%AC%EB%AA%BD)

## 웹 크롤링

![Untitled](images/web_crawling/Untitled.png)

웹 상의 정보를 쏙 빼오는 것!

필요한 것은 

1. 링크

## 이미지, PDF 도 주소만 알면 다운 받을 수 있다.

- 한마디로 인터넷상으로 접근이 가능하면 정보를 가져올 수 있다.

## 실제 실무에서는...(파이썬 기준)

- 도구가 필요 하다.
- BeautifulSoup : 가장 일반적인 수집 도구(CSS 통해서 수집)
- Scrapy (CSS, XPATH)
- Selenium (CSS, XPATH + JavaScript)

## 웹사이트에 있는 정보를 가져오는 것이기 때문에

- HTML
- CSS
- JavaScript
- (Ajax)
- 등을 알아야 한다.

## 간단한 웹사이트 말들기

- Index.html

![Untitled](images/web_crawling/Untitled_1.png)

- html문서를 만들거야
- 언어는 영어아
    
    ![Untitled](images/web_crawling/Untitled_2.png)
    
- <head>는 컨트롤하는영역
    - css, JavaScript는 다 <head>에 있다.
    
    ![Untitled](images/web_crawling/Untitled_3.png)
    
- 간단하게 html 문서를 작성했다.

![Untitled](images/web_crawling/Untitled_4.png)

## 본격적으로 웹크롤링 실습

- 파이썬 파일에서
- Beautifulsoup(x) → BeautifulSoup(o)

![Untitled](images/web_crawling/Untitled_5.png)

- 클래스로 변환 됐다.

![Untitled](images/web_crawling/Untitled_6.png)

- find 메서드로 웹 크롤링 할 부분을 지정

![Untitled](images/web_crawling/Untitled_7.png)

- 결과

![Untitled](images/web_crawling/Untitled_8.png)

- 텍스트만 가져오는 메서드 : get_text()

![Untitled](images/web_crawling/Untitled_9.png)

- 결과

![Untitled](images/web_crawling/Untitled_10.png)

- 더 많은 메서드는 BeautifulSoup 공식문서를 보고 공부하면 된다.

[https://www.crummy.com/software/BeautifulSoup/bs4/doc/#installing-beautiful-soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#installing-beautiful-soup)