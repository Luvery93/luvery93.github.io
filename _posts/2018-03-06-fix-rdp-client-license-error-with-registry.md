---
layout: post
title: "원격 데스크톱 서버 클라이언트 엑세스 라이선스 오류"
date: 2018-03-06 17:15 +0900
categories: [Windows]
comments: true
---

* 원격 데스크톱 연결 시 원격 데스크톱 서버 클라이언트 엑세스 라이선스가 없다는 오류가 발생하며 원격데스크톱 세션이 끊어지는 오류가 발생합니다.

  ![1]({{ site.url }}/img/2018-03-06-fix-rdp-client-license-error-with-registry/1.png)

* 원격 데스크톱으로 연결을 시도하는 클라이언트 컴퓨터의 레지스트리 값을 수정함으로 오류를 해결할 수 있습니다.

  1. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\HardwareID 아래의 ClientHWID를 삭제합니다.

     ![2]({{ site.url }}/img/2018-03-06-fix-rdp-client-license-error-with-registry/2.png)

  2. HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\Store\LICENSE000 폴더를 삭제합니다.

     ![3]({{ site.url }}/img/2018-03-06-fix-rdp-client-license-error-with-registry/3.png)

  3. 삭제한 뒤에 레즈스트리 편집기는 아래와 같습니다.

     ![4]({{ site.url }}/img/2018-03-06-fix-rdp-client-license-error-with-registry/4.png)

* 위 과정을 [레지스트리 편집 파일]({{ site.url }}/download/2018-03-06-fix-rdp-client-license-error-with-registry/rdp-client-license-registry.reg)을 통해서 진행할 수 있습니다.

  ```
  Windows Registry Editor Version 5.00

  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\HardwareID]
  "ClientHWID"=-

  [-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\Store\LICENSE000]
  ```