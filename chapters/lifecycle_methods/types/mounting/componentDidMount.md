## `componentDidMount()`

[EN]

The final mounting lifecycle method is called `componentDidMount`.

When a component renders for the first time, `componentDidMount` gets called right after the HTML from `render` has finished loading.

`componentDidMount` gets used a lot!

If your React app uses AJAX to fetch initial data from an API, then `componentDidMount` is the place to make that AJAX call. More generally, `componentDidMount` is a good place to connect a React app to external applications, such as web APIs or JavaScript frameworks. `componentDidMount` is also the place to set timers using `setTimeout` or `setInterval`.

[RU]

Финальный монтирующий метод жизненного цикла называется `componentDidMount`.

Когда отрисовка компонента происходит в первый раз, `componentDidMount` вызывается сразу после завершения загрузки HTML из` render`.

`componentDidMount` используется во множестве случаев!

Если ваше React-приложение использует AJAX для получения первоначальных данных из API, тогда `componentDidMount` - это место, предназначенное для вызова AJAX. Обобщенно, `componentDidMount` является хорошим местом для соединения React-приложения со сторонними приложениями, таких как веб API или JavaScript-фреймворки. `componentDidMount` также является местом для установки таймеров, используя для этого `setTimeout` или `setInterval`.
