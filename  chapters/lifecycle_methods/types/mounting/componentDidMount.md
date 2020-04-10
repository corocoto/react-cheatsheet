## `componentDidMount`

The final mounting lifecycle method is called `componentDidMount`.

When a component renders for the first time, `componentDidMount` gets called right after the HTML from `render` has finished loading.

`componentDidMount` gets used a lot!

If your React app uses AJAX to fetch initial data from an API, then `componentDidMount` is the place to make that `AJAX` call. More generally, `componentDidMount` is a good place to connect a React app to external applications, such as web APIs or JavaScript frameworks. `componentDidMount` is also the place to set timers using `setTimeout` or `setInterval`.