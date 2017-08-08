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

3. [Audio Router](https://github.com/audiorouterdev/audio-router/releases)

   * 특정 프로그램에서 출력 장치를 변경할 수 없는 경우 ( 예를 들어 브라우저 )에 Audio 출력 장치를 전환하는 프로그램입니다.
   * 프로그램 실행 후 출력 장치를 Route 해서 듣고자 하는 스피커로 설정해주면 됩니다.

4. 설정

   * Voicemeeter Banana 와 Virtual Audio Cables를 설치 후 재부팅합니다.

   * 재부팅 후 시스템 트레이의 오디오 설정을 아래와 같이 변경합니다.

     * 재생 : VoiceMeeter Input ( 기본 장치 ), 스피커( 기본 통신 장치 )

     ![1-1]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-1.PNG)

     * 녹음 : CABLE Output( 기본 장치 )

       ​			![1-2]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-2.PNG)

   * VoiceMeeter Banana를 실행 한 뒤 아래와 같이 설정합니다.

     * 우측 상단에 A1, A2, A3에 스피커를 설정합니다. 물리적인 스피커만 설정합니다.

       ![1-3]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-3.PNG)

     * 좌측의 HARDWARE INPUT 1, 2, 3에 물리 마이크와 CABLE Output(VB-Audio Virtual)을 설정합니다. 

       * 물리 마이크의 경우 Voice Meeter Input에 출력되야 하므로 B1 혹은 B2를 체크합니다.

       * CABLE Output(VB-Audio Virtual)은 스피커에만 나가고 Voice Meeter Input에는 출력되지 않도록 A1 혹은 A2에만 체크합니다.

       * VoiceMeeter VAIO는 소리가 출력될 스피커 A1, A2 그리고 소리가 입력될 마이크 B2에 체크합니다.

         ![1-4]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-4.PNG)

     * 설정을 저장하기 위해 우측 상단의 메뉴를 클릭하여 Restart Audio Engine을 실행 시킨 뒤, 윈도우 시작시마다 설정 되도록 System Tray(Run at Startup)에 체크해줍니다.

       ![1-5]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-5.PNG)

   * 방송 송출 프로그램은 모든 오디오 장치를 Disabled 한 다음에 마이크/보조 오디오 장치를 VoiceMeeter Aux Outer(VB-Audio VoiceMeeter AUX VAIO)로 설정합니다.

     ![1-6]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-6.PNG)

   * 스피커에는 출력이 되지만 방송에는 출력을 하지 않고자 하는 특정 프로그램들은 출력 장치를 CABLE Input(VB-Audio Virtual Cable)로 설정하여 줍니다. 위 예제에서는 Voice Meeter Banana의 HARDWARE INPUT 2에 해당합니다.

     ![1-7]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-7.PNG)

   * 스피커에는 출력이 되지만 방송에는 출력을 하지 않고자 하는 특정 프로그램 중 출력 장치를 변경할 수 없는 프로그램들은 Audio Router를 이용하여 출력 장치를 변경합니다.

     * 브라우저는 보통 기본 장치로 출력이 되기 때문에 특정 출력 장치를 선택할 수 없습니다. 따라서 Audio Router에서 출력하고자 하는 스피커로 출력장치를 변경합니다.

       ![1-8]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-8.PNG)

     * 출력 장치가 변경되면 박스 형식으로 손 쉽게 구분 되어있는 것을 확인할 수 있습니다.

       ![1-9]({{ site.url }}/img//2017-08-08-voicemeeter-banana-and-virtual-audio-cable-setting/1-9.PNG)