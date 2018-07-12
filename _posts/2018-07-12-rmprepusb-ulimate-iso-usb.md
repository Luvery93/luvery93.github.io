---
layout: post
title: RMPrepUSB로 통합 포맷 USB 만들기
categories: [Windows]
date: 2018-07-12 16:11 +0900
comments: true
---

* 포맷용 USB를 만들 떄 대부분 iso 한개를 담는 USB를 생성하곤 합니다. RMPrepUSB 유틸을 통해서 USB 용량이 허용하는 한에서 OS관계 없이 iso를 실행 시킬 수 있도록 생성할 수 있습니다.

* [RMPrepUSB]({{ site.url }}/download/2018-07-12-rmprepusb-ulimate-iso-usb/RMPrepUSB_Portable.zip)

  * portable 버전을 다운 받은 뒤 아래와 같이 설정합니다.

    ![1]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/1.png)

  * Prepare Drive 버튼을 누르면 확인창과 함께 만들고자하는 통합 USB가 포맷됩니다.

    ![2]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/2.png)

    ![3]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/3.png)

    ![4]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/4.png)

  * 다시 RMPrepUSB로 돌아와 Install grub4dos 버튼을 클릭합니다.

    ![5]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/5.png)

  * 그 이후 통합USB에 [Easy2Boot]({{ site.url }}/download/2018-07-12-rmprepusb-ulimate-iso-usb/Easy2Boot.zip)의 파일들을 복사합니다.

    ![7]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/7.png)

    ![8]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/8.png)

  * _ISO 폴더 아래에 운영 체제에 맞게 분류된 폴더에 ISO를 추가합니다. 이 때 ISO가 운영 체제 목록에 포함되지 않는 경우 _ISO/WINPE 아래에 추가하면 정상적으로 작동합니다.

  * RMPrepUSB로 돌아온 뒤 Drive-Make All File on Drive Contiguous 메뉴 혹은 Crtl+F2버튼을 누르면 통합 USB가 완성됩니다.

    ![10]({{ site.url }}/img/2018-07-12-rmprepusb-ulimate-iso-usb/10.png)