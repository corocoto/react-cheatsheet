## `getSnapshotBeforeUpdate(prevProps, prevState)`

[EN]

`getSnapshotBeforeUpdate` calls directly before "fixation" stage (as example, before adding into DOM). It allows your component to take some information from the DOM (as example, scroll position) before it possible changing. Any value that return this lifecycle method, will gives to `componentDidUpdate()` as parameter.

[RU]

`getSnapshotBeforeUpdate` вызывается прямо перед этапом "фиксирования" (например, перед добавлением в DOM). Он позволяет вашему компоненту брать некоторую информацию из DOM (например, положение прокрутки) перед её возможным изменением. Любое значение, возвращаемое этим методом жизненного цикла, будет передано как параметр `componentDidUpdate()`.
