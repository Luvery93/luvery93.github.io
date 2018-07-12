---
layout: post
title: "Google Analytics - 구글 웹로그 분석"
date: 2017-12-04 16:22 +0900
categories: [Blog]
comments: true
---

* [Google Analytics - 구글 웹로그 분석](https://www.google.co.kr/intl/ko/analytics/)에 접속하여 구글 계정으로 로그인합니다.

  ![1]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/1.png)

* Analytics에 처음 접속한 계정은 대시보드 화면이 아닌 Analytics 처음 가입할 떄 속성 추가 화면과 이 후의 웹사이트 들의 속성 추가 화면이 같으므로 가입하기를 선택합니다. 이미 속성이 있는 경우 좌측 하단 설정탭(톱니바퀴) 속성 추가를 선택합니다.

  ![2]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/2.png)

* 속성 추가 페이지에서 추가할 속성에 해당하는 웹사이트 이름과 URL을 정확하게 작성합니다. 이 과정을 거치면 추척 ID가 생성됩니다.

  ![3]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/3.png)

  ![4]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/4.png)

* 설치형 블로그 및 유투브 같은 개인 채널에 Google Analytics를 연동하도록 하겠습니다. 우선은 유투브 설정입니다.

  * 자신의 유투브 채널 대시보드 - 채널 - 고급을 선택합니다.

    ![5]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/5.png)

  * 목록하단에 Google 애널리틱스 속성 추적 ID에 추척 ID를 적은 뒤 저장합니다.

    ![6]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/6.png)

* 설치형 블로그에는 추적 코드를 삽입해야 합니다.

  *  추적코드는 좌측 하단 설정탭(톱니바퀴)에서 추적 정보 - 추적 코드를 선택합니다.

    ![7]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/7.png)

  * 해당 페이지에서 추적 ID 및 범용 사이트 태그(gtag.js)를 확인하실 수 있습니다. 이 범용 사이트 태그를 설치형 블로그에 추가합니다.

    ![8]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/8.png)

  * 다만 현재 사용하고 있는 Jekyll 테마에서는 범용 사이트 태그가 이미 추가되어 있어 추적 ID만 설정하면 됩니다.

    ![9]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/9.png)

    ![10]({{ site.url }}/img/2017-12-04-google-analytics-setting-youtube-and-jekyll/10.png)