# b-table

bootstrap 에서 제공하는 vue.js 테이블

# Pagination

[링크](https://bootstrap-vue.js.org/docs/components/pagination/)

total-rows, per-page 를 연결해 놓으면 알아서 paging 이 된다.

```html
      <b-table bordered responsive :items="items" :fields="fields" :current-page="currentPage" :per-page="perPage">
        <template slot="title" slot-scope="row" class="title-col">
          <div  class="mr-1" v-on:click="detail(row.item.requestNo)">{{ row.value }}</div>
        </template>
      </b-table>
      <b-pagination size="sm" align="center" :total-rows="totalRows" v-model="currentPage" :per-page="perPage">
      </b-pagination>
```

data 에 totalRows, currentPage 정의

```javascript
export default {
  name: 'ContractList',
  // props :['items'],
  data() {
    return {
      fields: [
        { key: 'requestNo', label: '신청정보', sortable: true },
        { key: 'seal', label: '날인첨부' },
        { key: 'title', label: '제목' },
        { key: 'location', label: '지역' },
        ...
      ],
      items: items,
      totalRows: items.length,
      modalInfo: { title: '', content: '' },
      currentPage: 1,
      perPage: 2
    };
  }
};
```
