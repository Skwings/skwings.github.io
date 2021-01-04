---

layout: post

title: 'TypeScript基础(接口)'

date: 2020-11-23

author: feiYu

color: rgb(255,210,32)

cover: '../assets/typeScript2.jpg'

tags: TypeScript

subtitle: ""

---

### 接口

这里规定了printLabel需要有一个string类型的属性。

```typescript
function printLabel(labelledObj: {label: string}){
	console.log(labelledObj.label);
}
let obj = {size: 10, label: "Ok"};
printLabel(obj);
```

```typescript
interface Label{
	label: string;
}

function printLabel(labelObj: Label){
	console.log(labelObj.lable);
}
```

Label就好比一个名字，用来描述上述例子的要求。

#### 可选属性

接口当中的属性不全是必须的。或者根本不存在。

```typescript
interface SquareConfig{
	color?: string;
	width?: number;
}

function createSqure(config: SquareConfig): {color: string; area: number}{
	let newSquare = {color: "white", area: 100};
	if(config.cplor){
		newSquare.color = config.color;
	}
	return newSquare;
}

let mySquare = createSqure({color: "black"});
```

可选属性的好处之一是对属性进行预定义，可以捕获引用了不存在的属性时的错误。

#### 只读属性

```typescript
interface Point {
	readonly x: number;
	readonly y: number;
}
let p1:Point = {x: 10, y:20};
p1.x = 5; //error
```

Typescript具有Readonly属性，与array相似，只是把所有可变方法去掉了。

#### 类型断言

```typescript
let mySquare = createSquare({width: 100, opacity: 0.5} as SquareConfig); //可跳过ts额外的属性检查
```

```typescript
interface SquareConifg{
	color?: string;
	width?: number;
	[propName: string]: any;
}; //类型签名，在确定对象可能具有额外属性属性时可以使用。
```

​       