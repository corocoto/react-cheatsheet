### React.memo

```jsx
const MyComponent = React.memo(function MyComponent(props) {
  /* рендер с использованием пропсов */
});
```

`React.memo` is the HOC (Higher Order Component). It's looks like on the `React.PureComponent`, but using for functional components.

If your functional component always to rendered same result for the same `props`, so you can to wrap it in the `React.memo` call for better performance in some cases, memorizing the result. 

It means, that React will using the last render result avoiding replay rendering.

`React.memo` only affect on `props` changes. If the functional component wraps into `React.memo` and uses one of the hooks `useState` or `useContext`, then it be repeatedly render, when context or state changing.

By default, it compares nested objects superficially. If you wanna to control comparing, you can pass your compare function as second argument.

```jsx
function MyComponent(props) {
  /* рендер с использованием пропсов */
}
function areEqual(prevProps, nextProps) {
  /*
  возвращает true, если nextProps рендерит
  тот же результат что и prevProps,
  иначе возвращает false
  */
}
export default React.memo(MyComponent, areEqual);
```

>**Note:**  function `areEqual` returns `true` if `props` are equal, and `false` value if `props` don't equal, `shouldComponent()` method for class-based components unlike.
