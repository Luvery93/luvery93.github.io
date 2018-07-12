---
layout: post
title: "Jekyll Theme 적용"
date:	2017-07-14 15:36:00 +0900
categories: [Blog]
comments: true
---

1. 변경하고자 하는 Jekyll Theme 소스를 가져온다. 여기에서는 [renyuanz/leonids](https://github.com/renyuanz/leonids/)소스를 가져온다.

   ```g
   git clone https://github.com/renyuanz/leonids.git
   ```

2. Theme에 posting 하기 전 테마 디렉토리 구조를 살펴본다.

   ```
   |-- _drafts
   	|-- 2011-03-10-sample-post.md
   	|-- 2012-05-22-readability-post.md
   	|-- 2013-05-23-readability-feature-post.md
   	|-- 2013-08-12-sample-link-post.md
   	|-- 2013-08-16-code-highlighting-post.md
   	|-- 2015-08-18-welcome-to-jekyll.md
   |-- _includes
   	|-- disuqs.html
   	|-- footer.html
   	|-- head.html
   	|-- js.html
   	|-- nav.html
   	|-- read_time.html
   	|-- sidebar.html
   	|-- social-links.html
   |-- _layouts
   	|-- default.html
   	|-- page.html
   	|-- post.html
   	|-- post_listing.html
   |-- _posts
   	|-- 2011-03-10-sample-post.md
   	|-- 2012-05-22-readability-post.md
   	|-- 2013-05-23-readability-feature-post.md
   	|-- 2013-08-12-sample-link-post.md
   	|-- 2013-08-16-code-highlighting-post.md
   	|-- 2015-08-18-welcome-to-jekyll.md
   |-- _saas
   	|-- components
   		|-- _buttons.scss
   		|-- _global.scss
   		|-- _grid.scss
   		|-- _helpers.scss
   		|-- _mixins.scss
   		|-- _nomalize.scss
   		|-- _syntax-highlighting.scss
   		|-- _typography.scss
   		|-- _variables.scss
   	|-- pages
   		|-- _archive.scss
   		|-- _layout.scss
   		|-- _post.scss
   		|-- _tags.scss
   |-- categories
   	|-- index.html
   |-- css
   	|-- font-awesome.min.css
   	|-- main.scss
   |-- fonts
   	|-- FontAwesome.otf
   	|-- fontawesome-webfont.eot
   	|-- fontawesome-webfont.svg
   	|-- fontawesome-webfont.ttf
   	|-- fontawesome-webfont.woff
   	|-- fontawesome-webfont.woff2
   |-- img
   	|-- avatar.jpg
   	|-- leonids-logo.png
   |-- js
   	|-- jquery-2.1.4.min.js
   	|-- main.js
   |-- .gitignore
   |-- _config.yml
   |-- archive.html
   |-- favicon.ico
   |-- favicon.png
   |-- feed.xml
   |-- index.html
   |-- LICENSE.txt
   |-- README.md
   |-- tags.html
   ```

3. 디렉토리 정리 및 첫 빌드

   * _posts 의 예제 md 파일을 지우고 _config.yml을 적절하게 수정합니다.

4. posting할 MD 파일을 _post에 작성하고 build, serve 합니다.

   ​