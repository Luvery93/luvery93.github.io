---
layout: post
title: "Restream.io를 통한 다중 송출 설정"
date: 2017-08-11 17:01 +09:00
categories: [BroadCast]
comments: true
---

1. NGINX

   * OBS를 통해 RTMP 서버 역할을 충분히 진행 할 수 있으나, 트위치/유튜브 동시 송출에 버퍼링이 심한 문제가 있습니다.
   * 개인 설정 문제가 있을 수 있으나, 방송 준비 시 NGINX 프로세스를 따로 실행해야 하는 점과 프로세스 실행 자체에 오류가 날경우 확인해야 되는 단점이 존재합니다.
   * 따라서 트위치/유튜브 동시 송출이 가능한 RTMP 서비스를 제공하는 Restream.io로 변경합니다.

2. [Restream.io](https://restream.io/)

   * 별도의 설정이 필요 없이 회원 가입을 통해 30 개 이상의 플랫폼에 동시 송출이 가능합니다.

   * RTMP URL에 Seoul, South Korea가 개설 되면서 방송 딜레이가 줄었습니다.

     ![1]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/1.png)

   * 대시보드에서 스트리밍하고자 하는 채널을 선택한 뒤, rtmp 스트림 키를 입력할 필요도 없이 해당 플랫폼 계정으로 쉽게 연동할 수 있습니다.

     ![2]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/2.png)

   * 다중 플랫폼 방송 송출시 방송 제목을 따로 설정해야 했던 NGINX 때와 달리 트위치/유튜브의 경우 Restream 관리 페이지에서 쉽게 변경이 가능합니다.

     ![3]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/3.png)

   * SNS (트위터/페이스북) 연동을 통해 방송 중 임을 알릴 수 도 있습니다.

     ![4]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/4.png)

   * 스트리밍 이후 스트리밍 중의 비트레이트 전송률 및 프레임 로그를 확인 할 수 있습니다.

     ![5]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/5.png)

     ![6]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/6.png)

   * 물론 플랫폼 별 확인도 가능합니다.

     ![7]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/7.png)

   * 마지막으로 웹 형식의 통합 채팅창을 지원합니다. 하지만 카카오TV의 경우 정식 지원하지 않고 있으므로 afreehp를 계속 이용하도록 합니다.

     ![8]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/8.png)

3. 설정

   * OBS Studio 설정입니다. 방송 시작 후 미리보기는 종료하는 것이 점유율 하락에 좋다고 합니다.

     1. 방송 형식

        * URL 은 Restream RTMP Server URL, 스트림 키는 Restream RTMP Server Stream Key 를 입력하세요.

        ![9]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/9.png)

     2. 출력 - 방송

        ​	![10]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/10.png)

     3. 출력 - 녹화

        ​	![11]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/11.png)

     4. 오디오 - [VoiceMeeter Banana](https://luvery93.github.io/articles/2017-08/voicemeeter-banana-and-virtual-audio-cable-setting) 사용

        ![12]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/12.png)	

     5. 비디오 - 1080p 

        ​	![13]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/13.png)

     6. 고급

        ​	![14]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/14.png)

   * 카카오팟

     1. 주소 입력

        * OBS에 입력하였던 Restream URL과 Stream Key를 이어서 입력합니다.

          ​	![15]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/15.png)

        * 구동하는 게임의 사양에 따라 인코더를 NVENC(고사양), Quick Sync(저사양) 하드웨어 인코딩으로 설정합니다. 방송과 녹화를 동시에 한다면 Quick Sync 인코더로 설정해야 합니다.

          ​		![16]({{ site.url }}/img/2017-08-11-change-from-nginx-to-restream/16.png)