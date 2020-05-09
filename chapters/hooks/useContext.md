## `useContext`

```jsx
const value = useContext(MyContext);
```

[EN]

Accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context. The current context value is determined by the `value` prop of the nearest `<MyContext.Provider>` above the calling component in the tree.

When the nearest `<MyContext.Provider>` above the component updates, this Hook will trigger a rerender with the latest context value passed to that MyContext provider. Even if an ancestor uses `React.memo` or `shouldComponentUpdate`, a rerender will still happen starting at the component itself using `useContext`.

Don’t forget that the argument to `useContext` must be the *context object itself*:

* **Correct**: `useContext(MyContext)`
* **Incorrect**: `useContext(MyContext.Consumer)`
* **Incorrect**: `useContext(MyContext.Provider)`

A component calling `useContext` will always re-render when the context value changes. If re-rendering the component is expensive, you can optimize it by using memoization.

>**Tip**
>
>If you’re familiar with the context API before Hooks, `useContext(MyContext)` is equivalent to `static contextType = MyContext` in a class, or to `<MyContext.Consumer>`.
>
>`useContext(MyContext)` only lets you read the context and subscribe to its changes. You still need a `<MyContext.Provider>` above in the tree to provide the value for this context.

Example:

```jsx
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light);

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );
}
```


[RU]

Принимает объект контекста (значение, возвращённое из `React.createContext`) и возвращает текущее значение контекста для этого контекста. Текущее значение контекста определяется пропом `value` ближайшего `<MyContext.Provider>` над вызывающим компонентом в дереве.

Когда ближайший `<MyContext.Provider>` над компонентом обновляется, этот хук вызовет повторную отрисовку с последним значением контекста, переданным этому провайдеру `MyContext`. Даже если родительский компонент использует `React.memo `или реализует `shouldComponentUpdate`, то повторная отрисовка будет выполняться, начиная c компонента, использующего `useContext`.

Запомните, аргумент для `useContext` должен быть *непосредственно сам объект контекста*:

* **Правильно**: `useContext(MyContext)`
* **Неправильно**: `useContext(MyContext.Consumer)`
* **Неправильно**: `useContext(MyContext.Provider)`

Компонент, вызывающий `useContext`, всегда будет переотрисовываться при изменении значения контекста. Если повторная отрисовка компонента затратна, вы можете оптимизировать его с помощью мемоизации.

>**Совет**
>
>Если вы были знакомы с API контекстов до появления хуков, то вызов `useContext(MyContext)` аналогичен выражению `static contextType = MyContext` в классе, либо компоненту `<MyContext.Consumer>`.
>
>`useContext(MyContext) `позволяет только читать контекст и подписываться на его изменения. Вам всё ещё нужен `<MyContext.Provider> ` выше в дереве, чтобы предоставить значение для этого контекста.

Пример:

```jsx
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light);

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      Я стилизован темой из контекста!
    </button>
  );
}
```