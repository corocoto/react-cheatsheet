## Updating Lifecycle Methods

The first time that a component instance renders, it does not update. A component updates every time that it renders, starting with the second render.

There are five updating lifecycle methods:

* [`static getDerivedStateFromProps`](../mounting/getDerivedStateFromProps.md)
* [`shouldComponentUpdate`](shouldComponentUpdate.md)
* [`render`](../mounting/render.md)
* [`getSnapshotBeforeUpdate`](getSnapshotBeforeUpdate.md)
* [`componentDidUpdate`](componentDidUpdate.md)

Whenever a component instance updates, it automatically calls all of these methods, in order.