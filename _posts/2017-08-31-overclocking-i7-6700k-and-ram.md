---
layout: post
title: "Intel I7-6700k, ram overclock"
categories: [Windows]
date: 2017-08-31 15:47 +09:00
comments: true
---

1. 시스템 사양

   * CPU : i7-6700k
   * M/B : ASUS Z170 PRO GAMING
   * RAM : SAMSUNG DDR4 16G PC4-17000
   * 시스템 오버클록은 시스템 사양 및 수율에 따라 개개인의 차이가 있습니다.

2. 램 오버

   * RAM 오버를 우선 진행해야, CPU 오버 시의 전압을 안정적으로 가져갈 수 있습니다.

   * BIOS 화면에 진입한 뒤 Advanced Mode(F7)로 진입합니다.

     ![1]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/1.png)

   * Ai Tweaker 탭을 선택한 뒤, DRAM Frequency, DRAM Timing Control, DRAM Voltage를 변경하여 오버를 진행합니다.

     * DRAM Frequency : DDR4-3000MHz

     * DRAM Timing Control

       * DRAM CAS# Latency : 17
       * DRAM RAS# to CAS# Delay : 17
       * DRAM RAS# ACT Time : 36
       * DRAM Command Rate : 1

     * DRAM Voltage : 1.35

       ![2]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/2.png)

       ![3]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/3.png)

       ![4]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/4.png)	

   * 이 후 안정화 테스트를 진행합니다.

3. CPU 오버

   * 2017-08-30 실 사용 44 배수(캐시 40배수), 1.260 입니다. (1.250 안정화)

   * Ai Tweaker 에서 순서대로 설정 값을 변경합니다.

     * Ai Overclock Tuner : Manual
     * BCLK Frequency : 100.00
     * CPU Core Ratio : Sync All Cores
     * 1-Core Ratio Limit : 44
     * Min. CPU Cache Ratio : 40
     * Max. CPU Cache Ratio : 40
     * CPU Core/Cache Voltage : Manual
     * CPU 코어 전압 재정의 : 1.260
     * CPU Load-line  Calibration : Level 6

     ![5]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/5.png)

     ![6]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/6.png)

     ![7]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/7.png)

     ![8]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/8.png)

     ![9]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/9.png)

   * CPU 전력 설정을 합니다.

     ![10]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/10.png)

     ![11]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/11.png)

     ![12]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/12.png)

4. 안정화 테스트

   * Linx 0.6.4 : CPU 및 RAM 과부화 프로그램

   * CPUID HWMonitor : 전력, 온도 체크 프로그램

   * CPU-Z : 전력, CPU Ghz, DRAM Frequency 체크 프로그램

   * RealTemp : CPU 온도 체크 프로그램

   * Linx 0.6.4 10회 - 20회 테스트 완료까지 에러가 발생하거나 온도가 높아 LOG가 발생하면 전압과 클럭을 낮추는 방식으로 진행하며 해당 클럭 및 전압을 무사히 통과하면 전압을 차례로 낮추는 방식으로 진행합니다.

   * 최종 안정화 이후 실사용시에는 전압을 한두단계 올려 사용합니다.

     ![13]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/13.png)

   * CPU-Z에서 Core Speed가 44배수 즉 4.4GHz로 오버되었음을 확인할 수 있습니다.

     ![14]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/14.png)

   * CPU-Z에서 Memory가 1499.6MHz ( = 3000Mhz)로 오버되었음을 확인할 수 있습니다.

     ![15]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/15.png)

   * Linx 과정 중 1회차가 완료된 과정입니다.

     ![16]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/16.png)

   * Linx 도중 RealTemp로 확인한 CPU 온도 정보입니다. Thermal Status가 전부 OK로 나와있습니다. 이 값이 LOG 혹은 HOT으로 변경된다면 전압과 클럭을 낮추거나 쿨링 과정을 점검해야합니다.

     ![17]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/17.png)

   * Linx 도중 HWMonitor로 확인한 CPU 정보입니다. Voltages의 전압갑이 비정상적으로 튀거나, Temperatures의 값이 높다면 전압과 클럭을 조정해야합니다.

     ![18]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/18.png)

   * Linx 도중 GFlops 값의 편차가 1보다 작고 Residual 값이 같아야 정상적인 진행입니다.

     ![19]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/19.png)

   * Linx 테스트 이후 전체 테스트 화면입니다.

     ![20]({{ site.url }}/img/2017-08-31-overclocking-i7-6700k-and-ram/20.png)