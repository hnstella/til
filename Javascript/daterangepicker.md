# daterangepicker

[daterangepicker](https://www.daterangepicker.com/)

## daterangepicker single, multi 사용

- text 입력도 허용하기 때문에 값을 지우는 경우, 변경하는 경우에 대한 처리 필요했음(input 값 제거해도 blur되면 picker 값이 설정됐었음)
- autoUpdateInput: false 하고 키보드 및 picker event에 대해 각각 처리
- 참고 [datepicker don't allowing empty values](https://github.com/dangrossman/daterangepicker/issues/771)

```javascript
function fn_datepicker(obj, options) {
  let m_options = $.extend(
    {},
    {
      format: 'YYYY-MM-DD',
      mode: 'single',
      addTodayBtn: true,
      isToday: false,
    },
    options
  );

  var single_options = {
    singleDatePicker: true,
    showDropdowns: true,
    autoUpdateInput: false, // 달력 선택시 자동으로 input 값 업데이트 해주는 기능 off
    locale: {
      format: m_options.format,
      separator: ' - ',
      applyLabel: '적용',
      cancelLabel: 'Clear',
      fromLabel: 'From',
      toLabel: 'To',
      weekLabel: 'W',
      daysOfWeek: ['일', '월', '화', '수', '목', '금', '토'],
      monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'],
      firstDay: 1,
    },
  };

  var multi_options = {
    showDropdowns: true,
    maxDate: moment().add(1, 'years'), // 최대 1년 선택 가능
    autoUpdateInput: false,
    locale: {
      format: m_options.format,
      separator: ' ~ ',
      applyLabel: '적용',
      cancelLabel: 'Clear',
      fromLabel: 'From',
      toLabel: 'To',
      weekLabel: 'W',
      daysOfWeek: ['일', '월', '화', '수', '목', '금', '토'],
      monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'],
      firstDay: 1,
    },
    applyButtonClasses: 'btn-info',
    cancelClass: 'btn-outline-secondary',
    autoApply: true, // true인 경우 적용, clear 버튼 표시하지 않음
  };

  if (m_options.addTodayBtn) {
    single_options.ranges = {
      오늘: [moment(), moment()],
    };
  }

  if (m_options.mode === 'single') {
    obj.daterangepicker(single_options, function (start, end, label) {
      obj.data('drp_empty', false); // means value was SET
    });

    obj.data('drp_empty', false); // 처음 로드되었을 때 data 값이 설정 안되기 때문에 강제로 해줌

    // 달력 날짜를 선택했을 때 input에 값 저장
    obj.on('apply.daterangepicker', function (ev, picker) {
      obj.val(picker.startDate.format(m_options.format));
    });
    obj.on('change input keyup', function () {
      if (!obj.val()) {
        obj.data('drp_empty', true);
        obj.val('');
      }
    });
    obj.on('blur', function () {
      // input 값 입력이 끝난 후 empty 여부 체크
      if (obj.data('drp_empty')) {
        obj.val('');
      }
    });
  } else {
    if (fn_isEmpty(m_options.startDate) || fn_isEmpty(m_options.endDate)) {
      fn_warn('datepicker multi mode에서는 startDate, endDate에 Object를 넣어야합니다.');
      fn_warn('참조 : http://localhost:8080/view/guide/sample/sample-searchgrid');
      fn_warn(
        "Sample Javascript Code : var options = { mode : 'multi' ,startDate: $('#date4Start'), endDate : $('#date4End')}"
      );
      fn_warn(
        'HTML 코드' +
          '\n' +
          '<div class="form-group row row-item4">' +
          '\n' +
          '<label class="col-form-label">기간선택</label>' +
          '\n' +
          '<input type="hidden" id="date4Start" name="date4Start">' +
          '\n' +
          '<input type="hidden" id="date4End" name="date4End">' +
          '<input type="text" id="date4" name="date4" class="form-control form-control-sm datepicker">' +
          '\n' +
          '  <div class="input-group-append btn-datepicker">' +
          '\n' +
          '<span class="input-group-text btn-trigger"> <span class="ti-calendar"></span></span>' +
          '\n' +
          '</div>' +
          '\n' +
          '</div>'
      );
    } else {
      obj.daterangepicker(multi_options, function (start, end, label) {
        obj.data('drp_empty', false); // means value was SET
      });

      obj.data('drp_empty', false); // 처음 로드되었을 때 data 값이 설정 안되기 때문에 강제로 해줌

      // 키보드 날짜 입력 처리
      obj.on('change input keyup', function (ev, picker) {
        if (!obj.val()) {
          obj.data('drp_empty', true);
          obj.val('');
          m_options.startDate.val('');
          m_options.endDate.val('');
        } else {
          var drp = obj.data('daterangepicker');
          m_options.startDate.val(drp.startDate.format(m_options.format));
          m_options.endDate.val(drp.endDate.format(m_options.format));
        }
      });
      obj.on('blur', function () {
        // input 값 입력이 끝난 후 empty 여부 체크
        if (obj.data('drp_empty')) {
          obj.val('');
        }
      });

      // 달력 날짜를 선택했을 때 input 및 hidden value에 값 저장
      obj.on('apply.daterangepicker', function (ev, picker) {
        obj.val(picker.startDate.format(m_options.format) + ' ~ ' + picker.endDate.format(m_options.format));
        m_options.startDate.val(picker.startDate.format(m_options.format));
        m_options.endDate.val(picker.endDate.format(m_options.format));
      });

      // today 값 설정된 경우 초기 페이지 로딩 후 hidden값도 저장해야함
      if (m_options.isToday) {
        var drp = obj.data('daterangepicker');
        m_options.startDate.val(drp.startDate.format(m_options.format));
        m_options.endDate.val(drp.endDate.format(m_options.format));
      }
    }
  }

  if (!m_options.isToday) {
    obj.val('');
  }
}
```
