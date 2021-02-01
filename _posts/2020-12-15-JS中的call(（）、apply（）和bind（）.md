---

layout: post

title: 'JS中的call(（）、apply（）和bind（）'

date: 2020-12-15

author: feiYu

color: rgb(255,210,32)

cover: '../assets/ECMAScript.jpg'

tags: Js

subtitle: " "

---
### JS中的call(（）、apply（）和bind（）

再js中，call、apply、bind都是用来改变原函数执行上下文，也就是说，改变函数执行时内部的this指向。

语法：

```javascript
.call(obj, arg1, arg2, arg3...)
```



```javascript
.apply(obj, [arg1, arg2, arg3...])
//参数为null或者undefined时，则指向全局对象
```

#### Apply:

在调用一个存在的函数时，你可以为其指定一个this对象。this指的是当前调用这个函数的对象。

示例：

```javascript
function fruits(){}

fruits.pototype = {
    color: 'red',
    say: function(){
        console.log('我的颜色是'+ this.color)
    }
}

var another = {
    color: 'yellow'
}

var apple = new fruits();
apple.say();// red
apple.say.apply(another); //yellow
apple.say.call(another); //yellow
```



用apply将数组各项添加到另一个数组

```javascript
var array = ['a', 'b'];
var ele = [0, 1, 2];
array.push.apply(array, ele);
//如果直接push的话，会将ele整个作为一个元素传递给array
```

实现继承