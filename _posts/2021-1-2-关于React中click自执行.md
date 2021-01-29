---
layout: post
title: '关于React中click自执行'
date: 2020-1-2
author: feiYu
color: rgb(255,210,32)
cover: '../assets/react.jpg'
tags: React
subtitle: ''
---

### 关于React中click自执行

`onClick = {此处为函数引用或匿名函数}`

所以如果`onclick={this.handle()}`这种写法就相当于写了一个自执行函数，会在页面初始化时执行。点击的话也不会触发相应的事件。

解决方案

方法一

```jsx
onClick = {this.handle}
```

方法二

```jsx
onClick = {() => {this.handle()}}
```

