---
layout: post
title: Vue.js PWA 프론트앤드 개발 2
categories: [Development]
date: 2018-11-20 16:08 +0900
comments: true
---

1. iptime의 [ddns 기능](https://luvery93.github.io/articles/2017-09/change-router-to-iptime-a2003ns-mu)을 활용해 ngrok을 사용하지 않고 외부 접속이 가능하도록 설정합니다.

   * node.js를 통해 vue.js 프론트앤트 페이지를 띄울때 포트가 8080이므로 아래와 같이 설정합니다.

     ![1]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/1.png)

2. [졸업 프로젝트](https://github.com/narsimplyme/PrintAnywhere)의 프론트앤드단의 기본 UI/UX를 고려해 보았습니다.

   * 로그인 여부에 따라 사용자가 접근할 수 있는 페이지를 구분하고 기능에 따라 구분지었습니다.

     ![2]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/2.png)

   * 서비스 소개 페이지와 메인 페이지 : **HomeView.vue**

   * 로그인 페이지 : **SigninView.vue**

   * 회원가입 페이지 : **SignupView.vue**

   * 회원정보 수정 페이지 : **ProfileView.vue**

   * 포인트 페이지 : **PointView.vue**

   * 클라이언트(=> 졸업 프로젝트의 PA서비스 제공단) 페이지 : **ClientView.vue**

3. Vue.js Router 설정

   * 위 에서 작성한 vue 파일들을 URL을 통해 접근할 수 있도록 설정합니다.

     ![3]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/3.png)

   * src/router/index.js

     ```javascript
     import Vue from 'vue'
     import Router from 'vue-router'
     import HomeView from '@/components/HomeView'
     import SigninView from '@/components/SigninView'
     import SignupView from '@/components/SignupView'
     import ProfileView from '@/components/ProfileView'
     import PointView from '@/components/PointView'
     import ClientView from '@/components/ClientView'
     
     Vue.use(Router)
     
     export default new Router({
       routes: [
         {
           path: '/',
           name: 'home',
           component: HomeView
         },
         {
           path: '/signin',
           name: 'signin',
           component: SigninView
         },
         {
           path: '/signup',
           name: 'signup',
           component: SignupView
         },
         {
           path: '/profile',
           name: 'profile',
           component: ProfileView
         },
         {
           path: '/point',
           name: 'point',
           component: PointView
         },
         {
           path: '/client',
           name: 'client',
           component: ClientView
         }
       ]
     })
     ```

4. App.vue Navigation 설정

   * accessToken은 우선 쿠키를 이용해 저장합니다. 로그인 과정에서 항상 사용자가 인증되었다고 가정하고 토큰도 간단하게 생성해 저장합니다.

   * src/components/SigninView.vue

     ![4]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/4.png)

     * html 부분

     ```html
     <template>
       <main class="mdl-layout__content">
         <div class="mdl-card mdl-shadow--6dp">
           <div class="mdl-card__title">
             <h2 class="mdl-card__title-text">Welcome</h2>
           </div>
           <div class="mdl-card__supporting-text">
             <form @submit="onSignIn">
               <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
                 <input class="mdl-textfield__input" type="text" id="username" v-model="username" />
                 <label class="mdl-textfield__label" for="username">아이디</label>
               </div>
               <div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">
                 <input class="mdl-textfield__input" type="password" id="password" v-model="password" />
                 <label class="mdl-textfield__label" for="password">비밀번호</label>
               </div>
               <button type="submit" class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored mdl-js-ripple-effect">SignIn</button>
               <router-link to="/signup" class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect">SignUp</router-link>
             </form>
           </div>
         </div>
       </main>
     </template>
     ```

     * script 부분

     ```javascript
     <script>
     export default {
       name: 'singin',
       data () {
         return {
           username: '',
           password: ''
         }
       },
       methods: {
         onSignIn () {
           if (this.username === '' || this.password === '') {
             return
           }
           // TODO api/auth/signin [POST]
           document.cookie = `accessToken=${(this.username + this.password)}`
           this.$router.push('/')
           location.reload()
         }
     }
     </script>
     ```

   * accessToken을 이용해 항상 인증이 되었다고 가정을 하고 토큰의 존재 여부에 따라 Navagation에서 접근할 수 있는 페이지를 다르게 설정합니다. 로그아웃을 했을 경우 token 값을 비워줍니다. *.vue 파일이 마운트되기 전에 인증을 나타내는 변수 auth를 계산하여 router-link를 다르게 렌더링합니다.

   * scr/App.vue

     ![5]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/5.png)

     ![6]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/6.png)

     * html 부분

     ```html
     <template>
       <div class="mdl-layout mdl-js-layout mdl-layout--fixed-header">
         <header class="mdl-layout__header">
           <div class="mdl-layout__header-row">
             <span class="mdl-layout-title">프린트애니웨어</span>
           </div>
         </header>
         <div class="mdl-layout__drawer">
           <span class="mdl-layout-title">프린트애니웨어</span>
           <nav class="mdl-navigation" v-if="auth">
             <router-link class="mdl-navigation__link" to="/" @click.native="hideMenu" replace>Home</router-link>
             <router-link class="mdl-navigation__link" to="/profile" @click.native="hideMenu" replace>Profile</router-link>
             <router-link class="mdl-navigation__link" to="/point" @click.native="hideMenu" replace>Point</router-link>
             <router-link class="mdl-navigation__link" to="/client" @click.native="hideMenu" replace>Client</router-link>
             <router-link class="mdl-navigation__link"  to="/" @click.native="unAuth" replace>Logout</router-link>
           </nav>
           <nav class="mdl-navigation" v-else>
             <router-link class="mdl-navigation__link" to="/" @click.native="hideMenu" replace>Home</router-link>
             <router-link class="mdl-navigation__link" to="/signin" @click.native="hideMenu" replace>SignIn</router-link>
             <router-link class="mdl-navigation__link" to="/signup" @click.native="hideMenu" replace>SignUp</router-link>
           </nav>
         </div>
         <main class="mdl-layout__content">
           <div class="page-content">
           <router-view></router-view>
           </div>
         </main>
       </div>
     </template>
     ```

     * script 부분

     ```javascript
     <script>
     require('material-design-lite')
     export default {
       name: 'app',
       data () {
         return {
           auth: false
         }
       },
       beforeMount () {
         this.setAuth()
       },
       methods: {
         hideMenu: function () {
           document.getElementsByClassName('mdl-layout__drawer')[0].classList.remove('is-visible')
           document.getElementsByClassName('mdl-layout__obfuscator')[0].classList.remove('is-visible')
           location.reload()
         },
         unAuth: function () {
           document.cookie = `accessToken=`
           document.getElementsByClassName('mdl-layout__drawer')[0].classList.remove('is-visible')
           document.getElementsByClassName('mdl-layout__obfuscator')[0].classList.remove('is-visible')
           location.reload()
         },
         setAuth: function () {
           var value = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')
           if (value[2] === '') {
             this.auth = false
           } else {
             this.auth = true
           }
         }
       }
     }
     </script>
     ```

5. ListView.vue v-for 임시 데이터로 렌더링 설정

   * 임시데이터를 생성하여 리스트뷰를 구현합니다.

   * src/test/files.js

     ```json
     fileData: [
       {
         'fileId': 0,
         'fileName': 'Test File 1',
         'fileType': 'pdf',
         'fileSize': 1000,
         'fileUploadDate': '2018-11-18 10:40:22',
         'isReserved': false
       },
       {
         'fileId': 1,
         'fileName': 'Test File 2',
         'fileType': 'pdf',
         'fileSize': 1000,
         'fileUploadDate': '2018-11-18 09:22:33',
         'isReserved': true
       },
       {
         'fileId': 2,
         'fileName': 'Test File 3',
         'fileType': 'pdf',
         'fileSize': 1000,
         'fileUploadDate': '2018-11-18 09:12:45',
         'isReserved': true
       },
       {
         'fileId': 3,
         'fileName': 'Test File 4',
         'fileType': 'pdf',
         'fileSize': 1000,
         'fileUploadDate': '2018-11-18 15:33:22',
         'isReserved': false
       },
       {
         'fileId': 4,
         'fileName': 'Test File 5',
         'fileType': 'pdf',
         'fileSize': 1000,
         'fileUploadDate': '2018-11-18 16:22:11',
         'isReserved': false
       }
     ]
     ```

   * 서버로부터 위 데이터를 받았다고 가정한뒤 바인딩하여 v-for 구문으로 나타냅니다.

   * src/components/homeView.vue

     ![7]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/7.png)

     * html 부분

       ```html
       <template>
         <div class="mdl-layout__content mdl-cell mdl-cell--12-col-desktop mdl-cell--8-col-tablet mdl-cell--4-col-phone">
           <div v-for="file in this.filelist" :key="file.id" v-bind:class="{'mdl-color--teal-100' : file.isReserved}" class="mdl-card mdl-cell mdl-cell--12-col-desktop mdl-cell--8-col-tablet mdl-cell--4-col-phone mdl-shadow--4dp">
             <div class="mdl-card__title">
               <h2 class=mdl-card__title-text v-text="file.fileName"></h2>
             </div>
             <div class="mdl-card__supporting-text file-info">
               <div>Size : <span v-text="file.fileSize"></span></div>
               <div>Uploaded : <span v-text="file.fileUploadDate"></span></div>
             </div>
             <div class="mdl-card__actions mdl-card--border">
               <button @click.native="onReserve(file.fileId)" v-if="file.isReserved" class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--colored">UnReserve</button>
               <button @click.native="onUnReserve(file.fileId)" v-else class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--colored">Reserve</button>
               <button @click.native="onDelete(file.fileId)" class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--accent">Delete</button>
             </div>
             <div class="mdl-card__menu">
               <i @click.native="onDownload(file.fileId)" class="material-icons">cloud_download</i>
             </div>
           </div>
         </div>
       </template>
       ```

     * script 부분

       ```javascript
       <script>
       import files from '../temp/files'
       require('material-design-lite')
       export default {
         name: 'home',
         data () {
           return {
             welcome: '님 환영합니다.',
             auth: false,
             'filelist': files.fileData
           }
         },
         methods: {
           setAuth () {
             var value = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')
             if (value[2] === '') {
               this.auth = false
             } else {
               this.auth = true
             }
           },
           onReserve (fileId) {
             // TODO api/files/{fileId} [PUT]
           },
           onUnReserve (fileId) {
             // TODO api/files/{fileId} [PUT]
           },
           onDelete (fileId) {
             // TODO api/files/{fileId} [DELETE]
           },
         },
         beforeMount () {
           this.setAuth()
         }
       }
       </script>
       ```

6. 이후 작업을 위해 axios를 설치해둡니다.

   ```
   npm install axios
   ```

   ![8]({{ site.url }}/img/2018-11-20-vue-pwa-mockup/8.png)
