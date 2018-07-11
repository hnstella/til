# 문자열 공백 제거


## trim()
양 옆의 공백만 제거될 뿐 중간 공백은 제거되지 않는다.

```html
<input type="text" id="trimText" value="       공백입니다."/>
<input type="button" id="trimButton" value="trim"/>
```

``` javascript
    $(function () {
        $("#trimButton").click(function() {
            var txt = $("#trimText").val();
            //console.log("before : (" + txt + ")");
            txt = $.trim(txt);
            //console.log("after : (" + txt + ")");
            $("#trimText").val(txt);
        })
    })
```


# 특정 영역 제거
## empty()
```javascript
$(function() {
    $("#button").click(function() {
        // 영역 비우기 = empty()
        $("#element").empty();
    })
});
```

## remove()
```javascript
$(function() {
    $("#button").click(function() {
        // 레이어 삭제 함수 = remove()
        $("#element").remove();
    })
});
```