---
layout: post
title: "Windows 10의 Hyper-v 가상 머신 생성과 RemoteFx 적용"
date: 2017-11-07 10:09 +0900
categories: [Windows]
comments: true
---

* 원격 데스크톱 (RDP) 이용 시 외부 그래픽카드를 사용하지 못하는 문제가 있어, Windows 10 의 hyper-v 가상 컴퓨터에 RemoteFx 기능을 활용하여 원격 데스크톱 상에서도 외부 그래픽카드를 활용할 수 있도록 합니다.

* 우선 Windows 기능에서 Hyper-v에 관련된 기능을 전부 설치합니다.

  ![1]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/1.png)

  ![2]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/2.png)

  ![3]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/3.png)

* 재부팅 후 Hyper-V 관리자를 실행하여 로컬 컴퓨터에 연결합니다.

  ![4]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/4.png)

  ![5]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/5.png)

  ![6]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/6.png)

* 로컬컴퓨터 내에 새 가상 컴퓨터을 생성합니다.

  ![7]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/7.png)

  ![8]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/8.png)

  ![9]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/9.png)

  ![10]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/10.png)

  ![11]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/11.png)

  ![12]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/12.png)

  ![13]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/13.png)

  ![14]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/14.png)

  ![15]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/15.png)

* 생성된 가상 컴퓨터에 외부 그래픽카드를 설정합니다. RemoteFx 기능을 활용합니다.

  ![16]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/16.png)

  ![17]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/17.png)

  ![18]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/18.png)

* OS 설치를 위해 DVD 드라이버를 설정합니다.

  ![19]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/19.png)

  ![20]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/20.png)

  ![21]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/21.png)

* 네트워크 사용을 위해 가상 스위치를 생성하고 가상 컴퓨터에 설정합니다.

  ![22]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/22.png)

  ![23]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/23.png)

  ![24]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/24.png)

  ![25]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/25.png)

  ![26]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/26.png)

  ![27]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/27.png)

* 가상 컴퓨터를 실행 한 뒤 OS 설치를 진행합니다.

  ![28]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/28.png)

  ![29]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/29.png)

  ![30]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/30.png)

  ![31]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/31.png)

* 외부 그래픽카드를 사용하는 프로그램을 이용할 준비가 완료되었습니다.

  ![32]({{ site.url }}/img/2017-11-07-windows10-hyper-v-and-remotefx/32.png)