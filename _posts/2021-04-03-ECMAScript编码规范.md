---

layout: post

title: 'Es2015的解构'

date: 2021-04-03

author: feiYu

color: rgb(255,210,32)

cover: '../assets/ECMAScript.jpg'

tags: Js

subtitle: ""

---

### ECMAScript编码规范

> ECMAScript 6（以下简称 ES6）是 JavaScript 语言的下一代标准，ES6 的第一个版本，就这样在 2015 年 6 月发布了，正式名称就是《ECMAScript 2015 标准》（简称 ES2015）。2016 年 6 月，小幅修订的《ECMAScript 2016 标准》（简称 ES2016）如期发布，这个版本可以看作是 ES6.1 版，因为两者的差异非常小（只新增了数组实例的 includes 方法和指数运算符），因此，ES6 是一个泛指， 含义是 5.1 版以后的 JavaScript 的下一代标准，涵盖了 ES2015、ES2016 等，而 ES2015 则是正式名称，特指该年发布的正式版本的语言标准。



#### 变量

+ 【强制】 使用let，const代替var

```js
//bad
var username =  "wzj";
var CONFIG = {};

//good
let username = "wzj";
const CONFIG = {};
```

+ 【强制】禁止修改const类型的变量

```js
//bad
const a = 1;
a = 2;
```



