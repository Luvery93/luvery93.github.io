---
layout: post
title: "원격데스크톱 포트 변경"
date: 2017-10-25 16:41:00 +0900
categories: [Windows]
comments: true
---

* 한 공유기 내에서 포트포워딩을 통해 여러대의 PC에 외부 원격접속을 진행하기 위해서는 포트 변경이 필수입니다.

1. 포트를 변경하고자 하는 PC의 레지스트리 편집기에서 아래 경로의 PortNumber 값을 변경합니다.

   ```
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\Wds\rdpwd\Tds\tcp
   ```

   ![1]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/1.png)

   ```
   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp
   ```

   ![2]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/2.png)

2. 변경하는 과정은 PortNumber 오른쪽 클릭 - 값 편집창을 띄운 뒤, 10진수로 선택 후 원하는 포트로 변경합니다.

   ![3]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/3.png)

   ![4]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/4.png)

3. Windwos 방화벽 고급설정에서 설정한 새로운 포트번호의 인바운드를 추가합니다.

   ![5]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/5.png)

   ![6]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/6.png)

   ![7]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/7.png)

   ![8]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/8.png)

   ![9]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/9.png)

   ![10]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/10.png)

   ![11]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/11.png)

   ![12]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/12.png)

4. 이후 원격데스크톱 서비스를 다시 시작 한 뒤, 포트포워딩 설정을 하면 새로운 포트로 원격 접속이 가능합니다.

   ![13]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/13.png)

   ![14]({{ site.url }}/img/2017-10-25-mstsc-change-portnumber/14.png)