---
layout: post
title: "vuejs 2.6.6 axios"
quote: "vuejs, axios, localhost, development env, cross domain, api,  Access-Control-Allow-Origin"
image: false
video: false
comments: true
---

-----
```console
  yarn add axios
```

### main.js
```html
  import axios from "axios";
  Vue.prototype.axios = axios; //把axios挂载到vue的原型中，在vue中每个组件都可以使用axios发送请求
  //axios base config
  axios.defaults.timeout = 5000;
  axios.defaults.baseURL = 'http://127.0.0.1:8098/api'; //定义api路径
```

### vue.config.js
```html
  devServer: {
        open: true,
        host: '0.0.0.0', // 允许外部ip访问
        port: 8080, // 端口
        https: false, // 启用https
        hot: true, //hot配置是否启用模块的热替换功能，devServer的默认行为是在发现源代码被变更后，通过自动刷新整个页面来做到事实预览，开启hot后，将在不刷新整个页面的情况下通过新模块替换老模块来做到实时预览。
        overlay: {
            warnings: true,
            errors: true
        }, // 错误、警告在页面弹出
   }
```

-----
