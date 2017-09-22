---
layout: post
title: "Voicemeeter banana 와 Virtual Audio Cable 설정"
date: 2017-08-08 10:43 +09:00
categories: [BroadCast]
comments: true
---

1. [Voicemeeter Banana](http://www.vb-audio.com/Voicemeeter/banana.htm)

   * Voicemeeter Banana는 윈도우 전용 가상 오디오 믹서입니다. 
   * 오디오 믹서 기능 외에도 EQ 설정과 음성 녹음을 지원합니다.
   * 2017-08-08 기준 Voicemeeter 2.0.3.4버전이 최신입니다.

2. [Virtual Audio Cables](http://www.vb-audio.com/Cable/index.htm)

   * 기본적으로 모든 사운드는 윈도우 출력 기기로 모이게 됩니다.
   * 특정 프로그램에서 출력 장치를 Virtual Audio Cable로 설정한다면 윈도우 기본 출력 기기에는 사운드가 들어가지 않게 됩니다.
   * Voicemeeter Banana에 가상 입력으로 Virtual Audio Cable를 추가하면 특정 프로그램의 출력을 조정할 수 있습니다.

3. 설정

   * Voicemeeter Banana 와 Virtual Audio Cables를 설치 후 재부팅합니다.

   * 재부팅 후 시스템 트레이의 오디오 설정을 아래와 같이 변경합니다.

     * 재생 : VoiceMeeter Input ( 기본 장치/기본 통신 장치 )

       ![1]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1.png)

     * 녹음 : 사용하는 마이크 장치(기본 장치/기본 통신장치 )

       ![2]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/2.png)

   * VoiceMeeter Banana를 실행 한 뒤 아래와 같이 설정합니다.

     * 우측 상단에 A1, A2, A3에 스피커를 설정합니다. 물리적인 스피커만 설정합니다.

       ![3]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/3.png)

     * 좌측 HARDWARE INPUT 1에 물리마이크를 설정합니다. 물리 마이크의 경우 VoiceMeeter Output에 출력되려면 B1, VoiceMeeter Aux Output에 출력되려면 B2로 설정합니다.

       ![4]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/4.png)

     * 좌측 상단 HARDWARE INPUT 2에 CABLE Output을 설정합니다. CABLE Output(VB-Audio Virtual)은을 자기 자신만 스피커로 듣기 위해서는 A1, A2(물리 스피커)에 체크합니다.

       ![5]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/5.PNG)

     * 좌측 상단 HARDWARE INPUT 2에 CABLE Output을 물리 마이크 처럼 시스템에 믹스하기 위해 B1(VoiceMeeter Output), 혹은 B2(VoiceMeeter Aux Output)를 설정합니다.

       ![6]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/6.png)

     * 설정을 저장하기 위해 우측 상단의 메뉴를 클릭하여 Restart Audio Engine을 실행 시킨 뒤, 윈도우 시작시마다 설정 되도록 System Tray(Run at Startup)에 체크해줍니다.

       ![7]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/7.png)

   * 기타 음원 관련 프로그램 설정을 진행합니다.

     * 방송 송출 프로그램은 모든 오디오 장치를 Disabled 한 다음에 마이크/보조 오디오 장치를 B1인 경우 VoiceMeeter Output(VB-Audio VoiceMeeter VAIO), B2인 경우 VoiceMeeter Aux Output(VB-Audio VoiceMeeter AUX VAIO)로 설정합니다.

       ![8]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/8.png)

     * 음성 채팅 프로그램은 출력 장치를 CABLE Input(VA-Audio Virtual Cabel)로 입력 장치를 물리마이크로 설정합니다.

       ![9]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/9.png)

       ![10]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/10.png)

     ​

     ​
