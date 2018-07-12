---
layout: post
title: 원컴 방송 세팅 144hz 모니터와 60hz 캡쳐보드 연결
date: 2018-07-12 15:20 +0900
categories: [BroadCast]
comments: true
---

* 원컴 방송 세팅시 주 모니터의 캡쳐 작업을 캡쳐보드에 맡겨 그래픽 카드의 로드율을 줄이는데 도움을 줄 수 있습니다. 

* 설명하고자 하는 환경은 아래와 같습니다.

  * 주 모니터 : 144hz FHD 모니터
  * 캡쳐보드 : Elgato HD60 pro ( 1080p60 지원 )
  * 그래픽카드 : Nvidia 제품
  * OS : Windows 10

* 그래픽카드에서 주 모니터와 캡쳐보드에 각각 출력 단자를 연결합니다. DVI, HDMI, DP 관계 없이 연결할 수 있는 방법이면 가능합니다.

* Nvidia 제어판의 다중 디스플레이 설정에서 **주모니터(1)**를 복제 소스로  **캡쳐보드 디스플레이(2)**에 복제 대상으로 설정합니다. 만약 복제 소스와 복제 대상을 반대로 설정하면 캡쳐보드에 출력되는 (1080p60) 화면이 주모니터에 복제되어 출력되는 결과가 되므로 144hz 모니터를 활용할 수 없습니다.

  ![1]({{ site.url }}/img/2018-07-12-144hz-monitor-and-60hz-capturecard-setting-in-single-computer/1.png)

* 다음 해상도 변경에서 주 모니터의 해상도와 주사율을 변경합니다.

  ![2]({{ site.url }}/img/2018-07-12-144hz-monitor-and-60hz-capturecard-setting-in-single-computer/2.png)

* 그렇게 되면 캡쳐보드의 해상도와 주사율이 자동으로 설정됩니다.

  ![3]({{ site.url }}/img/2018-07-12-144hz-monitor-and-60hz-capturecard-setting-in-single-computer/3.png)

* 윈도우 디스플레이 설정에서도 복제 화면으로 묶인 것을 확인할 수 있습니다.

  ![4]({{ site.url }}/img/2018-07-12-144hz-monitor-and-60hz-capturecard-setting-in-single-computer/4.png)