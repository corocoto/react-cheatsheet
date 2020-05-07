## `shouldComponentUpdate(nextProps, nextState)`

[EN]

The second updating lifecycle method is called `shouldComponentUpdate`.

When a component updates, `shouldComponentUpdate` gets called after `componentWillReceiveProps`, but still before the rendering begins.

`shouldComponentUpdate` should return either `true` or `false`.

If `shouldComponentUpdate` returns `true`, then nothing noticeable happens. But if `shouldComponentUpdate` returns `false`, then the component will not update! None of the remaining lifecycle methods for that updating period will be called, including `render`.

The best way to use `shouldComponentUpdate` is to have it return `false` only under certain conditions. If those conditions are met, then your component will not update.

`shouldComponentUpdate` automatically receives two arguments: `nextProps` and `nextState`. It’s typical to compare `nextProps` and `nextState` to the current `this.props` and `this.state`, and use the results to decide what to do. 

[RU]

Второй обновляющий метод жизненного цикла называется `shouldComponentUpdate`.

Когда компонент обновляется, `shouldComponentUpdate` будет вызван после `componentWillReceiveProps`, но перед началом отрисовки.

`shouldComponentUpdate` должен возвращать либо `true`, либо `false`.

Если `shouldComponentUpdate` возращает `true`, тогда ничего заметного не происходит. Но если `shouldComponentUpdate` возвращает `false`, компонент не будет обновлен! Ни один из оставшихся методов жизненного цикла для этого обновляющего периода не будет вызван, включая `render`.

Наилучший путь использования `shouldComponentUpdate` - возвращать `false` только при определенных условиях. Если эти условия соблюдены, тогда ваш компонент не будет обновлен.

`shouldComponentUpdate` автоматически получает два аргумента: `nextProps` и `nextState`. Обычно сравнивают `nextProps` и` nextState` с текущими `this.props` и` this.state` и используют результаты для того, чтобы решить, что делать.
