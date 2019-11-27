---
layout: post
title: "vuejs 2.6.6 mockjs"
quote: "vuejs, mockjs, localhost, development env, cross domain, api, data, Access-Control-Allow-Origin"
image: false
video: false
comments: true
---

-----
```console
  yarn add mockjs
```

### view.vue
```html
  import mockData from '../_mockData'
  export default {
  data: () => ({
    data: [],
    total: 0,
  }),
  watch: {
    query: {
      handler () {
        this.loadData()
      },
      deep: true
    }
  },
  methods: {
    loadData () {
      mockData(this.query).then(({ rows, total }) => {
        this.data = rows
        this.total = total
      })      
    }
  }
```

-----

or can use json file direct

```html

import apijson from "@/data/apijson.json";
export default {
	name: 'api-show',
	components: {
		'task': () => import('@/components/task')
	},
	data: function() {
		return {
			items: apijson
		}
	},	
}

```
-----

