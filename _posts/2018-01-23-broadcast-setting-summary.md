---
layout: post
title: "원컴방송 다중송출 설정 정리"
date: 2018-01-23 10:09 +0900
categories: [Broadcast]
comments: true
---

```
컴퓨터 한대로 게임 진행과 다중 플랫폼에 스트리밍하기 위한 방법에 대해 정리합니다.

방송에 사용되는 시스템 사양은 아래와 같습니다.
	CPU : i7-6700k@4.4 o.c
	RAM : 16G@3000 o.c
	M/B : ASUS Z170 programing
	VGA : NVIDIA Geforce GTX 970
	C/B : Elgato HD60 pro (new)
	A/I : Behringer UMC202hd
	M/C : Shure SM58
	CAM : Logitech C920

방송에 사용되는 프로그램이나 아래 설명할 키워드를 나열합니다.
	OBS studio
	OBS Virtual Cam
	Nginx rtmp server windows
	Nginxtool
	Restream.io
	Voicemeeter banana
	Virtual Audio Cable
	Noboard
	Potplayer
```

1. [OBS](https://obsproject.com/ko)

   * OBS는 영상 녹화와 실시간 스트리밍을 할 수 있는 무료 공개 소프트웨어 입니다.
   * 원컴방송에서 그래픽카드가 게임 구동에 대부분의 성능을 사용한다면, 캡쳐카드를 사용하는 것은 바람직한 선택입니다.
   * 아래 예시 설정은 nginx-rtmp 서버를 사용할 떄의 obs 설정입니다.
   * 4번의 [OBS VirtualCam](https://obsproject.com/forum/resources/obs-virtualcam.539/)은 팟플레이어에서 OBS 화면을 출력할 때 필요한 플러그인으로 팟플레이어 항목과 연관지어 보시길 바랍니다.

   1. 장면 당 여러개의 소스를 추가하여 송출하고자 하는 화면을 구성합니다. 미리보기 화면을 보고 작업하시면 어렵지 않습니다.

      ![1]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/1.png)

   2. 소스 목록에 추가하게 되는 대표적인 요소는 BrowseSource, 비디오 캡쳐 장치,  윈도우 캡쳐 등이 있습니다.

      ![2]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/2.png)

      ![3]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/3.png)

      ![4]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/4.png)

   3. Browse로 추가된 알림창과 채팅창은 [twip](http://twip.kr/), [afreehp](http://afreehp.kr/)에서 제공하는 서비스입니다.

      ![5]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/5.png)

      ![6]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/6.png)

      ![7]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/7.png)

      ![8]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/8.png)

   4. 스트리밍 출력, 인코딩, 오디오 및 비디오 설정을 진행합니다.

      ![9]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/9.png)

      ![10]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/10.png)

      ![11]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/11.png)

      ![12]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/12.png)

      ![13]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/13.png)

      ![14]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/14.png)

   5. [OBS VirtualCam](https://obsproject.com/forum/resources/obs-virtualcam.539/) 플러그인 설정 후 타 프로그램(ex 팟플레이어)에서 OBS화면을 입력받을 수 있습니다.

      ![15]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/15.png)

      ![16]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/16.png)

2. [Nginx-rtmp](https://github.com/illuspas/nginx-rtmp-win32) & [Nginxtool]({{ site.url }}/download/2018-01-23-broadcast-setting-summary/nginxtool.zip)

   * Nginx는 HTTP, reverse proxy IMAP/POP3 등 대부분의 웹서비스를 실행할 수 있는 무설치 웹 서버 데몬 프로그램으로써 여기서는 1935 포트를 이용하는 RTMP(Real Time Messaging Protocol)서버로 작동하게 됩니다.
   * Nginxtool은 nginx-rtmp-win32의 작동을 관리하는 GUI tool로서 현재 nginx 서버의 환경 설정 정보와 프로세스 시작유무를 관리할 수 있습니다.

   1. nginx-rtmp-win32 와 nginxtool을 다운로드한 뒤 설정합니다.

      ![17]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/17.png)

      ![18]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/18.png)

      ![19]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/19.png)

      ![20]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/20.png)

      ```
      worker_process	1;
      error_log	logs/error.log debug;
      events {
      	worker_connections	1024;
      }
      rtmp {
      	server {
      		listen 1935;
      		application live {
      			live on;
      			record off;
      			
      			push rtmp://{rtmp server ip주소}/stream/{stream key};
      			# push rtmp://a.rtmp.youtube.com/live2/{유투브 스트림 키};
      			# push rtmp://live-sel.twitch.tv/app/{트위치 스트림 키};
      		}
         		
      		application hls {
      			live on;
      			hls on;
      			hls_path	temp/hls;
      			hls_fragment	8s;
      		}
      	}
      }
      ```

   2. nginxtool을 실행하고 nginx-rtmp 서버가 작동되는지 확인할 수 있습니다.

      ![21]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/21.png)

      ![22]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/22.png)

3. [Voicemeeter Banana](https://www.vb-audio.com/Voicemeeter/banana.htm) & [Virtual Audio Cable](https://www.vb-audio.com/Cable/index.htm)

   * Voicemeeter Banana와 Virtual Audio Cable은 각각 가상 오디오 믹서와 가상 오디오 녹음 장치입니다.
   * 보통 오디오 인터페이스가 따로 없는 경우 시스템 사운드와 음성채팅 사운드를 구분하여 방송할 때 사용하게 됩니다.

   1. Voicemeeter Banana와 Virtual Audio Cable을 설치한 뒤 기본 장치를 설정합니다.

      ![23]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/23.png)

      ![24]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/24.png)

   2. Voicemeeter Banana를 현재 시스템 설정에 맞게 수정합니다. 좀 더 자세한 설명은 [여기](https://luvery93.github.io//articles/2017-08/voicemeeter-banana-and-virtual-audio-cable-setting)를 참고해주세요.

      ![25]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/25.png)

      ![26]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/26.png)

   3. 음성 채팅 프로그램에서 출력 장치를 Virtual Audio Cable로 수정하여 기본 시스템 사운드와 따로 관리합니다.

      ![27]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/27.png)

4. [Restream.io](https://restream.io)

   * 플랫폼에 따라 재 인코딩을 하는 문제는 nginx-rtmp로 해결할 수 있지만 송출 서비스의 업로드 속도의 제한이나 nginx-rtmp 유튜브 송출 시 발생하는 버퍼링 등을 해결하기 위해  채택하게 된 멀티스트리밍 서비스입니다.
   * restream 서울 서버를 거치기때문에 딜레이가 최대 수초 증가할 수 있으나 restream 서버로의 송출이 안전하다면 멀티스트리밍 자체가 안전하게 송출된다고 볼 수 있습니다.
   * 다만 restream 자체 내부의 문제로 송출이 원활하지 않을 경우를 대비해 niginx-rtmp로 다중송출하는 하는 방안을 마련해 두어야 합니다.

   1. Restream은 가이드에 따라 쉽게 송출 플랫폼을 추가할 수 있습니다.

      ![28]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/28.png)

      ![29]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/29.png)

      ![30]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/30.png)

      ![31]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/31.png)

      ![32]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/32.png)

      ![33]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/33.png)

      ![34]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/34.png)

      ![35]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/35.png)

      ![36]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/36.png)

      ![37]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/37.png)

5. [Potplayer(KaKaoTV)](https://tv.kakao.com/guide/potplayer)

   * 카카오TV에서 방송하기 위해서는 카카오TV에서 rtmp를 공개하지 않는 이상 팟플레이어를 거쳐야 합니다.
   * OBS를 통해 인코딩 된 화면을 받아와 송출하거나 nginx-rtmp 신호를 받아와 송출하거나 VirtualCam으로 OBS화면을 송출하는 방법 등이 있습니다.

   1. 팟플레이어 설치 후 팟플레이어 CPU 점유율 낮추는 설정을 진행합니다.

      ![38]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/38.png)

      ![39]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/39.png)

      ![40]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/40.png)

      ![41]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/41.png)

   2. 송출할 영상 소스를 받아옵니다.

      ![42]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/42.png)

      ![43]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/43.png)

      ![44]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/44.png)

      ![45]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/45.png)

   3. 인코딩 설정 후 방송을 송출합니다.

      ![46]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/46.png)

      ![47]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/47.png)

      ![48]({{ site.url }}/img/2018-01-23-broadcast-setting-summary/48.png)