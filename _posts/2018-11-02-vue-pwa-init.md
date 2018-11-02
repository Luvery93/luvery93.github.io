---
layout: post
title: Vue.js PWA 프론트앤드 개발 1
categories: [Development]
date: 2018-11-02 16:08 +0900
comments: true
---

1. npm 사용을 위해 node.js를 설치합니다.

   * [여기](https://nodejs.org/en/)에서 node.js를 설치하면 필요한 파일은 자동으로 설정을 잡아줍니다. Windows 10에서는 아래와 같이 PowerShell에서 설치 내용이 보입니다.

     ![1]({{ site.url }}/img/2018-11-02-vue-pwa-init/1.png)

2. Vue 사용을 위해 초기 설정을 진행합니다.

   * [여기](https://kr.vuejs.org/v2/guide/installation.html)에서 가이드라인에 따라 진행합니다.

   * vue CLI를 설치합니다.

     ```
     npm install -g vue-cli
     ```

     ![2]({{ site.url }}/img/2018-11-02-vue-pwa-init/2.png)

   * vue cli로 pwa 템플릿을 생성합니다.

     ```
     vue install pwa printanywhere-client
     ```

     ![3]({{ site.url }}/img/2018-11-02-vue-pwa-init/3.png)

   * node-module을 설치합니다.

     ```
     cd printanywhere-client
     npm install
     ```

     ![4]({{ site.url }}/img/2018-11-02-vue-pwa-init/4.png)

   * vue 초기 페이지를 실행해봅니다.

     ```
     npm run dev
     ```

     ![5]({{ site.url }}/img/2018-11-02-vue-pwa-init/5.png)

     ![6]({{ site.url }}/img/2018-11-02-vue-pwa-init/6.png)

   * 아래와 같은 페이지를 확인할 수 있습니다.

     ![7]({{ site.url }}/img/2018-11-02-vue-pwa-init/7.png)

3. Vscode에서 Vue 코드를 보기 위한 extension 설치합니다.

   * *.vue 파일의 시각화를 위해 아래 extension을 설치합니다.

     ![8]({{ site.url }}/img/2018-11-02-vue-pwa-init/8.png)

   * extension은 아래와 같은 코드를 좀더 식별하기 쉽게 돕습니다.

     ![9]({{ site.url }}/img/2018-11-02-vue-pwa-init/9.png)

     ![10]({{ site.url }}/img/2018-11-02-vue-pwa-init/10.png)

4. local:8080의 환경을 외부에서 접근 가능하도록 ngrok을 설치합니다.

   * ngrok을 설치합니다.

     ```
     npm install -g ngrok
     ```

     ![11]({{ site.url }}/img/2018-11-02-vue-pwa-init/11.png)

   * ngrok 을 실행합니다.

     ```
     ngrok http 8080
     ```

     ![12]({{ site.url }}/img/2018-11-02-vue-pwa-init/12.png)

5. Forwarding 된 주소로 다른 네트워크에서 접속 가능합니다.

   * URL을 통해 접속한 모습

     ![13]({{ site.url }}/img/2018-11-02-vue-pwa-init/13.png)

   * 모바일 환경에서 바로가기를 생성

     ![14]({{ site.url }}/img/2018-11-02-vue-pwa-init/14.png)

   * 생성된 모바일 바로가기

     ![15]({{ site.url }}/img/2018-11-02-vue-pwa-init/15.png)

   * 로딩화면

     ![16]({{ site.url }}/img/2018-11-02-vue-pwa-init/16.png)

   * 메인 화면 구동 모습

     ![17]({{ site.url }}/img/2018-11-02-vue-pwa-init/17.png)

   * 메인 화면 구동 모습 2

     ![18]({{ site.url }}/img/2018-11-02-vue-pwa-init/18.png)