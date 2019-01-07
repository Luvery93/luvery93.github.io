---
layout: post
title: Vue.js PWA 프론트앤드 개발 3
categories: [Development]
date: 2019-01-07 21:48 +0900
comments: true
---

1. 개요
   * 프론트단 목업 개발이 완료되었기에 이어서 서버 연동을 기능별로 개발합니다.
   * 각 필드별로 model을 바인딩하여 aixos를 통해 서버와 연동합니다. Server가 Vue.js를 실행하는 도메인과 다를 경우에 크로스도메인이슈를 고려해야 하며, axios는 기본적으로 JSON type이므로 헤더도 고려해야 했습니다. 
   * 당시 작성한 코드 원본은 [깃허브](https://github.com/narsimplyme/PrintAnywhere/tree/master/Src/Client/printanywhere-client)를 통해 확인할 수 있으며, 이 글에서는 서버와 통신 부분의 내용을 작성합니다.

2. 회원가입

   * 회원가입은 사용자 입력에 따른 새로운 사용자 정보를 서버로 **onSignUp[POST]** 하는 과정입니다. 로그인 이전에 사용자 입력정보가 올바른지 클라이언트 단에서 검증한 뒤 서버에서 검증하는 것이 컴퓨팅 자원을 불필요하게 낭비하지 않는다고 생각하여 과정을 추가하였습니다. 

   * 웹토큰의 경우 vuex를 이용해 저장하는 것을 계획하였으나 우선 웹 쿠키에 저장하는 방식으로 진행합니다. 웹토큰이 현재 브라우저 쿠키에 존재하는지에 따라 사용자 인증 여부를 체크하는 **setAuth[GET]**를 실행하도록 하였습니다. 

   * vue에서 화면에 객체가 마운트되기 전 beforeMount의 함수를 실행한다고 되어있어서 아래와 같이 작성하였는데, 화면에 DOM객체가 다른 화면에서도 마찬가지로 깜빡이 듯이 보이는 것을 제대로 처리하지 못하였습니다. 인증 여부에 따라 DOM객체를 동적으로 생성해서 SPA의 방향으로 작성한다면 더 나은 경험을 만들 수 있을 것 같습니다.

   * Script 부분

     ```javascript
     <script>
     import axios from 'axios'
     export default {
     // 중략...
       methods: {
         onSignUp () {
           if (this.username === '' || this.password === '' || this.passwordConfirm === '' || this.name === '' || this.nickName === '' || this.phone === '' || this.email === '') {
             return
           }
           if (this.onCheckPassword() === false) {
             return
           }
           axios.post('{serverIP}/signUp', {
             'userId': this.username,
             'userPw': this.password,
             'userName': this.name,
             'userMail': this.email,
             'userNickname': this.nickName,
             'userPhoneNumber': this.phone
           },
           {
             headers: {
               'Content-Type': 'application/json'
             }
           }
           ).then(response => {
             document.cookie = `accessToken=${(response.data.data.token)}`
             this.$router.push('/')
             location.reload()
           }).catch(errors => {
     
           })
         },
         setAuth () {
           var token = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')[2]
           if (token === '') {
             this.auth = false
             return
           }
           axios.get('{serverIP}/authMe', {
             headers: {
               'x-access-token': token
             }
           }).then(response => {
             if (response.data.success === true) {
               this.auth = true
               this.$router.push('/')
               location.reload()
             }
           }).catch(errors => {
             this.auth = false
           })
         }
       },
       beforeMount () {
         this.setAuth()
       }
     }
     </script>
     ```

3. 파일업로드

   * 홈 화면에서 사용자가 파일을 선택하고 업로드 하는 부분을 작성했습니다. 자바스크립트로 업로드 하기 전 다 수의 파일 목록을 관리하고 한 번에 업로드하는 방식으로 작성했습니다.

   * 파일을 업로드 하는 것은 multiple form data를 보내는 f**ileUpload[POST]** 요청이기에 서버에서 해당 헤더를 허용해야 하고 위와 같은 이유로 크로스도메인도 생각해야 합니다. 

   * 드래그 앤 드롭과 진행바를 추가했다면 더 나은 경험을 제공할 수 있었을 것입니다.

   * HTML 부분

     ```html
         <div class="mdl-card mdl-cell mdl-cell--12-col-desktop mdl-cell--8-col-tablet mdl-cell--4-col-phone mdl-shadow--4dp">
           <div class="mdl-card__supporting-text uploadFile-listing">
             <div class="mdl-cell mdl-cell--12-col-desktop mdl-cell--8-col-tablet mdl-cell--4-col-phone">
               <div v-for="(uploadFile, index) in this.uploadFileslist" :key="index" class="mdl-cell mdl-cell--12-col-desktop mdl-cell--8-col-tablet mdl-cell--4-col-phone">
                 <button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--accent" v-on:click="onRemoveFile( index )">취소</button>&nbsp;&nbsp;&nbsp;&nbsp;<span>{{ uploadFile.name }}</span>
               </div>
             </div>
           </div>
           <div class="mdl-card__actions mdl-card--border">
             <label class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--colored" :disabled="this.fileUploadProgress == true" >
               업로드할 파일 선택
               <input type="file" ref="uploadFileInput" multiple v-on:change="onFileUpload()" />
             </label>
             &nbsp;&nbsp;&nbsp;&nbsp;
             <button v-on:click="onSubmitFiles()" :disabled="this.fileUploadProgress == true" class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect mdl-button--accent">파일 업로드</button>
           </div>
         </div>
     ```

   * Script 부분

     ```javascript
     <script>
     import axios from 'axios'
     export default {
       data: {
         return {
           uploadFileList: [],
           // 중략...
         }
       }
       methods: {
         // 중략...
         onSubmitFiles () {
           var token = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')[2]
           let uploadFile = new FormData()
           for (var i = 0; i < this.uploadFileslist.length; i++) {
             uploadFile.append('uploadFile', this.uploadFileslist[i])
           }
           this.fileUploadProgress = true
           axios.post('{serverIP}/fileUpload', uploadFile, {
             headers: {
               'x-access-token': token
             }
           }).then(response => {
             this.uploadFileslist = []
             this.fileUploadProgress = false
             alert('파일이 업로드되었습니다.')
           }).catch(errors => {
     
           })
         },
         onFileUpload () {
           let uploadedFiles = this.$refs.uploadFileInput.files
           for (var i = 0; i < uploadedFiles.length; i++) {
             this.uploadFileslist.push(uploadedFiles[i])
           }
         },
         onRemoveFile (index) {
           this.uploadFileslist.splice(index, 1)
         },
         // 중략...
     }
     </script>
     ```

4. 파일 조회

   * 업로드 된 파일은 바로 업로드 화면에서 조회할 수 있도록 하였습니다.

   * 화면을 처음 조회할 때와 파일 업로드를 마친 뒤 다시 실행되도록 하였습니다.

   * 예약된 파일은 reserved라는 값을 추가로 지니도록 하였습니다.

   * Script 부분

     ```javascript
     <script>
     import axios from 'axios'
     export default {
       data () {
         return {
           filelist: [],
         }
       },
       methods: {
         onGetFileList () {
           var token = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')[2]
           axios.get('{serverIP}/fileList', {
             headers: {
               'x-access-token': token
             }
           }).then(response => {
             this.filelist = response.data.data.fileList
           }).catch(errors => {
     
           })
         },
         onGetReservedFile () {
           var token = document.cookie.match('(^|;) ?' + 'accessToken' + '=([^;]*)(;|$)')[2]
           axios.get('{serverIP}/selectReserveList', {
             headers: {
               'x-access-token': token
             }
           }).then(response => {
             for (var i = 0; response.data.data.reserveList.length; i++) {
               let file = this.filelist.find(f => f.fileId === response.data.data.reserveList[i].fileId)
               file.isReserved = true
               file.reserveId = response.data.data.reserveList[i].reserveId
             }
           }).catch(errors => {
     
           })
         },
       }
       // 중략...
     }
     </script>
     ```

      

5. 파일 다운로드

   * 파일다운로드는 파일 목록 조회에서 아이콘을 통해 다운받을 수 있도록 하였습니다.

   * Script 부분

     ```javascript
     <script>
     import axios from 'axios'
     export default {    
       methods: {
         onFileDonwload (url, fileName) {
           axios.get(url, {
             responseType: 'blob'
           }).then(response => {
             let link = document.createElement('a')
             link.href = window.URL.createObjectURL(new Blob([response.data]))
             link.setAttribute('download', fileName)
             document.body.appendChild(link)
             link.click()
             link.remove()
             window.URL.revokeObjectURL(url)
           })
         }
       // 중략...
       }
     }
     </script>
     ```

6. 기타

   * 그 외에도 'vue2-datepicker', 'vue2-datepicker', 그리고 'vue-browser-geolocation' 등의 컴포넌트를 이용하여 뷰단을 쉽게 구축할 수 있었습니다.