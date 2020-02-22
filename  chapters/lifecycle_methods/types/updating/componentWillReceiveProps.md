### `componentWillReceiveProps`

The first updating lifecycle method is called `componentWillReceiveProps`.

When a component instance updates, `componentWillReceiveProps` gets called before the rendering begins.

As one might expect, `componentWillReceiveProps` only gets called if the component will receive props:
```
// componentWillReceiveProps will get called here:
ReactDOM.render(
  <Example prop="myVal" />,
  document.getElementById('app')
);

// componentWillReceiveProps will NOT get called here:
ReactDOM.render(
  <Example />,
  document.getElementById('app')
);
```

`componentWillReceiveProps` automatically gets passed one argument: an object called `nextProps`. `nextProps` is a preview of the upcoming `props` object that the component is about to receive.