###`componentWillUnmount`

`componentWillUnmount` gets called right before a component is removed from the DOM. If a component initiates any methods that require cleanup, then `componentWillUnmount` is where you should put that cleanup.

> **Note:** Don't using `setState()` on the `componentWillUnmount()`, because component never been render again. After component's instance will be unmounting, it never been mounting again.