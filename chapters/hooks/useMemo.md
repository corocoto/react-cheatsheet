## `useMemo`

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

[EN]

Returns a [memoized](https://en.wikipedia.org/wiki/Memoization) value.

Pass a "create" function and an array of dependencies. `useMemo` will only recompute the memoized value when one of the dependencies has changed. This optimization helps to avoid expensive calculations on every render.

>Remember that the function passed to `useMemo` runs during rendering. Don’t do anything there that you wouldn’t normally do while rendering. For example, side effects belong in `useEffect`, not `useMemo`.

If no array is provided, a new value will be computed on every render.

You may rely on `useMemo` as a performance optimization, not as a semantic guarantee. In the future, React may choose to "forget" some previously memoized values and recalculate them on next render, e.g. to free memory for offscreen components.

>**Note**
>
>The array of dependencies is not passed as arguments to the function. Conceptually, though, that’s what they represent: every value referenced inside the function should also appear in the dependencies array.

[RU]

Возвращает [мемоизированное](https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D0%BC%D0%BE%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F) значение.

Передайте "создающую" функцию и массив зависимостей. `useMemo` будет повторно вычислять мемоизированное значение только тогда, когда значение какой-либо из зависимостей изменилось. Эта оптимизация помогает избежать дорогостоящих вычислений при каждой отрисовке.

>Помните, что функция, переданная `useMemo`, запускается во время отрисовки. Не делайте там ничего, что вы обычно не делаете во время рендеринга. Например, побочные эффекты принадлежат `useEffect`, а не `useMemo`.

Если массив не был передан, новое значение будет вычисляться при каждом рендере.

Вы можете использовать `useMemo` как оптимизацию производительности, а не как семантическую гарантию. В будущем React может решить "забыть" некоторые ранее мемоизированные значения и пересчитать их при следующем рендере, например, чтобы освободить память для компонентов вне области видимости экрана.

>**Примечание**
>
>Массив зависимостей не передаётся в качестве аргументов функции. Концептуально, однако, это то, что они представляют: каждое значение, на которое ссылается функция, должно также появиться в массиве зависимостей.