---
layout: post
title: "OBS + NGINX를 통해 RTMP 동시 송출"
date:	2017-07-17 14:42 +0900
categories: [BroadCast]
comment: true
---

1. Open Broadcaster Software

   * [OBS Studio](https://obsproject.com/)는 영상 녹화 및 스트리밍을 간단한 설정으로 가능케 하는 무료 프로그램입니다.
   * 방송 설정은 i7-6700k, gtx 970, 16 g ram 기준으로 설정 테스트 중입니다.
     1. 방송 형식	
        * 사용자 임의 방송 서버 선택
        * URL : rtmp://localhost/live
        * 스트림 키 : {개인 스트림키}
     2. 출력
        * 출력 모드 : 고급
        * 인코더 : QuickSync H.264
          * NVENC H.264 : NVIDIA 그래픽 사용 : 보통 화질, 낮은 CPU 로드율, 외장 VGA 사용
          * QuickSync : Intel CPU 내장 그래픽 사용 : 보통 화질, 낮은 CPU 로드율
          * x264 : Intel CPU 사용 : 선명한 화질, 높은 CPU 로드율
        * 키프레임 : 2
        * 데이터율 제어 : CBR
        * 비트레이트 : 4000
        * 720p, 60fps
     3. 비디오
        * 출력 (조정된) 해상도 : 1280x720 (720p)
        * 공통 FPS 값 : 60
     4. 고급
        * 프로세스 우선순위 설정 : 높음


   * 장면 목록 설정은 우선 순위에 따라 앞으로 나오게 됩니다.
     * 장면 목록 : 게임
     * 소스 목록 :
       * 가림막 : 화면 전부를 가리는 화면, 이미지
       * 트입 : 트위치 twip 이벤트 관련 화면, BrowserSource
       * 통합 채팅창 : JSAssist 통합 채팅창 관련 화면, BrowserSource
       * 게임 화면 : 실행할 게임 화면, 디스플레이 캡쳐
       * 전체 화면 : 전체 화면, 디스플레이 캡쳐

2. NGINX

   * NGINX 는 HTTP, reverse proxy, IMAP/POP3 등 대부분의 웹 관련 서비스를 실행시킬 수 있는 무설치 웹 서버 데몬 프로그램으로 여기에서는 rtmp 서버로의 기능을 사용합니다.
   * RTMP(Real Time Messaging Protocol) : 1935포트를 사용하는 오디오, 비디오 및 기타 데이터를 인터넷을 통해 스트리밍할 떄 쓰이는 통신규약입니다.
   * [NGINX-win32](https://github.com/illuspas/nginx-rtmp-win32)모듈을 다운로드 받은 뒤 .\conf 아래의 nginx.conf를 아래와 같이 수정합니다.

   ```shell
   worker_process	1;
   error_log	logs/error.log debug;
   events {
   	worker_connections	1024;
   }
   rtmp {
   	server {
   		listen 1935;
   		application live {
   			live on;
   			record on;
   			# push rtmp://a.rtmp.youtube.com/live2/{유투브 스트림 키};
   			# push rtmp://live-sel.twitch.tv/app/{트위치 스트림 키};
   		}
   		
   		application hls {
   			live on;
   			hls on;
   			hls_path	temp/hls;
   			hls_fragment	8s;
   		}
   	}
   }
   ```

   * nginx를 종료할 떄에는 nginx.exe 파일 위치에서 아래 커맨드를 입력합니다.

   ```
   nginx.exe -s quit
   ```

3. JSAssist

   * [JSAssist](http://www.js-almighty.com/)는 트위치, 유투브, 카카오 TV 채팅을 HTML5 형식으로 통합 반환시켜주는 프로그램입니다.
   * 다운로드 후 연동방법은 아래와 같습니다.
     * 트위치 : 트위치 송출 시, 트위치 ID 입력
     * 유투브 : 유투브 popout chat에서 chat key 값 입력
     * 카카오 TV:  카카오TV 방송 준비시 실행중인 팟플레이어 프로세스 설정

4. Twippy (twip 전용)

   * [twippy](https://support.twip.kr/hc/ko/articles/115000506168)는 [twip](http://twip.kr/)설정 이후 로컬 프로그램으로 도네이션 관리를 위한 프로그램입니다.
   * twippy 프리셋 설정은 [twip 대시보드](http://twip.kr/dashboard)에서 설정이 가능합니다.
   * twip 대시보드 초기 등록 시 신분증, 본인 명의 계좌 정보(인터넷 뱅킹 스크린샷 가능)이 필요합니다.
   * twip 대시보드 alert box에서 최소 후원 금액과 후원 효과를 설정한 뒤 저장한 프리셋을 등록합니다.

5. 카카오 TV rtmp 소스 설정

   * 카카오 TV는 팟플레이어(카카오 TV)를 실행시켜 입력 소스를 2에서 작성한 소스로 수정해야 합니다.
   * 방송 장치 : 파일 주소를 rtmp://localhost/live/{스트림 키} 로 입력해 줍니다.
   * 팟플레이어를 음소거 해야 음원이 이중 송출되지 않습니다.
   * 팟플레이어 자체가 rtmp 서버가 될 수 있지만 시도는 해보지 않았습니다.