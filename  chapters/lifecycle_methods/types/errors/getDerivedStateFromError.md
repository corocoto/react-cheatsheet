## `static getDerivedStateFromError(error)`

[EN]

This lifecycle method calls after get an error from the child component. It gets an error as parameter and return value for updating state.

Example:

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Обновите состояние так, чтобы следующий рендер показал запасной интерфейс.
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      // Здесь можно рендерить запасной интерфейс
      return <h1>Что-то пошло не так.</h1>;
    }

    return this.props.children;
  }
}
```

>**Note:** `getDerivedStateFromError()` calls  at the render time. So there prohibited any side effects, but it can using on the `componentDidCatch()`.

[RU]

Этот метод жизненного цикла вызвается после получения ошибки от дочернего компонента. Он получает ошибку как параметр и возвращает значение для обновления состояния.

Пример:

```jsx
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Обновите состояние так, чтобы следующий рендер показал запасной интерфейс.
    return { hasError: true };
  }

  render() {
    if (this.state.hasError) {
      // Здесь можно рендерить запасной интерфейс
      return <h1>Что-то пошло не так.</h1>;
    }

    return this.props.children;
  }
}
```

>**Примечание:** `getDerivedStateFromError()` вызвается во время отрисовки. Поэтому здесь запрещены какие-либо побочные эффекты, но их можно использовать в `componentDidCatch()`.