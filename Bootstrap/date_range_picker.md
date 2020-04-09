# Date Range Picker

- [Date Range Picker Options](https://www.daterangepicker.com/#options)

```javascript
$('.date-picker').daterangepicker({
  singleDatePicker: true,
  showDropdowns: true,
  locale: {
    format: 'YYYY/MM/DD',
    separator: ' - ',
    applyLabel: '적용',
    cancelLabel: '취소',
    fromLabel: 'From',
    toLabel: 'To',
    weekLabel: 'W',
    daysOfWeek: ['일', '월', '화', '수', '목', '금', '토'],
    monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'],
    firstDay: 1
  }
});
```

```javascript
/* jquery Date Range Picker init - Single Use */
function fn_daterangepicker_single(obj, format, addTodayBtn) {
  var options = {
    singleDatePicker: true,
    showDropdowns: true,
    locale: {
      format: format,
      separator: ' - ',
      applyLabel: '적용',
      cancelLabel: '취소',
      fromLabel: 'From',
      toLabel: 'To',
      weekLabel: 'W',
      daysOfWeek: ['일', '월', '화', '수', '목', '금', '토'],
      monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'],
      firstDay: 1
    }
  };
  if (true === addTodayBtn) {
    options.ranges = {
      오늘: [moment(), moment()]
    };
  }
  obj.daterangepicker(options);
}

/* daterangepicker-multi */
function fn_daterangepicker_multi(obj, format, startDateObj, endDateObj) {
  var options = {
    showDropdowns: true,
    maxDate: moment().add(1, 'years'), // 최대 1년 선택 가능
    locale: {
      format: format,
      separator: ' ~ ',
      applyLabel: '적용',
      cancelLabel: '취소',
      fromLabel: 'From',
      toLabel: 'To',
      weekLabel: 'W',
      daysOfWeek: ['일', '월', '화', '수', '목', '금', '토'],
      monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'],
      firstDay: 1
    },
    autoApply: true
  };
  obj.daterangepicker(options, function(start, end) {
    startDateObj.val(start.format(format));
    endDateObj.val(end.format(format));
  });
}
```
