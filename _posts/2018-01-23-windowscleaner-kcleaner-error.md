---
layout: post
title: "윈도우클리너 실행 오류 해결"
date: 2018-01-23 09:58 +0900
categories: [Windows]
comments: true
---

윈도우클리너(구 KCleaner) 사용 중 연관되는 윈도우 서비스가 닫혀 있어 "서비스를 사용할 수 없거나 서비스와 연관되어 사용 가능한 장치가 없기 때문에 시작할 수 없습니다." 라는 오류 메시지가 나오면 작동이 안될 경우가 있습니다.

​	![1]({{ site.url }}/img/2018-01-23-windowscleaner-kcleaner-error/1.png) 

이럴 경우에 실행창에 service.msc를 실행 한 뒤 "Windows Management Instrumentataion" 서비스가 중지되었는지 확인하고 실행시킵니다.

​	![2]({{ site.url }}/img/2018-01-23-windowscleaner-kcleaner-error/2.png) 

​	![3]({{ site.url }}/img/2018-01-23-windowscleaner-kcleaner-error/3.png)