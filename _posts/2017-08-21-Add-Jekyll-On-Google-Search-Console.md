---
layout: post
title: "Google Search Console에 Jekyll 블로그 등록"
date: 2017-08-21 17:30 +09:00
categories: [Jekyll]
comments: true
---

1. [Google Search Console](https://www.google.com/webmasters/tools/home?hl=ko)에 블로그 등록

   * Google Search Console에 Jekyll 블로그 URL을 등록합니다.

     ![1]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/1.png)

2. Google Search에 등록하는 웹사이트의 소유권을 확인합니다.

   * Google Search에서 제공하는 **html 파일을 다운로드** 한 뒤, 웹사이트에 업로드 합니다.

     ![2]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/2.png)

   * Jekyll 프로젝트 루트 폴더에 추가합니다.

     ![3]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/3.png)

   * **_config.xml** 파일의 url에 웹사이트 도메인을 추가합니다.

     ![4]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/4.png)

   * 정상적으로 업로드 되었는지 확인합니다.

     ![5]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/5.png)

   * 웹사이트 소유권을 인증합니다.

     ![6]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/6.png)

3. Sitemap을 작성하여 포스트가 검색에 포함되도록 설정합니다.

   * 아래와 같이 [sitemap.xml]({{ site.url }}/downlaod/2017-08-21-Add-Jekyll-On-Google-Search-Console/sitemap.xml) 을 작성합니다.

     ![7]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/7.png)

   * sitemap.xml을 Jekyll 프로젝트의 루트 폴더에 추가합니다.

     ![8]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/8.png)

   * sitemap.xml이 정상 작동하는 지 확인합니다.

     ![9]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/9.png)

   * [Google Search Home](https://www.google.com/webmasters/tools/home?hl=ko)에서 추가한 사이트를 선택합니다.

     ![10]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/10.png)

   * Sitemaps 관리 페이지로 진입합니다.

     ![11]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/11.png)

   * SITEMAP 추가/테스트를 눌러 테스트를 진행합니다.

     ![12]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/12.png)

     ![13]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/13.png)

     ![14]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/14.png)

     ![15]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/15.png)

   * 위와 같이 테스트의 결과에 이상이 없다면 sitemap.xml을 추가합니다.

     ![12]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/12.png)

     ![16]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/16.png)

     ![17]({{ site.url }}/img/2017-08-21-Add-Jekyll-On-Google-Search-Console/17.png)