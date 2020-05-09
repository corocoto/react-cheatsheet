## `componentDidCatch(error, info)`

[EN]

This lifecycle method calls after occurrence an error from the child-component. It gets 2 parameters:

1. `error` - intercepted error;
2. `info` - object with `componentStack` key containing information about component that the error has occurred

>**Note:** It runs at stage of "fixation" time, so there may using side effects.

[RU]

Этот метод жизненного цикла вызывается после возникновения ошибки у компонента-потомка. Он получает два параметра:

1. `error` - перехваченная ошибка;
2. `info` - объект с ключом `componentStack`, содержащий информацию о компоненте, в котором произошла ошибка.

>**Примечание:** Он вызывается во время этапа "фиксации", поэтому здесь можно использовать побочные эффекты.