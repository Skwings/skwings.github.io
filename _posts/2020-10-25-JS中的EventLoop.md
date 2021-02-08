---

layout: post

title: 'JS中的EventLoop'

date: 2020-10-25
author: feiYu

color: rgb(255,210,32)

cover: '../assets/ECMAscript.jpg'

tags: JS

subtitle: ""

---


### JS中的EventLoop

> JS为了避免复杂性一开始就是单线程的。那么JS是通过什么来协调各个事件的呢？

#### JS中的代码分为两类

+ 同步任务
+ 异步任务

![](..\..\..\assets\images\eventLoop.jpg)

如图可以看出：

+ 同步和异步任务分别进入不同的执行场所，同步任务进入主线程，异步的进入EventTable并注册函数
+ 当指定的事情完成时，EventTable会将这个函数移入到EventQueue。
+ 当主线程的任务栈执行为空时，会去EventQueue读取对应的函数，进入主线程执行。
+ 上述的过程会不断的重复，也就是常说的EventLoop



JS存在monitoring process进程，会持续不断的检查主线程执行栈是否为空，一旦为空就会去Queue那里检查是否有等待被调用的函数。



#### 异步任务

宏任务：整体代码script， setTimeout， setInterval()

微任务：Promise.then(), process.nextTick(node特有) 

宏任务与微任务会放入不同的EventQueue中。那么它们的执行顺序是怎样的呢？

![](..\..\..\assets\images\eventLoop2.jpg)

那么此时来看一个例子：

```js
setTimeout(() => {
    task()
},3000)

sleep(10000000)
```



此时我们发现task（）任务执行时间远不止3秒。

此段代码的执行顺序：

> + task进入EventTable并注册，等待计时
> + 执行sleep函数
> + 3秒到了，task进入eventQueue
> + sleep执行完毕，查询eventQueue，执行task

我们常看见的`setTimeout(fn, 0)`的作用是，当主线程执行完后立马执行。  

上述代码不包含微任务，接下来看包含微任务的代码：

```javascript
setTimeout(function() {
    console.log('setTimeout');
},1000)

new Promise(function(resolve) {
    console.log('promise');
}).then(function() {
    console.log('then');
})

console.log('console');
```

+ 首先setTimeout被放入EventTable中，一秒后将`console.log('setTimeout')`放入宏任务EventQueue中。
+ 执行Promise中的同步代码`console.log('promise')`，将then放入微任务队列中
+ 执行同步代码`console.log('console');`
+ 执行宏任务`console.log('setTimeout');`
+ 执行微任务`console.log('then')`