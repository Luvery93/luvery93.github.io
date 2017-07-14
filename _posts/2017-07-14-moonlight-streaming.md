---
layout: post
title:	"Moonlight, Geforce Shield 기능으로 원격에서 게임 실행하기"
date:	2017-07-14 16:28:00 +0900
categories: [Game]
comment: true
---

1. Host 설정
   * Geforece Experience Shield의 GAMESTREAM 옵션 실행
   * Chrome 원격 데스크톱을 통해 로그인한 상태 유지
   * Moonlight Port 설정
     * TCP : 35043, 47984, 47989, 47995~47996, 48010
     * UDP : 47998~48000
2. Client 설정
   * JRE(JDK) 1.7.0 이상 설치 및 환경 변수 설정
   * [Moonlight PC](https://github.com/moonlight-stream/moonlight-pc/releases)에서 OS에 맞는 .jar 파일 다운로드 및 [Launch4j](http://launch4j.sourceforge.net/)를 통해 윈도우 실행프로그램으로 변경
   * Client에서 Moonlight.exe 실행 후 Host 주소를 입력하면 생성되는 pin code를 Host의 Shield에 입력
   * Geforece Experience 에서 지원하는 게임 및 추가한 게임을 선택 후 실행