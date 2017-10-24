---
layout: post
title: "Git History 되돌려서 Commit 정리하기"
date: 2017-10-24 16:54:00 +0900
categories: [Jekyll]
comments: true
---

* 이미 push 된 commit을 되돌리고 수정된 git history를 작성하여 관리하려면 다음과 같은 과정을 진행합니다.

  1. 현재 git history를 1단계 전으로 강제로 되돌립니다. 단, 이 커맨드를 입력하기 전에 작업해둔 파일이 있다면 git repository 외의 공간에 백업해둡니다.

     ```
     git reset --hard HEAD~1
     ```

  2. 수정해야 될 사항을 수정하고 일반적인 commit 과정을 거치되 github에 push할 떄 강제로 덮어쓰기 합니다.

     ```
     git add .
     git commit "..."
     git push origin +master
     ```