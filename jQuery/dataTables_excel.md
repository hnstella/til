# datatables 데이터를 엑셀로 내보내기

## Button extension

Button extension으로 Datatable에 간단히 추가할 수 있다. 3가지 플러그인 방식을 제공한다.

- HTML5 export buttons - HTML5 API를 사용하여 클라이언트 사이드에서 파일을 생성
- Flash export buttons - Adobe Flash 사용
- Print button

## 제공하는 기능

- Copy to clipboard
- Save as Excel(XLSX)
- Save as CSV
- Save as PDF
- Display a print view

## 사용법

기본 버튼 사용

```javascript
$('#example').DataTable({
  buttons: ['excelHtml5']
});
```

버튼 Customize

```javascript
$('#example').DataTable({
  buttons: [
    {
      extend: 'excelHtml5',
      text: '엑셀 내보내기'
    }
  ]
});
```

## 필요한 라이브러리

javascript

> https://code.jquery.com/jquery-3.3.1.js > https://cdn.datatables.net/1.10.19/js/jquery.dataTables.min.js > https://cdn.datatables.net/buttons/1.5.2/js/dataTables.buttons.min.js > https://cdnjs.cloudflare.com/ajax/libs/jszip/3.1.3/jszip.min.js > https://cdn.datatables.net/buttons/1.5.2/js/buttons.html5.min.js

css

> https://cdn.datatables.net/1.10.19/css/jquery.dataTables.min.css > https://cdn.datatables.net/buttons/1.5.2/css/buttons.dataTables.min.css

# LINK

- [File export](https://datatables.net/extensions/buttons/examples/initialisation/export.html)
- [Excel - Bold text](https://datatables.net/extensions/buttons/examples/html5/excelTextBold.html)
- [Button configuration](https://datatables.net/extensions/buttons/config)
