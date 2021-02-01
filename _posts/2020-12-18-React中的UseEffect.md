### React中的UseEffect

> react官方推崇我们使用钩子函数（与之对应的是Es6类），因为钩子函数代码更加简洁。较为符合React本质。

#### UseEffect出现的原因

类与函数的差异

+ 类是数据和逻辑的封装。组件的数据与操作应被写于同一个Class中。
+ 函数一般来说需要做的就是返回一个值。如果有多个操作，每个操作应该写成一个单独的函数。而且数据的状态与操作应该分离。

如下就是一个存函数：不改变数据的状态，只依据输入返回相应的代码。

```jsx
funciton Welcome(props){
    return <h1>{this.props.name}</h1>
}
```

#### 什么是负效应

> 函数式编程将那些和数据计算无关的操作（生成日志、存储数据、改变应用状态等），都称之为负效应。

#### 钩子（hook）的作用

hook的作用就是用来处理React组件中副效应。函数组件的主体用来返回HTML代码，其他副效应操作都应该通过钩子引入。

钩子有多种：

useState（）：保存状态

useContext（）：保存上下文

useRef（）：保存引用 

...

#### `UseEffect`的作用

就是一个通用的`副效应钩子`。找不到对应钩子时就可以用它。

语法：

```jsx
useEffect(sidefn, [依赖项])
```

##### 用法：

```jsx
function Welcome(props){
    useEffect(() => {
        document.title = 'Loaded'
    })
    return <h1>{props.name}</h1>
}
```

这个例子中，组件每渲染一次，该函数就会执行一次。组件在网页Dom初始化后，副效应函数也会执行。

##### 第二个参数

useEffect的第二个参数可以指定一个依赖项，避免useEffect在每次渲染时都被执行，当依赖项发生改变时才会执行函数。

```jsx
function Welcome(props) {
  useEffect(() => {
    document.title = `Hello, ${props.name}`;
  }, [props.name]);
  return <h1>Hello, {props.name}</h1>;
}
```

第二个参数可以传入一个数组，声明依赖项。如果是传入空数组，则只在组件加载时才会执行，只执行一次。

#### useEffect常见使用场景

+ 获取数据
+ 事件监听
+ 改变Dom
+ 输出日志

#### UseEffect的返回值

UseEffect允许返回一个函数，这个函数在组件被卸载时会触发。

```jsx
useEffect(() => {
  const subscription = props.source.subscribe();
  return () => {
    subscription.unsubscribe();
  };
}, [props.source]);
```

每次使用UseEffect时，如果有多个副效应，则应该调用多个UseEffect，而不是合并写在一起。

```jsx

function App() {
  const [varA, setVarA] = useState(0);
  const [varB, setVarB] = useState(0);

  useEffect(() => {
    const timeout = setTimeout(() => setVarA(varA + 1), 1000);
    return () => clearTimeout(timeout);
  }, [varA]);

  useEffect(() => {
    const timeout = setTimeout(() => setVarB(varB + 2), 2000);

    return () => clearTimeout(timeout);
  }, [varB]);

  return <span>{varA}, {varB}</span>;
}
```

