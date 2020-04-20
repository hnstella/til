# datepicker 사용하기

## 준비

- jquery
- jquery-ui [다운로드](http://jqueryui.com/download/all/)
- 한글화 파일 [링크](https://github.com/jquery/jquery-ui/blob/master/ui/i18n/datepicker-ko.js)
- [jquery-ui datepicker api](https://api.jqueryui.com/datepicker/)

## 사용법

- 날짜 선택 시 특정 element에 값 입력하기

```javascript
$(function () {
  $('#dueDate').datepicker({
    dateFormat: 'yy-mm-dd',
    onSelect: function (d) {
      $('#duDate').text(d);
    },
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

## 전체 datepicker 옵션 일괄 설정

- [참고링크](https://its-easy.tistory.com/12)

```javascript
$(function () {
  //모든 datepicker에 대한 공통 옵션 설정
  $.datepicker.setDefaults({
    dateFormat: 'yy-mm-dd', //Input Display Format 변경
    showOtherMonths: true, //빈 공간에 현재월의 앞뒤월의 날짜를 표시
    showMonthAfterYear: true, //년도 먼저 나오고, 뒤에 월 표시
    changeYear: true, //콤보박스에서 년 선택 가능
    changeMonth: true, //콤보박스에서 월 선택 가능
    showOn: 'both', //button:버튼을 표시하고,버튼을 눌러야만 달력 표시 ^ both:버튼을 표시하고,버튼을 누르거나 input을 클릭하면 달력 표시
    buttonImage: 'http://jqueryui.com/resources/demos/datepicker/images/calendar.gif', //버튼 이미지 경로
    buttonImageOnly: true, //기본 버튼의 회색 부분을 없애고, 이미지만 보이게 함
    buttonText: '선택', //버튼에 마우스 갖다 댔을 때 표시되는 텍스트
    yearSuffix: '년', //달력의 년도 부분 뒤에 붙는 텍스트
    monthNamesShort: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12'], //달력의 월 부분 텍스트
    monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'], //달력의 월 부분 Tooltip 텍스트
    dayNamesMin: ['일', '월', '화', '수', '목', '금', '토'], //달력의 요일 부분 텍스트
    dayNames: ['일요일', '월요일', '화요일', '수요일', '목요일', '금요일', '토요일'], //달력의 요일 부분 Tooltip 텍스트
    minDate: '-1M', //최소 선택일자(-1D:하루전, -1M:한달전, -1Y:일년전)
    maxDate: '+1M', //최대 선택일자(+1D:하루후, -1M:한달후, -1Y:일년후)
  });

  //input을 datepicker로 선언
  $('#datepicker').datepicker();
  $('#datepicker2').datepicker();

  //From의 초기값을 오늘 날짜로 설정
  $('#datepicker').datepicker('setDate', 'today'); //(-1D:하루전, -1M:한달전, -1Y:일년전), (+1D:하루후, -1M:한달후, -1Y:일년후)
  //To의 초기값을 내일로 설정
  $('#datepicker2').datepicker('setDate', '+1D'); //(-1D:하루전, -1M:한달전, -1Y:일년전), (+1D:하루후, -1M:한달후, -1Y:일년후)
});
```

## datepicker today button

- today 버튼 클릭 시 오늘 날짜로 선택되도록

```javascript
obj.datepicker({
  showButtonPanel: true,
});

$.datepicker._gotoToday = function (id) {
  $(id).datepicker('setDate', new Date()).datepicker('hide').blur().change();
};
```

- clear 버튼 추가

```javascript
function cleanDatepicker() {
  var old_fn = $.datepicker._updateDatepicker;

  $.datepicker._updateDatepicker = function (inst) {
    old_fn.call(this, inst);

    var buttonPane = $(this).datepicker('widget').find('.ui-datepicker-buttonpane');

    $(
      "<button type='button' class='ui-datepicker-clean ui-state-default ui-priority-primary ui-corner-all'>Delete</button>"
    )
      .appendTo(buttonPane)
      .click(function (ev) {
        $.datepicker._clearDate(inst.input);
      });
  };
}
```

- done 버튼 없애기

```css
/* datepicker input, custom button 롤오버 시 손가락 모양 표시*/
.hasDatepicker,
.btn-datepicker {
  cursor: pointer;
}

/* datepicker DONE 버튼 숨기기 */
button.ui-datepicker-close {
  display: none;
}

/* 오늘 버튼 글씨 투명도 수정 */
button.ui-datepicker-current {
  opacity: 1 !important;
}
```

## sample

```javascript
$(function () {
  /* jquery ui datepicker 공통 옵션 정의 */
  $.datepicker.setDefaults({
    dateFormat: 'yy-mm-dd', //Input Display Format 변경
    showOtherMonths: true, //빈 공간에 현재월의 앞뒤월의 날짜를 표시
    showMonthAfterYear: true, //년도 먼저 나오고, 뒤에 월 표시
    changeYear: true, //콤보박스에서 년 선택 가능
    changeMonth: true, //콤보박스에서 월 선택 가능
    yearSuffix: '년', //달력의 년도 부분 뒤에 붙는 텍스트
    monthNamesShort: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12'], //달력의 월 부분 텍스트
    monthNames: ['1월', '2월', '3월', '4월', '5월', '6월', '7월', '8월', '9월', '10월', '11월', '12월'], //달력의 월 부분 Tooltip 텍스트
    dayNamesMin: ['일', '월', '화', '수', '목', '금', '토'], //달력의 요일 부분 텍스트
    dayNames: ['일요일', '월요일', '화요일', '수요일', '목요일', '금요일', '토요일'], //달력의 요일 부분 Tooltip 텍스트
    currentText: '오늘',
  });
});

function fn_datepicker(obj, options) {
  let m_options = $.extend(
    {},
    {
      format: 'yy-mm-dd',
      isToday: false,
      showTodayButton: true,
    },
    options
  );

  // datepicker 생성
  obj.datepicker({
    dateFormat: m_options.format,
  });

  // 사용자 옵션에 따라 설정 추가
  // 1. 로딩 시 오늘 날짜로 설정
  if (m_options.isToday) {
    obj.datepicker('setDate', 'today');
  } else {
    obj.datepicker('setDate', '');
  }

  // 2. 오늘 버튼 달력 하단에 추가
  if (m_options.showTodayButton) {
    obj.datepicker('option', 'showButtonPanel', true);
    $.datepicker._gotoToday = function (id) {
      $(id).datepicker('setDate', new Date()).datepicker('hide').blur().change();
    };
  }
}
```

## input readonly일 때 datepicker 달력 표시하지 않도록 변경하기

- 공통 적용 시 setDefaults에 아래 옵션 추가
- [참고](https://stackoverflow.com/questions/7812063/jquery-datepicker-readonly)

```javascript
beforeShow: function(i) {
  if ($(i).attr('readonly')) { return false; }
}
```
