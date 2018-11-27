# datepicker 사용하기

## 준비

- jquery
- jquery-ui [다운로드](http://jqueryui.com/download/all/)
- 한글화 파일 [링크](https://github.com/jquery/jquery-ui/blob/master/ui/i18n/datepicker-ko.js)

## 사용법

- 날짜 선택 시 특정 element에 값 입력하기

```javascript
$(function() {
  $('#dueDate').datepicker({
    dateFormat: 'yy-mm-dd',
    onSelect: function(d) {
      $('#duDate').text(d);
    }
  });
});
```

- 클릭하면 달력 팝업 뜨기

```javascript
<input id="dueDate" name="dueDate" type="text" class="form-control">
  <span class="input-group-addon cursor" onclick="$('#dueDate').datepicker('show');">
  <i class="far fa-calendar-alt"></i>
</span>

```

### 참고

- [jquery api](http://api.jqueryui.com/datepicker/)
- [jQuery UI datepicker - 자바스크립트 달력 사용하기](https://offbyone.tistory.com/230)
