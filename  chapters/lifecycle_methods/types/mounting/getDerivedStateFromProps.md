## `static getDerivedStateFromProps(props, state)`

It calls before calling `render` method as starter mounting as next updates. It must return an object for state updates or `null` for updates nothing.

This method is exist for rare cases when state depending on props changing.