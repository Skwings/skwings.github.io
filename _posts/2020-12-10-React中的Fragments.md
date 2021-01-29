### React中的Fragments

Fragments的作用：

> fragments允许你将子列表分组，并且无需向Dom节点添加额外节点。

语法一：

```jsx
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}
```

语法二：

```jsx
render() {
  return (
    <>
      <ChildA />
      <ChildB />
      <ChildC />
    </>
  );
}
```

#### 为什么要用fragments

例如现在有这样一个场景，父组件table，需要子组件返回<td>来渲染元素。

```jsx
class Table extends React.Component {
  render() {
    return (
      <table>
        <tr>
          <Columns />
        </tr>
      </table>
    );
  }
}
```

```jsx
class Columns extends React.Component {
  render() {
    return (
      <div>
        <td>Hello</td>
        <td>World</td>
      </div>
    );
  }
}
```

此时子组件<Colums />返回了的react元素中使用了父<div>，这样导致了table不能正常渲染。

此时就可以用fragments解决这个问题。

```jsx
class Columns extends React.Component {
  render() {
    return (
      <React.Fragments>
        <td>Hello</td>
        <td>World</td>
      </React.Fragments>
    );
  }
}
```

此时返回的就是正常的<td>