# DataTables

## dataTable ajax

```javascript
table = $('#userListTbl').DataTable({
  pageLength: 25,
  processing: true,
  searching: true,
  ordering: false,
  info: false,
  lengthChange: false,
  serverSide: false,
  ajax: {
    url: '/pharosExt/getUserList.do',
    type: 'GET',
    dataSrc: 'list'
  },
  columns: [{ data: 'COMP_NM' }, { data: 'NAME' }, { data: 'PERSON_NO' }]
});
```

- [참고 : Nested object data (objects)](https://datatables.net/examples/ajax/deep.html)

## 커스텀 필터링

```javascript
// datatable 검색 기능 customize
$.fn.dataTable.ext.search.push (function (settings, data, dataIndex) {
    var input = $('#searchName').val();
    var name = data[1];

    if (!input) {
        return true;
    }

    //if (input && name == input) {
    if (name.match(input)) {
        return true;
    }
    return false;
});

$(document).ready(function() {
   /* Modal에서 사용자 이름 검색 버튼 클릭 시 결과 표시 */
   $(document).on('click', '#searchBtn', function(e) {
       var table = $('#userListTbl').DataTable();
       table.draw();
   });
}
```

- [참고 : Custom filtering - range search](https://datatables.net/examples/plug-ins/range_filtering.html)

## Check dataTable reinitialise

- [참고 : 3. Warning: Cannot reinitialise Data](https://datatables.net/manual/tech-notes/3#retrieve)

## 특정 컬럼 hidden 처리 시 값 가져오는 방법

- [row().data()](<https://datatables.net/reference/api/row().data()>) 참고
- row().data()를 사용하여 가져온다.

1. visible: false 처리

```javascript
table = $('#userListTbl').DataTable({
  pageLength: 10,
  pagingType: 'simple',
  processing: true,
  searching: true,
  ordering: false,
  info: false,
  lengthChange: false,
  serverSide: false,
  ajax: {
    url: '/pharosExt/getUserList.do',
    type: 'GET',
    data: {
      userId: oaId
    },
    dataSrc: 'list'
  },
  columns: [
    { data: 'COMP_NM' },
    { data: 'DEPT_NM' },
    { data: 'NAME' },
    { data: 'EMAIL' },
    { data: 'PERSON_NO', visible: false },
    { data: 'COMP_CD', visible: false }
  ]
});
```

2. 데이터 선택 시 선택한 row 데이터 가져오기

```javascript
/* Modal에서 row 선택 시 요청자에 입력 */
$(document).on('click', '#userListTbl tbody tr', function(e) {
  e.preventDefault();

  var table = $('#userListTbl').DataTable();
  var columns = table.row($(this)).data();
  console.log(columns);

  $('#compCd').val(columns.COMP_CD);
  $('#compNm').val(columns.COMP_NM);
  $('#userId').val(columns.PERSON_NO);
  $('#userNm').val(columns.NAME);
  $('#myModal').modal('toggle');
});
```
