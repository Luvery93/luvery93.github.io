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

     * VoiceMeeter Input - 기본 시스템 재생장치, VoiceMeeter Output, VoiceMeeter Aux Output 포함
     * VoiceMeeter Output - 물리 마이크 입력, 기본 시스템 녹음장치
     * VoiceMeeter Aux Output - 물리 마이크 입력, 방송 송출용 마이크로 설정

   * 재부팅 후 시스템 트레이의 오디오 설정을 아래와 같이 변경합니다.

     * 재생 : VoiceMeeter Input ( 기본 장치/기본 통신 장치 )

       ![1]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1.png)

     * 녹음 : VoiceMeeter Output ( 기본 장치/기본 통신장치 )

       ![2]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/2.png)

   * VoiceMeeter Banana를 실행 한 뒤 아래와 같이 설정합니다.

     * 우측 상단에 A1, A2, A3에 스피커를 설정합니다. 물리적인 스피커만 설정합니다.

       ![3]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/3.png)

     * 좌측 상단 HARDWARE INPUT 1에 물리마이크를 설정합니다. 물리마이크의 경우 음성채팅과 방송용 마이크에 출력되야 하므로 B1(VoiceMeeter Output), B2(VoiceMeeter Aux Output)에 모두 출력되도록 설정합니다.

       ![4]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/4.png)

     * 좌측 상단 HARDWARE INPUT 2에 CABLE Output을 설정합니다. CABLE Output(VB-Audio Virtual)을 따로 설정하여 기본 시스템 사운드(VoiceMeeter Input)에 합치거나 제외시키거나 하는 설정을 선택할 수 있습니다. 기본적으로 시스템 사운드 이므로 물리 스피커(A1, A2)에 체크합니다.

       * 예를 들어 음성채팅 대화내용을 방송용 마이크에 섞이지 않기 위해서는 B2(VoiceMeeter Aux Output)를 체크 해제합니다.

       ![5]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/5.png)

       * 반대로 음성채팅 대화내용을 섞이게 하기위해선 B2(VoiceMeeter Aux Output)에 체크합니다.

       ![6]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/6.PNG)

     * 좌측 상단 HARDWARE INPUT 3에 물리마이크 2를 설정합니다. HARDWARE INPUT 1에 설정한 마이크 설정과 같습니다.

       ![7]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/7.png)

     * 설정을 저장하기 위해 우측 상단의 메뉴를 클릭하여 Restart Audio Engine을 실행 시킨 뒤, 윈도우 시작시마다 설정 되도록 System Tray(Run at Startup)에 체크해줍니다.

       ![8]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/8.png)

     * 실 사용 예시입니다.

       * HARDWARE INPUT 1, HARDWARE INPUT 2, HARDWARE INPUT 3는 결국 시스템 사운드에 믹스될 수 있는 소스입니다. VoiceMeeter Aux Output( 방송용 출력 마이크 )에 모든 소리를 출력하고자 한다면 VoiceMeeter Aux Output( B2 ) 출력 설정을 각각의 마이크와 VoiceMeeter Input ( 시스템 사운드 )에 설정합니다.

         ![9]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/9.png)

       * HARDWARE INPUT 1 과 HARDWARE INPUT 3는 물리마이크로 실제 소리가 입력됩니다. 프로그램마다 마이크 설정을 변경할 필요없이 VoiceMeeter Output(B1)으로 마이크 소리를 리다이렉트하면 VoiceMeeter Output 마이크 설정으로 언제든지 두 물리마이크를 사용하실 수 있습니다.

         ![10]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/10.png)

       * 마이크 사용시 테스트를 위해서 자기 자신의 소리를 확인해야될 경우가 있습니다. 약간의 딜레이가 존재하지만 마이크 소리 및 잡음을 테스트해보려면 물리마이크에 실제 물리스피커(A1, A2)를 설정하면 VoiceMeeter Input( 시스템 사운드 )로 나가는 소리를 확인하실 수 있습니다.

         ![11]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/11.png)

   * 기타 음원 관련 프로그램 설정을 진행합니다.

     * 방송 송출 프로그램은 모든 오디오 장치를 Disabled 한 다음에 마이크/보조 오디오 장치를 B1인 경우 VoiceMeeter Output(VB-Audio VoiceMeeter VAIO), B2인 경우 VoiceMeeter Aux Output(VB-Audio VoiceMeeter AUX VAIO)로 설정합니다.

       ![12]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/12.png)

     * 음성 채팅 프로그램은 출력 장치를 CABLE Input(VA-Audio Virtual Cabel)로 입력 장치를 물리마이크로 설정합니다.

       ![13]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/13.png)

       ![14]({{ site.url }}/img/2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/14.png)

     ​

     ​
