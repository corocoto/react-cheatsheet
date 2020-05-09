### React.Component vs React.PureComponent

#### Introduction

So on React, we have `PureComponent ` and  `Component`.Let looks both of them.

We can extends from `PureComponent` as like simple `Component`. And it has same methods and rules.

But, `PureComponent` allows us to improve performance of component work.

Let's look why it work so. And for that, we are need to move at `shouldComponentUpdate` lifecycle hook.

### Component

When you're work with simple component (`React.Component`), you're changing the state, and  re-render running, using `setState` function, accordingly.
In this case, re-render are running anyway.
You can using `shouldComponentUpdate`(and writing your own logic handling for new `state` and `props`) for controlling it.

On `React.Component` this method always returns `true`,  if you don't writes necessary checking only.
Because of this, any call the `setState`, or getting new `props`, will trigger a re-render.

This greatly affects on performance.

### PureComponent

Another situation, when you're working with `React.PureComponent`. It runs "non-deep" checking inside of `shouldComponentUpdate` (it's already implemented "out of the box"), and, if data has been changed, so then update running.

This checking looks like this:
```jsx
shouldComponentUpdate(nextProps, nextState) {
    return !shallowEqual(nextProps, this.props) || 
           !shallowEqual(nextState, this.state);
}
```