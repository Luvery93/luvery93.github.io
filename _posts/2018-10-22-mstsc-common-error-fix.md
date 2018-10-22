---
layout: post
title: 원격 데스크톱 연결 일반적인 연결 오류 해결
categories: [Windows]
date: 2018-10-22 11:38 +0900
comments: true
---

* 원격 데스크톱 연결로 접근하고자 하는 컴퓨터의 원격 설정에 따라 아래와 같은 문제가 자주 발생하여 이를 기록합니다.

1. 원격 데스크톱 연결 설정에서 Oracle 수정 암호화 그룹 정책 값을 변경하여 아래와 같이 "**인증 오류가 발생했습니다**" 라는 오류가 발생할 경우

   ![1]({{ site.url }}/img/2018-10-22-mstsc-common-error-fix/1.png)

* 원격 데스크톱 연결을 실행하는 컴퓨터에서 "**gpedit.msc**"를 실행하여 로컬 그룹 정책 편집기를 연 뒤, "**관리 템플릿-시스템-자격 증명 위임**"으로 접근하여 "**Oracle 수정 암호화**" 를 편집합니다.

  ![2]({{ site.url }}/img/2018-10-22-mstsc-common-error-fix/2.png)

* "**Oracle 수정 암호화**"의 설정 값을 "**사용(E)**"로 변경한 뒤, 보호 수준을 "**취약**"으로 설정합니다.

  ![3]({{ site.url }}/img/2018-10-22-mstsc-common-error-fix/3.png)

2. 윈도우 서버 운영체제로 원격 데스크톱 연결을 진행할 때, "**원격 데스크톱 서버 클라이언트 엑세스가 없으므로 원격 세션 연결이 끊어졌습니다**" 라는 오류가 발생합니다.

   ![4]({{ site.url }}/img/2018-10-22-mstsc-common-error-fix/4.png)

* 이 경우에는 레지스트리에서 원격 데스크톱 연결에 사용하는 "ClientHWID" 의 값을 삭제합니다. 아래와 같은 레지스트리 설정 문구를 [".reg"파일]({{ site.url }}/download/2018-10-22-mstsc-common-error-fix/mstsc_client_access_error_fix.reg)로 저장한 뒤 실행하여 적용시킬 수 있습니다. 

  ```
  Windows Registry Editor Version 5.00
  
  [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\HardwareID]
  "ClientHWID"=-
  
  [-HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSLicensing\Store\LICENSE000]
  ```