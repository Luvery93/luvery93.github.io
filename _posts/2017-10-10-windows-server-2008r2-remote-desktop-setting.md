---
layout: post
title: "Windwos Server 2008R2 - 원격데스크톱 역할 추가"
date:	2017-10-10 16:37:00 +0900
categories: [Windows]
comments: true
---

1. Windows Server 2008 이상부터 서버에 원격데스크톱 기능을 사용하기 위해서 서버 역할의 **원격 데스크톱 서비스**를 설치합니다.

   ![1]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/1.png)

2. 원격 데스크톱 서비스 소개를 지나 설치할 역할 서비스를 선택합니다.

   ![2]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/2.png)

   ![3]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/3.png)

   ![4]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/4.png)

   ![5]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/5.png)

   ![6]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/6.png)

   ![7]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/7.png)

   ![8]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/8.png)

   ![9]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/9.png)

3. 선택된 역할 서비스를 확인하고 설치를 진행합니다.

   ![10]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/10.png)

   ![11]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/11.png)

   ![12]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/12.png)

4. 재부팅 이후 설치 완료 메시지를 확인합니다.

   ![13]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/13.png)

5. 서버 - 역할 - 원격 데스크톱 서비스 에서 세션 호스트 구성 설정을 진행합니다.

   ![14]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/14.png)

6. 위 설정 편집을 더블 클릭하여 한 계정에 다중 세션을 설정합니다.

   ![15]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/15.png)

7. 라이선스 서버를 설정합니다.

   ![16]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/16.png)

   ![17]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/17.png)

   ![18]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/18.png)

8. 설정이 완료되었는지 확인합니다.

   ![19]({{ site.url }}/img/2017-10-10-windows-server-2008r2-remote-desktop-setting/19.png)