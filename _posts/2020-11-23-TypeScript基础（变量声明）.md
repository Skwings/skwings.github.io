---

layout: post

title: 'TypeScript基础(变量声明)'

date: 2020-11-23

author: feiYu

color: rgb(255,210,32)

cover: '../assets/typeScript2.jpg'

tags: TypeScript

subtitle: " "

---

### 变量声明

#### let

let不允许重复声明，在循环里引用时会引入一个新的环境变量，针对每次迭代都会创建一个新的作用域。

#### 结构数组

解构赋值

```typescript
let input = [1, 2];
let [first, second] = input;
```

用于以声明变量

```typescript
[first, second] = [second, first]; //swap variables
```

作用于函数参数

```typescript
function([first, second]: [number, number]){
	console.log(first);
	console.log(second);
}
```

#### 展开

数组

```typescript
let first = [1, 2];
let second = [3, 4];
let both = [0, ...first, ...second];
```

对象

```typescript
let defaults = {food: "spicy", price: "$$", ambiance:"no"};
let search = {...defaults, food: "rich"};//food: "rich"
```

