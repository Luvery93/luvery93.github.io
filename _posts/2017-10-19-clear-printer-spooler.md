---
layout: post
title: "프린터 스풀러 삭제"
categories: [Windows]
date: 2017-10-19 14:40:00 +0900
comments: true
---

* 윈도우 서비스 중 Printer Spooler가 삭제되지 않을 때 아래 명령어를 통해 삭제할 수 있습니다.​

  ```
  net stop splooer
  attrib -r -h -s C:\Windows\System32\spool\PRINTERS
  echo y|del /s C:\Windows\System32\spool\PRINTERS\*.*
  net start spooler
  pause
  ```

