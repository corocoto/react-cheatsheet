### Class Components and Functional Components

1. Example of work:

* Stateless (Class) Component:

```jsx
export class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}
```

* Stateless Functional Component: 

```jsx
export const MyComponentClass = () => {
  return <h1>Hello world</h1>;
}
```

2. Work with props:

* Stateless (Class) Component:

```jsx
export class MyComponentClass extends React.Component {
  render() {
    return <h1>{this.props.title}</h1>;
  }
}
```

* Stateless Functional Component: 

```jsx
export const MyComponentClass = (props) => {
  return <h1>{props.title}</h1>;
}
```