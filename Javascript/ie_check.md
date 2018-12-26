# IE 버전 체크

## IE 버전 가져오기

```javascript
function get_version_of_IE () { 
	 var word; 
	 var agent = navigator.userAgent.toLowerCase(); 

	 // IE old version ( IE 10 or Lower ) 
	 if ( navigator.appName == "Microsoft Internet Explorer" ) word = "msie "; 
	 // IE 11 
	 else if ( agent.search( "trident" ) > -1 ) word = "trident/.*rv:"; 
	 // Microsoft Edge  
	 else if ( agent.search( "edge/" ) > -1 ) word = "edge/"; 
	 // 그외, IE가 아니라면 ( If it's not IE or Edge )  
	 else return -1; 

	 var reg = new RegExp( word + "([0-9]{1,})(\\.{0,}[0-9]{0,1})" ); 

	 if (  reg.exec( agent ) != null  ) return parseFloat( RegExp.$1 + RegExp.$2 ); 

	 return -1; 
} 
```

## 함수 사용

```html
<button onclick="checkVersion()"> 클릭하세요 </button>
<p id="demo1"></p>
<p id="demo2"></p>

<script type="text/javascript">
function checkVersion () { 
	 var verNumber = get_version_of_IE(); 
	 demo1.innerHTML = verNumber; 
	 if ( verNumber == -1 ){ 
		demo2.innerHTML = "인터넷 익스플로러가 아닌, 다른 브라우저를 사용중이십니다."; 
	 } 
	 else { 
		 demo2.innerHTML = "인터넷 익스플로러 또는 엣지 브라우저를 사용중이십니다."; 
	 } 
} 
</script>
```

## LINK
[IE 버전 체크용 자바스크립트 함수](https://tonks.tistory.com/107)