README
===========================
解决mpvue多个页面公用一个vm对象的问题 [mpvue issue 140](https://github.com/Meituan-Dianping/mpvue/issues/140)

### 使用方法:

使用我的[mpvue-loader分支](https://github.com/HelloZJW/mpvue-loader)

pagckage.json 中添加依赖
```
"mpvue-loader": "git+https://github.com/HelloZJW/mpvue-loader.git",
"mpvue-page-factory": "^1.0.0",
```

在页面的main.js中
 ```javascript
import pageFactory from 'mpvue-page-factory'
import App from './index'

Page(pageFactory(App))
```

### 如果你用了mpvue-entry:

```
"mpvue-loader": "git+https://github.com/HelloZJW/mpvue-loader.git",
"mpvue-page-factory": "^1.0.0",
```
#### 配置方法:
在你的pages.js相同目录下建一个template.js文件，此文件为入口模板；里面内容为:
```
import pageFactory from 'mpvue-page-factory'
import App from '@/App'

Page(pageFactory(App))
```
然后修改build/webpack.base.conf.js 中MpvueEntry.getEntry()方法的入参
```
const fs = require('fs');
const entry = MpvueEntry.getEntry({
  pages: './src/pages.js', //可以不填，缺省就是这个
  main: './src/main.js',  //可以不填，缺省就是这个
  template: './src/template.js'
})
```
然后你会发现node_module/mpvue-entry/dist目录里面js文件内容发生了变化。
![image](https://user-images.githubusercontent.com/8361397/45264454-43671a00-b46f-11e8-8b4f-ecfd534a4755.png)

enjoy，其他工程代码不需要修改
