---
layout: post
title: "TextBox에 숫자만 입력되도록 하는 스크립트"
date: 2018-02-05 16:59 +0900
categories: [Development]
comments: true
---

* Textbox에 숫자만 입력하는 스크립트와 적용 예시입니다.
* Keycode는 [여기](http://www.foreui.com/articles/Key_Code_Table.htm)에서 확인할 수 있습니다.

```html
<input type="number" onkeydown"return $.numberFilterKeyDown(event)" onkeyup="$.numberFIlterKeyUp(event)" />
```

```javascript
<script>
  $(function () {
  	$.numberFilterKeyDown = function(event) {
      	event = event || window.event
    	var code = (event.which) ? event.which : event.KeyCode;
      	if( (code > 47 && code <58) || (code > 95 && code < 106) ||
           code === 8 || code === 9 || code === 13 || code === 16 ||
           code === 35 || code === 36 || code === 37 || code === 38 ||
           code === 39 || code === 40 || code === 46 ) {
        	return;     
        }
      	return false;
	}
    $.numberFilterKeyUp = function (event) {
      	event = event || window.event;
        var code = (event.which) ? event.which : event.KeyCode;
      	if( code === 9 || code === 16 || code === 35 || code === 36 ||
          code === 37 || code === 38 || code === 39 || code === 40){
        	return;  
        } else if ( (code > 47 && code <58) || (code > 95 && code < 106) ||
          code === 8 || code === 13 || code === 46 ) {
        	// 숫자 변동 시 처리 함수
          	return;
        } else {
          	var target = event.target || window.event.srcElement;
          	target.value = target.value.replace(/[^0-9]/g, "");
        }
    }
  })
</script>
```

