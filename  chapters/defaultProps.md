## `defaultProps`

[EN]

`defaultProps` is a property in React component used to set default values for the `props` argument. It will be changed if the prop property is passed.

Example of work `defaultProps`:
```jsx
class Example extends React.Component {
  render() {
    return <h1>{this.props.text}</h1>;
  }
}

Example.defaultProps = { text: 'yo' }; 
```

[RU]

`defaultProps` - это свойство в React-компоненте, используемое для установки значений по умолчанию для аргумента `props`. Он будет изменен, если передано соответствующее свойство prop.

Пример работы `defaultProps`:
```jsx
class Example extends React.Component {
  render() {
    return <h1>{this.props.text}</h1>;
  }
}

Example.defaultProps = { text: 'yo' }; 
```
