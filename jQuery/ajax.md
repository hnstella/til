# ajax

사용법
```javascript
$.ajax({
    url : '/list_ajax.jsp',
    type : 'GET',
    dataType : 'html',
    // data : {content : $("input[name=content]").val()},
    //data : $("form").serialize(),
    success : function(data) {
        $("table").html(data);
    }
});
```
```javascript
$.ajax({
    url : '/insert_ajax.jsp',
    type : 'POST',
    dataType : 'html',
    // data : {content : $("input[name=content]").val()},
    data : $("form").serialize(),
    success : function(data) {
        $("table").html(data);
    }
});
```