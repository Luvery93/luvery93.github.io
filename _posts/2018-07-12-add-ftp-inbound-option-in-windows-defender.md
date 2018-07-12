---
layout: post
title: IIS FTP 익명 접속 권한이 있지만 접속 불가한 경우
categories: [Windows]
date: 2018-07-12 16:42 +0900
comments: true
---

* IIS FTP 익명 접속 설정을 마친 뒤 외부 접속을 테스트 해보니 접근할 수 없는 경우일 떄는 방화벽을 확인해봅니다.

* Windows Defender 고급 보안 옵션에서 인바운드 규칙을 추가합니다.

  ![1]({{ site.url }}/img/2018-07-12-add-ftp-inbound-option-in-windows-defender/1.png)

* FTP 규칙은 미리 정의 되어 있으므로 FTP 서버 규칙을 선택합니다.

  ![2]({{ site.url }}/img/2018-07-12-add-ftp-inbound-option-in-windows-defender/2.png)

* 연결 허용 옵션을 선택합니다.

  ![4]({{ site.url }}/img/2018-07-12-add-ftp-inbound-option-in-windows-defender/4.png)

* 인바운드 규칙을 설정한 뒤 FTP 서비스를 재실행 합니다.

  ![5]({{ site.url }}/img/2018-07-12-add-ftp-inbound-option-in-windows-defender/5.png)