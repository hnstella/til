# jquery validation

- [jquery validate](https://jqueryvalidation.org/validate/)

```javascript
$('#searchForm').validate({
  rules: {
    form7: {
      required: true,
      minlength: 3,
    },
    form6: {
      required: true,
      minlength: 3,
    },
    form3: {
      number: true,
    },
    form4: {
      number: true,
    },
    date1: {
      dateISO: true,
    },
  },
  messages: {
    /* 에러 문구 수정이 필요한 경우 아래에 필드별 에러메시지를 정의한다 */
    form7: {
      required: '납품처 값을 입력해 주세요',
    },
  },
  submitHandler: function (form) {
    grid_reload(maingrid);
  },
});
```

## text 표시하지 말고 알람 처리

- text 표시하지 않고 알람 처리 (invalidHandler)
- highlight/unhighlight에서 bootstrap class 추가/삭제 (참고)[https://stackoverflow.com/questions/28489625/jquery-validation-showerrors-blocks-highlight-unhighlight]

```javascript
$(function () {
  $.validator.setDefaults({
    errorClass: 'is-invalid',
    validClass: 'is-valid',
    errorPlacement: function (error, element) {
      // 에러 발생 시 alert 창으로 띄우고 element나 tooltip으로 표시 안함
    },
    highlight: function (element, errorClass, validClass) {
      $(element).addClass(errorClass);
    },
    unhighlight: function (element, errorClass, validClass) {
      $(element).removeClass(errorClass);
      //            $(element).addClass(validClass);      // valid border 표시
    },
    invalidHandler: function (form, validator) {
      var obj = validator.errorList[0].element;
      // focus invalid input
      var errors = validator.numberOfInvalids();
      if (errors) {
        alert(validator.errorList[0].message); // 경고창으로 띄움
        validator.errorList[0].element.focus();
      }
    },
  });

  $.validator.addMethod(
    'time',
    function (value, element) {
      if (value == '') return true;
      return /^(?:2[0-3]|[01][0-9]):[0-5][0-9]:[0-5][0-9]$/.test(value);
    },
    '형식에 맞춰 시간을 입력해 주세요 (HH:MM:SS)'
  );
});
```

## valid() - 원하시는 시점에 validate 수행

form validate() 선언 후, 원하는 시점에 form.valid()를 호출한다.

- invalidHandler에서 invalid한 input에 대해 포커싱한다.
- [jquery invalid() method](https://jqueryvalidation.org/valid/)

```javascript
    $('#searchForm').validate({
        rules: {
            form7: {
                required: true,
                minlength: 3
            },
            form6: {
                required: true,
                minlength: 3
            },
            form3: {
                number: true
            },
            form4: {
                number: true
            },
            date1: {
                dateISO: true
            },
            time1: {
                time: true      // HH:MM:SS 형식
            }
        },
        messages: {
            /* 에러 문구 수정이 필요한 경우 아래에 필드별 에러메시지를 정의한다 */
            form7: {
                required: "납품처 값을 입력해 주세요"
            }
        },
        onfocusout: false,
        invalidHandler: function(form, validator) {
            // focus invalid input
            var errors = validator.numberOfInvalids();
            if (errors) {
                validator.errorList[0].element.focus();
            }
        }
```

- [How to focus invalid fields with jQuery validate?](https://stackoverflow.com/questions/10111907/how-to-focus-invalid-fields-with-jquery-validate)
