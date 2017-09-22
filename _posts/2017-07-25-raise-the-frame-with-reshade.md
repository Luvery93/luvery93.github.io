---
layout: post
title: "배틀그라운드 리쉐이드 적용을 통해 프레임 향상"
date:	2017-07-25 14:12 +0900
categories: [Game]
comments: true
---

1. [Reshade(리쉐이드)](https://reshade.me/)

   * 게임 혹은 영상의 후처리 작업을 통해 그래픽 품질을 향상시키는데 목적이 있는 프로그램입니다.
   * 리쉐이드는 Direct3D 9, Direct3D 10, Direct3D 11, 그리고 OpenGL을 모두 지원합니다.
   * Windows Vista SP1 혹은 그 이상의 운영체제에서 작동하며 [DirectX end-user runtime](https://www.microsoft.com/en-us/download/details.aspx?id=8109)을 필요로 합니다.
   * 2017-07-25 기준 최신 버전은 [3.0.8](https://reshade.me/downloads/ReShade_Setup_3.0.8.exe) 버전입니다.
   * 리쉐이드 적용
     1. 다운로드 받은 ReShade_Setup_3.0.8.exe 를 실행 합니다.

        ![1]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/1.png)

     2. S**elect game**을 선택한 뒤 PUBG 설치 경로를 선택합니다.

        ```
        C:\Program Files (x86)\Steam\steamapps\common\PUBG\TslGame\Binaries\Win64\TslGame.exe
        ```

        ![2]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/2.png)

     3. **Select rendering API**에서 **Direct3D 10+**을 선택합니다.

        ![3]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/3.png)

     4. 리쉐이드 다운로드 확인창이 뜬 뒤, 다운로드가 진행 됩니다.

        ![4]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/4.png)

        ![5]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/5.png)

     5. 다운로드 후 뜨는 팝업창에서 설치하고자 하는 effect를 전부 해제합니다.

        ![6]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/6.png)

     6. 그 후  **AdaptiveSharpen.fx, Technicolor2.fx**만 선택합니다. 각각 선명도, 색감에 관한 효과입니다.

        ![7]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/7.png)

        ![8]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/8.png)

     7. Done 이라는 글자가 보이면 패치가 완료된 것이므로 프로그램을 종료합니다.

        ![9]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/9.png)

     8. 위 과정으로 설치된 파일들을 백업해 둡니다. 리쉐이드로 인한 실행 오류가 발생 했을 시 기존 리쉐이드 설정 파일을 삭제하고 리쉐이드 백업 파일을 덮어쓰기 합니다.

        ![10]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/10.png)

     9. 아래는 리쉐이드 백업파일 입니다.

        [Resade PUBG Backup.zip]({{ site.url }}/download/2017-07-25-raise-the-frame-with-reshade/reshade_backup.zip)

2. Pugb 설정

   * 게임 내에서 shift+f2 키를 통해 리쉐이드 오버레이에 접근합니다.

     ![11]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/11.png)


   * Continue를 누른 뒤, + 버튼을 누르고 새 프로파일 이름을 입력하여 작성합니다.

     ![12]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/12.png)


   * Continue를 누른 뒤, 적용하고자 하는 효과인 **AdaptiveSharpen.fx, Techinicolor2.fx**에 단축키를 설정합니다. 그 후 해당 옵션을 단축키를 통해 활성화 합니다.

     ![13]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/13.png)


   * Finish를 누른 뒤, 두 효과의 적용 강도를 조절합니다.

     ![14]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/14.png)


   * FPS는 Settigns 의 Show FPS를 활성화합니다.

     ![15]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/15.png)

   * 지속되는 PUBG 최적화 패치로 개인 사양에 맞게 PUBG 인게임 옵션을 조정합니다.

     * i7-6700(4.4/4.0 oc), gt970 super jetstream, 16g ram(3000)

       ![16]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/16.png)

3. 시작옵션 설정

   * 프레임에 직접적인 영향을 끼치는지는 불분명하나 우선 적용중이며 게임 도중 오류가 발생하면 옵션을 삭제해야 됩니다.

     ```
     -cpuPause 4 -thread 8 -nojoy -high -novid -refresh 144 -heapsize 1572864 -maxMem=15360 -maxVram=3072 -USEALLAVAILABLECORES -malloc=system
     ```

     ![17]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/17.png)

     ![18]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/18.png)

     * cpuPause : CPU 물리 코어 갯수
     * thread : CPU 논리 코어 갯수
     * nojoy : 패드 리소스 제거
     * high : cpu 사용 우선 순의 높음 설정
     * novid : 동영상 및 로고 무시
     * refresh : 모니터 화면 주사율에 맞춰서 작성
     * heapsize : 3GB 이상 = 1572864
     * maxMem : 최대 동적 메모리 설정, 전체 메모리 - 1GB 설정
       * 16GB : (16-1) * 1024 = 15360
     * maxVram : 그래픽 카드 최대 동적 메모리 설정, 전체 메모리 - 0.5GB 설정
       * GTX 970 : 3.5GB + 0.5GB 의 vram을 지니므로 (3.5 - 0.5) * 1024 = 3072
     * USEALLAVAILABLECORES : 모든 코어를 프로세스에 할당
     * malloc=system : 동적 메모리 할당을 시스템에서 조정

4. TslGame.exe 클라이언트 높은 DPI 조정 동작을 재정의

   * PUBG 설치 경로의 클라이언트 속성의 호환성의 높은 DPI 조정 동작을 재정의 합니다를 체크합니다.

     ```
     C:\Program Files (x86)\Steam\steamapps\common\PUBG\TslGame\Binaries\Win64\TslGame.exe
     ```

     ![19]({{ site.url }}/img/2017-07-25-raise-the-frame-with-reshade/19.png)
