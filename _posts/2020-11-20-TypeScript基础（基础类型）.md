---

layout: post

title: 'TypeScript基础（基础类型）'

date: 2020-11-20

author: feiYu

color: rgb(255,210,32)

cover: '../assets/test.png'

tags: TypeScript
 
subtitle: " "

---

### TypeScript基础（一）

#### 基础类型

##### 布尔值

```typescript
let isDone: boolean = false; //类型注解
```

##### 数字

和Javascript一样，TypeScript里的所有数字都是浮点数。这些浮点数的类型是`number`。Ts支持二进制和八进制字面量。

```typescript
let deLiteral: number = 6;
let hexLiteral: number = 0xf00d;
let binaryLiteral: 0b1010;
```

##### 字符串

```typescript
let name: string = "hello!";
```

```typescript
let name: srting = `
	WuZhiJian
`;
let age: number = 22;
let sentence: string = `Hello, my name is ${name}.My age is ${age}.`
```

模板字符串可以定义多行文本与内嵌表达式。以`${expr}`这种形式嵌入表达式。

##### 数组

Ts定义数组有两种方式

```typescript
let list: number[] = [1, 2, 3];
```

```typescript
let list: Array<number> = [1, 2, 3];
```

##### 元组

元组类型允许表示一个已知元素数量和类型的数组。

```typescript
let x: [number, straing];
x = [13, "hello"];
```

当访问一个越界的元素，会使用联合元素代替。

```javascript
x[3] = "Jack"; //属于 number | string，ok
x[4] = true; //报错，属于 number | string
```

##### 枚举

`enum`类型是对JavaScript标准数据类型的一个补充。像其他语言一样，使用枚举可以为一组数值赋予有好的名字。所有枚举类都是enum的子类

```typescript
enum Color {Red, Blue, Green}
let c: Color = Color.Green;
```

```java
public enum Direction{
	Red, Blue, Green;
}
Direction d = Direction.Red;
```

默认情况，从0开始为元素编号，可以手动设置。

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
```

```typescript
enum Color {Red = 1, Green, Blue}
let c: Color = Color[3];
console.log(c); //Blue
```

##### 任意值

编程时，常常遇到还不清楚为变量定义哪个类型，然鹅我们不希望他报错，这时候我们就可以通过`any`来定义这些变量。

```typescript
let notSure: any;
notSure = "hello";
notSure = 123;
notSure = true;
notSure.sayHello(); //Ok
```

只知道部分数据类型

```typescript
let list: any[] = [123, "hello", true];
```

##### Null 和 Undefined

默认情况两者是所有类型的子类。可以将两者赋给其他其他类型的变量。

##### Never

never类型表示那些永远不存在值的类型。例如抛出异常或根本不存在值得函数表达式。

