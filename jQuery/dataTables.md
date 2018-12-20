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
