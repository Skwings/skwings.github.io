---

layout: post

title: '对于Es6中关于Async、await的理解'

date: 2020-11-24

author: feiYu

color: rgb(255,210,32)

cover: '../assets/ECMAScript.jpg'

tags: Es6

subtitle: " "

---

### 对于Async/await的理解

async输出的是一个Promise对象，如果在async中return一个直接量，async会把这个直接量通过Promise.resolve封装成Promise对象。

```typescript
async function testAsync(){
	return "hello";
}
console.log(testAsync()); //=>Promise{'hello'}
```

#### await

await的作用是等待一个async函数的完成。用于等待async函数的返回值。

```typescript
async function test(){
	const v = await Promise.resolve("Hello");
	console.log(v);
}
```

##### 为什么要用async？

来看一个比较典型的情况

```javascript
async function do(){
	const num1 = 1;
	const num2 = await step1(num1);
	const num3 = await step2(num1, num2);
	const result = await step3(num1, num2, num3);
}
```

可以看出step函数每一步的执行都依赖上一个函数的结果。async在处理这种情况时比写Promise代码看起来简洁多了。

来看看用Promise如何写

```javascript
function do(){
	const num1 = 1;
	step1(num1).then(num2=>{
		return step2(num1, num2).then(num3 => [num1, num2, num3]);
	}).then(num3 => {
        const [num1, num2, num3] = num3;
		return step3(num1, num2, num3);
	})
}
```



