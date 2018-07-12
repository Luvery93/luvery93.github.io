---
layout:	post
title:	"Jekyll에 disqus 연동하여 댓글 시스템 구축"
date:	2017-07-18 11:22 +0900
categories: [Blog]
comments: true
---

1. Disqus

   * Jekyll은 정적 웹사이트이기 때문에 댓글과 같은 동적인 요소를 자체적으로 삽입할 수 없습니다. 따라서 댓글을 포스트마다 붙여주고 마이그레이션까지 가능한 [disqus](https://disqus.com/)를 도입합니다.
     1. disqus에 회원가입 하고 난 뒤 GET STARTED, I want to install Disqus on my site 를 순서대로 선택합니다.
     2. Create a new site 에서 필수 정보를 입력한 뒤 Create site 버튼을 누릅니다.
        *  Site Owner : 페이지 관리자(자신 계정)
        *  Website Name : 웹 사이트 이름
        *  Website URL : 웹 사이트 URL
        *  Category : 카테고리
        *  Language : 언어
   * 현재 사용중인 renyuanz/lenodis Jekyll 테마는 기본 레이아웃에 disqus 가 포함되어 있으므로 _config.yml 파일에서 disqus_shortname만 설정하면 됩니다. disqus-shortname은 DISQUS Settings - ORGANIZATION Sites - Site Settings - Shortname에 있습니다.

   ```
   disqus-shortname: {개별 disqus shortname}
   ```

   * disqus 관련 레이아웃 파일은 아래와 같습니다.
   * _config.yml 변수는 site.owner.disqus-shortname 형식으로 호출합니다.

   ```javascript
   <script type="text/javascript">
   	var disqus_shortname = '{_config.yml의 disqus-shortname}';
   	(function () {
   		var dsq = document.createElement('script');
   		dsq.type = 'text/javascript';
   		dsq.async = true;
   		dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
   		(document.getElementByTagName('haed')[0]
   		|| document.getElementByTagName('body')[0]).appendChild(dsq);
   	})();
   </script>
   ```

