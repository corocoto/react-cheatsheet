### Updating Lifecycle Methods

The first time that a component instance renders, it does not update. A component updates every time that it renders, starting with the second render.

There are five updating lifecycle methods:

* `componentWillReceiveProps`
* `shouldComponentUpdate`
* `componentWillUpdate`
* `render`
* `componentDidUpdate`

Whenever a component instance updates, it automatically calls all five of these methods, in order.