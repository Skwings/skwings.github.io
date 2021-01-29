---
layout: post
title: 'Hash路由与History路由模式'
date: 2020-1-3
author: feiYu
color: rgb(255,210,32)
cover: ''
tags: Js
subtitle: ''
---

### Hash路由与History路由模式

> Spa单页面应用需要在不刷新页面的情况下更新页面，需要使用前端路由，前端路由是利用了浏览器的Hash或者History属性。

#### Hash路由Api

> hash(url 中#后面的部分)虽然不会被包含在http请求中，对后端没有影响，因此改变hash不会重新加载页面

```javascript
window.onhashChange = function(){
    //ToDo
}//监听地址的切换 
```

#### History路由Api

```javascript
history.pushState(data, title, url) //入栈一条历史记录
history.replaceState(data, title, url) //替换一条历史记录
history.state //获取pushState和repalceState传递的data
```

这两种执行修改时，虽然改变了URL，但是浏览器不会立即向后端发送请求。

history对比hash

pushState设置的Url可以是当前同源下的任意url；hash只能修改#后面的部分，因此只能设置当前url同文档的url