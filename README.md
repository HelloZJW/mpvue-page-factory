README
===========================
解决mpvue多个页面公用一个mpvue的问题 [mpvue issue 140](https://github.com/Meituan-Dianping/mpvue/issues/140)

## 使用方法:

在页面的main.js中
 ```javascript
import pageFactory from 'mpvue-page-factory'
import App from './index'

Page(pageFactory(App))
```
