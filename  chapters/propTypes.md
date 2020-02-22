### `propTypes`

React provides an internal mechanism for adding type checking to components. 

React components use a special property named `propTypes` to set up type checking.


Example of work `propTypes`:

```jsx
export class MessageDisplayer extends React.Component {
  render() {
    return <h1>{this.props.message}</h1>;
  }
}

// This propTypes object should have
// one property for each expected prop:
MessageDisplayer.propTypes = {
  message: React.PropTypes.string
};
```


List of available types, which using for work with `propTypes`:

```jsx
Runner.propTypes = {
   message:   React.PropTypes.string.isRequired,
   style:     React.PropTypes.object.isRequired,
   isMetric:  React.PropTypes.bool.isRequired,
   miles:     React.PropTypes.number.isRequired,
   milesToKM: React.PropTypes.func.isRequired,
   races:     React.PropTypes.array.isRequired
};

// `bool` and `func` are abbreviated, but all other datatypes are spelled normally.
// If you add .isRequired to a propType, then you will get a console warning if that prop isn’t sent.
```

### Can are you set multiple data types for an expected prop?

Yes, you can allow an expected prop to have multiple data types. To do this, you can utilize `PropTypes.oneOfType()`, which will let you list each type that can be expected.

```jsx
import PropTypes from 'prop-types';

// In the following component, propOne can be
// of type string or boolean.
ExampleComponent.propTypes = {
  propOne: PropTypes.oneOfType([
    PropTypes.string,
    PropTypes.boolean
  ])
}
```