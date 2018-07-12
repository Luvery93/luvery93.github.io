---
layout: post
title: git push 도중 AggregateException 오류가 발생했을 경우
categories: [Blog]
date: 2018-07-12 15:54 +0900
comments: true
---

* github의 암호를 갱신한 이후 로컬 저장소에 저장되있는 github 계정과 일치하지 않을 떄 발생했던 오류입니다.

  ![1]({{ site.url }}/img/2018-07-12-git-aggregate-exception-error/1.png)

* CMD 창에서 **rundll32 keymgr.dll KRShowKeyMgr**을 입력하면 자격증명 정보를 편집할 수 있습니다.

  ![2]({{ site.url }}/img/2018-07-12-git-aggregate-exception-error/2.png)

* 변경된 계정 정보를 입력하여 자격증명을 수정합니다.

  ![3]({{ site.url }}/img/2018-07-12-git-aggregate-exception-error/3.png)