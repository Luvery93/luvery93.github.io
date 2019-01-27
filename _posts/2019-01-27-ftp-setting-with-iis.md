---
layout: post
title: Windows FTP 설정하기(IIS)
categories: [Windows]
date: 2019-01-27 14:19 +0900
comments: true
---

* 이 글은 윈도우에서 **IIS(인터넷 정보서비스, 이하 IIS)**를 통해 FTP를 구축하는 과정을 정리합니다. Windows FTP서버는 FTP가 설정된 컴퓨터가 전원이 켜있는 상태에서만 이용가능하며 원격지에서 컴퓨터 전원관리를 위해서는 [이글](https://luvery93.github.io/articles/2017-09/change-router-to-iptime-a2003ns-mu)을 통해 **WOL 기능**을 활용하시길 바랍니다.

* 제어판에서 **IIS - FTP 기능**을 켭니다.

  ![1]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/1.png)

  ![2]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/2.png)

* FTP로 사용할 폴더를 생성합니다.

  ![3]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/3.png)

* **시작 - 모든 프로그램 - Windows 관리 도구**에서 **IIS 관리자**를 실행합니다.

  ![4]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/4.png)

* IIS에서 사이트에 오른쪽 클릭 후 **FTP 사이트 추가**를 진행합니다.

  ![5]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/5.png)

* **FTP 사이트 이름**과 위에서 생성한 **FTP 실제 폴더 경로**를 설정합니다.

  ![6]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/6.png)

* IP 주소는 기본 IPv4 주소나 지정하지 않은 **기본 호스트주소**로 설정하고 포트도 **기본 21**로 설정합니다. SSL 인증서가 있는 환경에서만 SSL을 허용합니다.

  ![7]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/7.png)

* 익명 인증은 FTP 사용 시 누구나 사용할 수 있도록 허용하는 것이고 기본 인증은 윈도우 로컬 계정이나 그룹에 한해 이용가능하도록 허용할 수 있습니다. 우선은 **기본 인증과 모든 사용자에 대해 읽기/쓰기 권한**을 넣습니다. 이 설정은 FTP사이트가 생성된 후 **FTP 인증**에서 변경할 수 있습니다.

  ![8]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/8.png)

  ![9]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/9.png)

  ![10]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/10.png)

* 다음으로 FTP에 사용할 계정을 생성합니다. **윈도우 탐색기 - 내 PC에서 우클릭 - 관리 페이지**를 엽니다.

  ![11]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/11.png)

* 관리페이지의 **시스템 도구 - 로컬 사용자 및 그룹 - 사용자**에서 기본 사용자(여기에서는 young)이 외에 FTP이용을 위한 새 사용자를 생성합니다.

  ![12]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/12.png)

  ![13]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/13.png)

  ![14]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/14.png)

* 다시 IIS로 돌아가 **FTP 권한 부여 규칙**을 선택합니다. 모든 사용자에 대해 허용된 권한 규칙을 제거하고 위에서 생성한 FTP 전용 계정에 권한을 부여합니다.

  ![15]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/15.png)

  ![16]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/16.png)

  ![17]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/17.png)

  ![18]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/18.png)

  ![19]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/19.png)

* 위 설정으로 **내부망에서 FTP 사용**은 완료되었습니다. 다음은 iptime사용자에 한해 **포트포워딩 기능**으로 외부에서 FTP 사용이 가능하도록 설정합니다. iptime 기본 설정은 [이글](https://luvery93.github.io/articles/2017-09/change-router-to-iptime-a2003ns-mu)을 참고하여 DDNS설정을 해주시길 바랍니다. 공유기 관리페이지로 이동하여 FTP 설정합니다.

  ![20]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/20.png)

  ![21]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/21.png)

  ![22]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/22.png)

* 외부망에서 **ftp://{DDNS 호스트이름}.iptime.org** 를 탐색기에 검색하고 위에서 생성한 **FTP 계정으로 접속**후 정상적으로 FTP 사용이 가능합니다.

  ![23]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/23.png)

  ![24]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/24.png)

  ![25]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/25.png)

  ![26]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/26.png)

* FTP 이용시 아래와 같이 **한글로 된 파일**을 송수신할 때 발생하는 오류는 IIS에서 **FTP 사이트 - 고급 설정 - UTF8허용** 옵션을 **False**로 변경하고 재시작합니다.

  ![27]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/27.JPG)

  ![28]({{ site.url }}/img/2019-01-23-ftp-setting-with-iis/28.png)

* FTP 계정이 없이 **익명 인증**으로 이용할 때 외부망에서 접속이 불가한 경우 [이글](https://luvery93.github.io/articles/2018-07/add-ftp-inbound-option-in-windows-defender)을 참고하시길 바랍니다.