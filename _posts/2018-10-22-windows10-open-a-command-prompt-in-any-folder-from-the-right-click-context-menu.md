---
layout: post
title: 윈도우 10 오른쪽 메뉴에 [여기서 명령창 열기] 추가하기
categories: [Windows]
date: 2018-10-22 15:08 +0900
comments: true
---

* 아래 그림과 같이 윈도우10의 **오른쪽 클릭**과 **Shift + 오른쪽 클릭** 메뉴에 "여기서 명령창 열기"가 존재하지 않습니다.

  ![1]({{ site.url }}/img/2018-10-22-windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu/1.png)

  ![2]({{ site.url }}/img/2018-10-22-windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu/2.png)

* 이 때 오른쪽 클릭 메뉴에 관련된 레지스트리를 수정하면 **Shift + 오른쪽 클릭** 메뉴에 "**여기서 명령창 열기**"를 추가할 수 있습니다.

  * 추가 : [레지스트리 파일]({{ site.url }}/download/2018-10-22-windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu/add_open_cmd_here_for_windows10.reg)

    ```
    Windows Registry Editor Version 5.00
    
    [HKEY_CLASSES_ROOT\Directory\shell\cmdprompt]
    @="@shell32.dll,-8506"
    "Extended"=""
    "NoWorkingDirectory"=""
    
    [HKEY_CLASSES_ROOT\Directory\shell\cmdprompt\command]
    @="cmd.exe /s /k pushd \"%V\""
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\cmdprompt]
    @="@shell32.dll,-8506"
    "Extended"=""
    "NoWorkingDirectory"=""
    
    [HKEY_CLASSES_ROOT\Directory\Background\shell\cmdprompt\command]
    @="cmd.exe /s /k pushd \"%V\""
    
    [HKEY_CLASSES_ROOT\Drive\shell\cmdprompt]
    @="@shell32.dll,-8506"
    "Extended"=""
    "NoWorkingDirectory"=""
    
    [HKEY_CLASSES_ROOT\Drive\shell\cmdprompt\command]
    @="cmd.exe /s /k pushd \"%V\""
    
    ```

  * 복원 : [레지스트리 파일]({{ site.url }}/download/2018-10-22-windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu/restore_open_cmd_here_for_windows10.reg)

    ```
    Windows Registry Editor Version 5.00
    
    [-HKEY_CLASSES_ROOT\Directory\shell\cmdprompt]
    
    [-HKEY_CLASSES_ROOT\Directory\Background\shell\cmdprompt]
    
    [-HKEY_CLASSES_ROOT\Drive\shell\cmdprompt]
    
    ```

* 그 결과 아래와 같이 **Shift + 오른쪽 클릭 메뉴**에 "**여기서 명령창 열기**"가 추가되었음을 확인할 수 있습니다.

  ![3]({{ site.url }}/img/2018-10-22-windows10-open-a-command-prompt-in-any-folder-from-the-right-click-context-menu/3.png)