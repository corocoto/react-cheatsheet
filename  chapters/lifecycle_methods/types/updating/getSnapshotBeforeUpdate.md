## `getSnapshotBeforeUpdate(prevProps, prevState)`

`getSnapshotBeforeUpdate` calls directly before "fixation" stage (as example, before adding into DOM). It allows your component to take some information from the DOM (as example, scroll position) before it possible changing. Any value that return this lifecycle method, will gives to `componentDidUpdate()` as parameter.