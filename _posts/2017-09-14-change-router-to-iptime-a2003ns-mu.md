---
layout: post
title: "기가 인터넷 변경 이후 공유기 설정 - ipTIME A2003NS-MU"
categories: [Windows]
date: 2017-09-14 14:45 +09:00
comments: true
---

* 기가 인터넷 컴팩트(KT) 회선으로 변경으로 인해 공유기도 기가 인터넷을 지원하는 ipTIME A2003NS-MU 로 변경하여 기록을 남깁니다.

  1. 공유기 LAN 포트로 물려있는 데스크탑 (혹은 스마트폰)에서 192.168.0.1 로 접속하여 공유기 관리자 페이지에 접속 후 로그인 합니다.

  2. 메뉴 탐색기 - 시스템 관리 - 관리자 설정에서 관리자 계정과 암호를 설정합니다.

     ![1]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/1.png)

  3. 기가 인터넷을 지원하도록 무선 네트워크 중 하나는 11ac/11n 모드로 설정합니다.

     ![2]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/2.png)

  4. 인터넷 전화기를 사용하지 않는다면 상관없지만, 인터넷 전화기가 지원하는 무선 네트워크 모드(G and N)를 설정해야 한다면 나머지 무선 네트워크 모드를 G and N으로 설정합니다.

     ![3]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/3.png)

  5. 메뉴 탐색기 - NAT/라우터 관리 - 포트포워드 설정에서 원격데스크톱 포트 및 기타 필요한 포트를 설정합니다. 주 사용 컴퓨터의 내부 아이피가 192.168.0.2 이므로 아래와 같은 설정이 예시가 될 수 있습니다.

     ![4]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/4.png)

  6. DDNS설정을 통해 공유기 관리 페이지 접속 및 원격데스크톱을 도메인 이름으로 사용할 수 있도록 설정합니다.

     ![5]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/5.png)

  7. WOL 기능을 지원하는 데스크톱을 MAC주소 등록을 통해 곧바로 이용할 수 있습니다.

     ![6]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/6.png)

  8. 원격 관리 포트를 입력하지 않는다면 공유기 외부 접속이 제한되게 됩니다.

     ![7]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/7.png)

* 다음은 안드로이드 어플을 통해 WOL 신호를 보내 데스크톱에 원격접속하는 과정입니다.

  1. 안드로이드 어플 중 ipTIME WOL을 이용하면 WOL 신호를 스마트폰을 통해 곧바로 보낼 수 있습니다.

     ![8]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/8.png)

  2. 외부 공유기 추가에서 DDNS 주소, 원격 접속 포트 및 관리자 계정 정보를 입력하여 공유기 정보를 추가합니다.

     ![9]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/9.png)

  3. 공유기에 접근하면 아래와 같이 등록된 PC에 WOL 신호를 보낼 수 있습니다.

     ![10]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/10.png)

  4. 안드로이드 어플 중 microsoft remote desktop을 이용하면 윈도우 원격데스크톱을 쉽게 이용할 수 있습니다.

     ![11]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/11.png)

  5. Remote Desktop에서 + 버튼을 눌러 Desktop를 추가합니다.

     ![12]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/12.png)

  6. DDNS로 설정한 도메인과 윈도우즈 로그인 계정을 각각 입력하여 저장합니다.

     ![13]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/13.png)

  7. 설정된 값으로 원격 데스크톱을 접속할 수 있습니다.

     ![14]({{ site.url }}/img/2017-09-14-change-router-to-iptime-a2003ns-mu/14.png)