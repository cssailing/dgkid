---
layout: post
title: "vuejs 2.6.6 datatable"
quote: "vuejs, datatable, localhost, componets, api, search"
image: false
video: false
comments: true
---

-----
```console
  yarn add fuse.js
  yarn add tb-skeleton
```
use datatable.vue as a componet, you can do everything you wangt to do
follow package 
- [MicroDroid/vue-materialize-datatable] (https://github.com/MicroDroid/vue-materialize-datatable)

### componets/DataTable.vue
```html
  export default {
		props: {
      locale: {
          type: String,
          required: false,
          default: 'cn',  //set default language
        },
    }
    data: () => ({
			locales: { //language data
				cn: {
					"rows_per_page": "每页",
					"out_of_pages": "of",
					"all": "所有",
					"search_data": "搜索信息"
				},
				en: {
					"rows_per_page": "rows-page",
					"out_of_pages": "of",
					"all": "all",
					"search_data": "Search"
				}
			},
		}),
```
### view/table.vue
```html
<template>
    <div class="table-responsive">
        <datatable
            title="table title"
            :columns="tableColumns"
            :rows="tableRows"
            :exportable="false"
            :printable="false"
            :perPage= "[50, 100, 200]"
            :defaultPerPage= "50"
        />
    </div>
</template>
<script>

import DataTable from "@/components/DataTable";
export default {
    name: 'list-table',
    components: {
        "datatable": DataTable
    },
    data() {
        return {
            tableRows: [],
            tableColumns:[
                {label: "username", field: "name", numeric: false, html: false },
                {label: "sex", field: "gender", numeric: false, html: false },
                {label: "company", field: "company", numeric: false, html: false },
                {label: "career", field: "career", numeric: false, html: false },
                {label: "location", field: "location", numeric: false, html: false }
            ]
        }
    },
    mounted(){
        this.getTableData();
    },
    methods: {
        getTableData(){
            let params = {
                params: {
                    type: '',
                    token: ,
                }
            };
            this.axios.get('/', params)
            .then(response => {
                if (response.data.code == 4){
                    this.tableRows = response.data.lists;
                }else{
                    this.$router.push('/');
                }
            })
        }
    }
};

</script>
<style>
/**
*移动端 table td 竖排显示
 */
@media screen and (max-width: 500px){
    .table-responsive table  thead {display: none !important;}
    .table-responsive table  td:before {content: attr(data-label);float: left;text-transform: uppercase;font-weight: bold;}
}
table th {border-bottom: 0.125rem solid #dee2e6}
/**
* 去掉翻页 li 的点
*/
li {list-style-type:none;}
</style>
```
