---

layout: post

title: 'TypeScript的意义'

date: 2020-11-20

author: feiYu

color: rgb(255,210,32)

cover: '../assets/test.png'

tags: TypeScript

subtitle: "Ts为什么会出现，以及为什么我们需要使用它？"

---


### TypeScript的意义

> Ts是Js的超集，具有可选类型并且可以编译为Js。技术上讲Ts就是具有静态类型的JavaScript。

TypeScript的设计目的是解决Js的弱类型以及没有命名空间的缺点，这导致了很难实现模块化，并且不适合大型程序的开发。

##### 为什么需要向Js添加静态类型？

+ 经常出现类型未定义的问题
+ 使重构代码变的更为方便
+ 使大型复杂的应用程序源码更加容易阅读
+ 减少不必要的类型判断

```
//不必要的类型判断
function sum(a, b){
  if(typeof a !== 'number' || typeof b !== 'number') {
    throw new TypeError('arguments must be a number')
  }
}
```

##### 动态类型的缺点：

+ 动态类型的自由特性经常会导致错误，这些错误不仅会降低程序员的工作效率，而且还会由于增加新代码的成本变高导致开发陷入停顿。Javascript无法合并类型以及编译时缺乏错误检查，使得它不适合作为企业和大型代码库中服务端代码。

##### TypeScript的强类型判断：

+ 可以提前发现代码错误提示。Ts可以声明变量类型，那么当其他任何变量类型的赋值将会引起编译错误。强类型的好处就是智能提示，例如你可以知道当前变量具有哪些属性和方法。

##### 模块化

+ 利用Ts的关键词module，可以达到类似与命名空间的效果，而export可以控制是否外部访问。

  ```typescript
  module Project{
  	export module Core{
          function FuncA(){}
          export function FuncB(){}
      }
  }
  ```

  只有被export的对象才能被访问，module可以合并，非export对象在其他module下，即使是同一名称，也不能被访问。

  ##### 语法糖

  TypeScript可以实现类，接口，枚举，泛型，方法重载等。