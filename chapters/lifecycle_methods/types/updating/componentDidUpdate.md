## `componentDidUpdate(prevProps, prevState, snapshot)`

[EN]

The last updating lifecycle method is `componentDidUpdate`.

When a component instance updates `componentDidUpdate` gets called after any rendered HTML has finished loading.

`componentDidUpdate` automatically gets passed three arguments: 
* `prevProps`
* `prevState`
* `snapshot` (optional)

`prevProps` and `prevState` are references to the component’s `props` and `state` before the current updating period began. You can compare them to the current `props` and `state`.

`componentDidUpdate` is usually used for interacting with things outside of the React environment, like the browser or APIs. It’s similar to `componentWillUpdate` in that way, except that it gets called after `render` instead of before.

[RU]

Последний обновляющий метод жизненного цикла - `componentDidUpdate`.

Когда экземпляр компонента обновляется, `componentDidUpdate` вызывается после завершения загрузки любого отрендеренного HTML.

`componentDidUpdate` автоматически получает три аргумента:
* `prevProps`
* `prevState`
* `snapshot` (необязательный)

`prevProps` и `prevState` являются ссылками на `props` и `state` компонента перед началом текущего периода обновления. Вы можете сравнить их с текущими значениями `props` и `state`.

`componentDidUpdate` обычно используется для взаимодействия с внешними объектами React-окружения, например такими, как браузер или различные API. Он похож на `componentWillUpdate` в этом плане, кроме той детали, что он будет вызван после метода `render` в отличие от `componentWillUpdate` (он будет вызван перед этим методом).
