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
     2. Select game을 선택한 뒤 PUBG경로 C:\Program Files (x86)\Steam\steamapps\common\PUBG\TslGame\Binaries\Win64\TslGame.exe 를 선택합니다.
     3. Direct3D 10+을 선택합니다.
     4. 팝업창의 설치하고자 하는 effect를 전부 해제 한뒤 **AdaptiveSharpen.fx, Technicolor2.fx**만 선택합니다. 각각 선명도, 색감에 관한 효과입니다.
     5. Done 이라는 글자가 보이면 패치가 완료된 것이므로 프로그램을 종료합니다.

2. Pugb 설정

   * 게임 내에서 shift+f2 키를 통해 리쉐이드 오버레이에 접근합니다.
   * Continue를 누른 뒤, + 버튼을 누르고 새 프로파일 이름을 입력하여 작성합니다.
   * Continue를 누른 뒤, 적용하고자 하는 효과인 **AdaptiveSharpen.fx, Techinicolor2.fx**에 단축키를 설정합니다. 그 후 해당 옵션을 단축키를 통해 활성화 합니다.
   * Continue를 누른 뒤, 두 효과의 적용 강도를 조절합니다.
   * 기존 **안티-울트라, 나머지-매우낮음** 설정에서 **거리-중간, 나머지-매우낮음** 설정을 변경하여 그래픽 품질은 그대로이고 시야가 늘어나며 프레임이 안정화되었습니다.

3. 시작옵션 설정

   * 프레임에 직접적인 영향을 끼치는지는 불분명하나 우선 적용중이며 게임 도중 오류가 발생하면 -d3d9를 제외하고 나머지 옵션을 삭제해야 됩니다.


   * -cpuPause 4 -thread 8 -nojoy -high -novid -refresh 144 -heapsize 1572864 -maxMem=8192 -maxVram=3072 -USEALLAVAILABLECORES -malloc=system -d3d9