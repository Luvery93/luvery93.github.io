---
layout: post
title: ASUS Z170 BIOS 기타 설정
date: 2017-09-22 16:32 +09:00
categories: [Windows]
comments: true
---

1. 외장그래픽 연결 시 비활성화 되는 내장 그래픽 활성화

   * Advanced - System Agent(SA) Configuration - Graphics Configuration의 iGPU 다중 모니터를 활성화 합니다. 활성화 이후 내장 그래픽 및 외장 그래픽을 전부 사용하게 되므로 모니터 출력 및 하드웨어 인코딩이 가능하게 됩니다.

   ![1]({{ site.url }}/img/2017-09-22-asus-z170-mainboard-setting-etc/1.png)

2. USB로 연결된 키보드 입력으로 컴퓨터 전원 켜기

   * Advanced - APM - Power On By PCI-E(PCI-E로 전원 켜기)를 활성화합니다. 키보드의 아무 키를 입력하면 컴퓨터 전원이 켜지게 됩니다.

   ![2]({{ site.url }}/img/2017-09-22-asus-z170-mainboard-setting-etc/2.png)