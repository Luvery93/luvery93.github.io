---
layout: post
title:	"Moonlight, Geforce Shield 기능으로 원격에서 게임 실행하기"
date:	2017-07-14 16:28:00 +0900
categories: [Game]
comments: true
---

1. Host 설정
   * Geforece Experience Shield의 GAMESTREAM 옵션 실행
   * Chrome 원격 데스크톱을 통해 로그인한 상태 유지
   * Moonlight Port 설정
     * TCP : 35043, 47984, 47989, 47995~47996, 48010
     * UDP : 47998~48000, 48010
2. Client 설정 - Java(legacy)
   * JRE(JDK) 1.7.0 이상 설치 및 환경 변수 설정
   * [Moonlight PC](https://github.com/moonlight-stream/moonlight-pc/releases)에서 OS에 맞는 .jar 파일 다운로드 및 [Launch4j](http://launch4j.sourceforge.net/)를 통해 윈도우 실행프로그램으로 변경, 혹은 jar 파일 그대로 실행
   * Client에서 Moonlight.exe 실행 후 Host 주소를 입력하면 생성되는 pin code를 Host의 Shield에 입력
   * Host PC가 세션을 가지고 있어야 되므로, pin code 입력시 크롬 원격데스크톱을 이용
   * Geforece Experience 에서 지원하는 게임 및 추가한 게임을 선택 후 실행
3. Client 설정 - Chrome(alpha)
   * [Moonlight Chrome](https://github.com/moonlight-stream/moonlight-chrome/releases/tag/v0.7.3)에서 Chrome용 설치 파일 다운로드 후 [크롬 확장프로그램](chrome://extensions/)에서 드래그 후 설치
   * Client에서 WOL로 Host PC를 킨 후 Host 정보를 추가, Host 주소를 입력하면 생성되는 pin code를 Host의 Shield에 입력
   * Host PC가 세션을 가지고 있어야 되므로, pin code 입력시 크롬 원격데스크톱을 이용
   * Geforece Experience 에서 지원하는 게임 및 추가한 게임을 선택 후 실행
4. Client 설정 - Android(app)
   * Moolight 안드로이드 어플리케이션을 마켓에서 검색 후 설치
   * Android에서 WOL로 Host PC를 킨 후 Host 정보를 추가, Host 주소를 입력하면 생성되는 pin code를 Host Shield에 입력
   * Host PC가 세션을 가지고 있어야 되므로, pin code 입력시 크롬 원격데스크톱을 이용
   * Geforece Experience 에서 지원하는 게임 및 추가한 게임을 선택 후 실행

* PC 연결 시(Java, Chrome) 전체 화면 및 기타 옵션은 성능에 문제가 발생 할 수 있으므로 체크 해제