## `componentDidCatch(error, info)`

This lifecycle method calls after occurrence an error from the child-component. It gets 2 parameters:

1. `error` - intercepted error;
2. `info` - object with `componentStack` key containing information about component that the error has occurred

>**Note:** It runs at stage of "fixation" time, so there may using side effects.