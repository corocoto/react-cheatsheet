### `defaultProps` keyword

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