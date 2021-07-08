---

layout: post

title: '关于React中的为什么需要用bind（this）'

date: 2021-04-21

author: feiYu

color: rgb(255,210,32)

cover: '../assets/react.jpg'

tags: React

subtitle: ""

---

### 关于React中的为什么需要用bind（this）

> 当React实例中的方法中用到了this属性时，通常会在constructor中进行this绑定。来看个例子了解为什么需要这么做。

```jsx
import React from 'react';
export default class Life extends React.Component{
    constructor(props){
        super(props);
        this.state = {
            count:4
        };
    }
    render(){
        var style = {
            padding:'10px',
            color:'red',
            fontSize:'30px'
        }
        return (
            <div style={style}>{/*注意js语法使用一个括号{}去表示,style使用两个括号,原因里面其实是一个对象*/}
                <p>React生命周期介绍</p>
                <button onClick={this.handleAdd}>无bind点击一下</button>
                <button onClick={this.handleClick.bind(this)}>有bind点击一下</button>
                <p>{this.state.count}</p>
            </div>
        )
    }
    //此时this指向是当前实例对象
    handleAdd = ()=> {
        console.log(this)
        this.setState({
            count:5
        })
    }
    handleClick(){
        this.setState({
            count:6
        })
    }
}
```