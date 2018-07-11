# 부트스트랩 캘린더 일주일 기간 선택하기
datetimePicker 선택 시 강제로 월-일 선택되도록 하기

```html
<div class='input-group date' id='startDatetimePicker'>
    <input type="text" id="startDate1" name="startDate1" class="form-control" th:value="${startDate1}" />
    <span class="input-group-addon"><span class="glyphicon glyphicon-calendar"></span></span>
</div>

```

```javascript
var val = $('#startDate1').val();
var firstDate = moment(val, 'YYYY-MM-DD').day(1).format('YYYY-MM-DD');
var lastDate = moment(val, 'YYYY-MM-DD').day(7).format('YYYY-MM-DD');
console.log('first date : ' + firstDate);
console.log('last date : ' + lastDate);
$('#startDate1').val(firstDate);
$('#endDate1').val(lastDate);
```

아래 링크 참조함

- [Bootstrap datepicker: Select entire week and put week interval in input field](https://stackoverflow.com/questions/28713964/bootstrap-datepicker-select-entire-week-and-put-week-interval-in-input-field/34129546)
- 일~토 선택인 경우 예제처럼 css 적용해서 캘린더에 hover 스타일 적용을 하면 좋겠다.
```css
.bootstrap-datetimepicker-widget .datepicker-days table tbody tr:hover {
    background-color: #eee;
}
```