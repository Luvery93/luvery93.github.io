---
layout: post
title: "Jekyll 빌드 오류 - tzinfo 종속성"
date: 2017-08-14 17:06 +09:00
categories: [Blog]
comments: true
---

1. **Jekyll Build** 입력시 에러가 발생함을 확인했습니다.

   ![1]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/1.png)

2. **tzinfo**가 없기 떄문에 발생한 오류이므로 **tzinfo**를 설치합니다.

   ```
   gem install tzifo
   ```

   ![2]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/2.png)

3. **tzinfo** 설치 이후 **Jekyll Build** 입력을 하여도 오류가 발생합니다.

   ![3]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/3.png)

4. **tzinfo-data**가 없기 떄문에 발생한 오류이므로 **tzinfo-data**를 설치합니다

   ```
   gem install tzinfo-data
   ```

   ![4]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/4.png)

5. **tzinfo-data** 설치 이후 정상 작동하는 모습을 확인할 수 있습니다.

   ![5]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/5.png)

   ![6]({{ site.url }}/img/2017-08-14-Jekyll-Build-error-tzinfo-dependency/6.png)