---

layout: post

title: '对于Vuex中的actions与mutations区别的理解'

date: 2020-12-9

author: feiYu

color: rgb(255,210,32)

cover: '../assets/vue.png'

tags: Vue

subtitle: " "

---

### 对于Vuex中的actions与mutations区别的理解

actions与mutations同样可以实现异步操作，为什么异步操作要用actions而不是mutations呢？

官方文档中的说明

> 现在想象，我们正在 debug 一个 app 并且观察 devtool 中的 mutation 日志。每一条 mutation 被记录，devtools 都需要捕捉到前一状态和后一状态的快照。然而，在上面的例子中 mutation 中的异步函数中的回调让这不可能完成：因为当 mutation 触发的时候，回调函数还没有被调用，devtools 不知道什么时候回调函数实际上被调用——实质上任何在回调函数中进行的状态的改变都是不可追踪的。

实际上在mutation中执行异步操作，并不适合devtools进行调试，追踪状态的变更。

改变state唯一的方法是提交mutation，所在在action中需要commit触发mutation进行状态更改。

#### 所以

+ Mutation中写的是同步函数，actions中写的需要是异步函数，这是一种约定，为了更好的追踪vuex的状态变更，我们都需要按照这种原则进行开发。
+ 更改state的唯一方法是提交mutation，action中需要通过commit触发mutation。

