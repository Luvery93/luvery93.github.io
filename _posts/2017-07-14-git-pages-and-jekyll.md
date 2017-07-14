---
layout: post
title: "Git pages and Jekyll 연동"
date:	2017-07-14 18:06 +0900
categories: [Jekyll]
comment: true
---

1. Github에 git pages를 위해 repository를 생성합니다.

   * repository 이름은 {username}.github.io 형식이어야 합니다.

   ```
   https://github.com/Luvery93/luvery93.github.io.git
   ```

2. 위에서 생성한 repository에 Jekyll project를 push 합니다.

   * Git이 설치되어 있지 않을 경우 [여기](https://git-scm.com/)에서 Git을 설치합니다.
   * CMD 창에서 아래를 입력합니다.

   ```
   $ git clone https://github.com/Luvery93/luvery93.github.io.git
   $ cd luvery93.github.io
   $ git add .
   $ git commit -m "2017-07-14 post"
   $ git push origin master
   ```