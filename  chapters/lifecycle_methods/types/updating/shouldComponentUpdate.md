### `shouldComponentUpdate`

The second updating lifecycle method is called `shouldComponentUpdate`.

When a component updates, `shouldComponentUpdate` gets called after `componentWillReceiveProps`, but still before the rendering begins.

`shouldComponentUpdate` should return either `true` or `false`.

If `shouldComponentUpdate` returns `true`, then nothing noticeable happens. But if `shouldComponentUpdate` returns `false`, then the component will not update! None of the remaining lifecycle methods for that updating period will be called, including `render`.

The best way to use `shouldComponentUpdate` is to have it return `false` only under certain conditions. If those conditions are met, then your component will not update.

`shouldComponentUpdate` automatically receives two arguments: `nextProps` and `nextState`. It’s typical to compare `nextProps` and `nextState` to the current `this.props` and `this.state`, and use the results to decide what to do. 