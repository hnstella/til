# jQuery

## window.onload() / jQuery $(document).ready()

onload 함수는 웹페이지 로딩이 끝나는 시점에 수행
- 이미지나 파일까지 모두 로드될 때까지 기다리기 때문에 불필요한 로딩시간이 길어진다.
- 동일한 페이지 내 onload 함수는 하나만 존재해야 한다.

jQuery의 ready 함수는 브라우저가 DOM 트리를 생성한 직후 실행한다. 따라서 이미지나 파일 로딩까지 기다리지 않고 빠르게 웹페이지 기능을 수행할 수 있다.
```javascript
<script type="text/javascript" src="http://code.jquery.com/jquery-1.4.4.min.js"></script>
<script type="text/javascript">
window.onload = function() { alert("첫번째 window.onload"); };
window.onload = function() { alert("두번째 window.onload"); };
$(document).ready(function() { alert("첫번째 ready()"); });
$(document).ready(function() { alert("두번째 ready()"); });
</script>
```
실행 순서 : 첫번째 ready() -> 두번째 ready() -> 두번째 window.download
첫번째 window.onload는 실행되지 않는다.
