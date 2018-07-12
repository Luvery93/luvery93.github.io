---
layout: post
title:	"Jekyll 초기 설정"
date:	2017-07-14 15:35:00 +0900
categories: [Blog]
comments: true
---

* [Jekyll](https://jekyllrb-ko.github.io/) 홈페이지에서 Windows를 공식지원하지 않고 있어서 [Windows 에서 Jekyll 실행](http://jekyll-windows.juthilo.com/)의 문서를 참고해서 설치를 진행하도록 합니다.

1. Ruby 와 Ruby DevKit을 설치합니다.

   * [Windows 버전 Ruby 설치](https://rubyinstaller.org/downloads/)는 v2.0.0를 추천하고 있으나, 최신버전 v2.4.x로 테스트를 진행해봅니다. (07/12/17 기준)


   * Ruby 2.4.0 그리고 그 이상 버전에서는 Ruby Devkit이 설치 이후에 자동으로 진행됩니다. 1, 2, 3 순서대로 설치를 진행합니다.

2. Jekyll 를 설치합니다.

   * CMD 창에서 아래를 입력합니다.

   ```
   > gem install jekyll
   ```

3. syntax highlighter를 위해 Rouge를 설치합니다. ( 필수 아님 )

   * CMD 창에서 아래를 입력합니다.

   ```
   > gem install rouge
   ```

4. syntax highlighting를 위해 pygments을 설치합니다. ( 필수 아님 )

   * 파이썬 3 버전으로는 작동을 하지않는다고 하니, 파이썬 2 버전을 설치합니다.
   * 이미 로컬에 파이썬 3 버전이 설치되어 있는 관계로 파이썬 2 버전 설치 후 환경 변수 설정을 해줍니다.

   ```
   C:\Develop\python36\Scripts;C:\Delvelop\python27\Scripts;
   ```

   * 파이썬2를 통해 pygments를 설치합니다.
   * CMD 창에 아래를 입력합니다.

   ```
   > pip2 install Pygments
   ```

5. wdm을 설치합니다.

   * CMD 창에서 아래를 입력합니다.

   ```
   > gem install wdm
   ```

6. bundler 를 설치합니다.

   * CMD 창에서 아래를 입력합니다.

   ```
   > gem install bundler
   ```

7. 로컬 프로젝트 경로를 생성하고 그 아래 jekyll 프로젝트를 생성합니다.

   * CMD 창에서 아래를 입력합니다.

   ```
   > mkdir luvery93.github.io
   > cd luvery93.github.io
   > jekyll new .
   ```

8. 로컬 프로젝트 빌드 및 실행

   * CMD 창에서 아래를 입력합니다.

   ```
   > jekyll build [--watch | -w]
   > jekyll serve [--watch | -w]
   ```