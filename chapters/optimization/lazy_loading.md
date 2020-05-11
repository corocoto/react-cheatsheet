## Lazy Loading (Ленивая загрузка)

[EN]

#### React.lazy
The `React.lazy` function lets you render a dynamic import as a regular component.

Before:

```js
import OtherComponent from './OtherComponent';
```

After:

```js
const OtherComponent = React.lazy(() => import('./OtherComponent'));
```

This will automatically load the bundle containing the **OtherComponent** when this component is first rendered.

`React.lazy` takes a function that must call a dynamic `import()`. This must return a `Promise` which resolves to a module with a default export containing a React component.

#### Delay

The lazy component should then be rendered inside a **Suspense** component, which allows us to show some fallback content (such as a loading indicator) while we’re waiting for the lazy component to load.

```jsx
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

The `fallback` prop accepts any React elements that you want to render while waiting for the component to load. You can place the **Suspense** component anywhere above the lazy component. You can even wrap multiple lazy components with a single **Suspense** component.

```jsx
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </div>
  );
}
```

#### Error boundaries

If the other module fails to load (for example, due to network failure), it will trigger an error. You can handle these errors to show a nice user experience and manage recovery with Error Boundaries. Once you’ve created your **Error Boundary**, you can use it anywhere above your lazy components to display an error state when there’s a network error.
```jsx
import React, { Suspense } from 'react';
import MyErrorBoundary from './MyErrorBoundary';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

const MyComponent = () => (
  <div>
    <MyErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </MyErrorBoundary>
  </div>
);
```

#### Route-based code splitting

Deciding where in your app to introduce code splitting can be a bit tricky. You want to make sure you choose places that will split bundles evenly, but won’t disrupt the user experience.

A good place to start is with routes. Most people on the web are used to page transitions taking some amount of time to load. You also tend to be re-rendering the entire page at once so your users are unlikely to be interacting with other elements on the page at the same time.

Here’s an example of how to setup route-based code splitting into your app using libraries like **React Router** with `React.lazy`.

```jsx
import React, { Suspense, lazy } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = lazy(() => import('./routes/Home'));
const About = lazy(() => import('./routes/About'));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading...</div>}>
      <Switch>
        <Route exact path="/" component={Home}/>
        <Route path="/about" component={About}/>
      </Switch>
    </Suspense>
  </Router>
);
```

#### Named Exports

`React.lazy` currently only supports default exports. If the module you want to import uses named exports, you can create an intermediate module that reexports it as the default. This ensures that *tree shaking* keeps working and that you don’t pull in unused components.

**ManyComponents.js**:

```js
export const MyComponent = /* ... */;
export const MyUnusedComponent = /* ... */;
```

**MyComponent.js**:

```js
export { MyComponent as default } from './ManyComponents.js;'

```

**MyApp.js**:
```js
import React, { lazy } from 'react';
const MyComponent = lazy(() => import('./MyComponent.js'));
```

[RU]

#### React.lazy

Функция `React.lazy` позволяет рендерить динамический импорт как обычный компонент.

До:

```js
import OtherComponent from './OtherComponent';
```

После:

```js
const OtherComponent = React.lazy(() => import('./OtherComponent'));
```

Она автоматически загрузит бандл, содержащий **OtherComponent**, когда этот компонент будет впервые отрендерен.

`React.lazy` принимает функцию, которая должна вызвать динамический `import()`. Результатом возвращённого `Promise` является модуль, который экспортирует по умолчанию React-компонент (`export default`).

#### Задержка

Компонент с ленивой загрузкой должен рендериться внутри компонента **Suspense**, который позволяет нам показать запасное содержимое (например, индикатор загрузки) пока происходит загрузка ленивого компонента.

```jsx
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Загрузка...</div>}>
        <OtherComponent />
      </Suspense>
    </div>
  );
}
```

Проп `fallback` принимает любой React-элемент, который вы хотите показать, пока происходит загрузка компонента. Компонент **Suspense** можно разместить в любом месте над ленивым компонентом. Кроме того, можно обернуть несколько ленивых компонентов одним компонентом **Suspense**.

```jsx
import React, { Suspense } from 'react';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

function MyComponent() {
  return (
    <div>
      <Suspense fallback={<div>Загрузка...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </div>
  );
}
```

#### Предохранители

Если какой-то модуль не загружается (например, из-за сбоя сети), это вызовет ошибку. Вы можете обрабатывать эти ошибки для улучшения пользовательского опыта с помощью предохранителей. После создания предохранителя, его можно использовать в любом месте над ленивыми компонентами для отображения состояния ошибки.

```jsx
import React, { Suspense } from 'react';
import MyErrorBoundary from './MyErrorBoundary';

const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

const MyComponent = () => (
  <div>
    <MyErrorBoundary>
      <Suspense fallback={<div>Загрузка...</div>}>
        <section>
          <OtherComponent />
          <AnotherComponent />
        </section>
      </Suspense>
    </MyErrorBoundary>
  </div>
);
```

#### Разделение кода на основе маршрутов

Решение о том, где в вашем приложении ввести разделение кода, может быть непростым. В идеале, следует выбрать такие места, чтобы код разделялся на бандлы примерно одного размера, тем самым поддерживая хороший пользовательский опыт.

Часто таким удобным местом оказываются маршруты. Большинство интернет-пользователей привыкли к задержкам во время переходов между страницами. Поэтому и вам может быть выгодно повторно отрендерить всю страницу целиком. Это не позволит пользователям взаимодействовать с другими элементами на странице, пока происходит обновление.

Вот пример того, как организовать разделение кода на основе маршрутов с помощью `React.lazy` и таких библиотек как **React Router**.

```jsx
import React, { Suspense, lazy } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

const Home = lazy(() => import('./routes/Home'));
const About = lazy(() => import('./routes/About'));

const App = () => (
  <Router>
    <Suspense fallback={<div>Загрузка...</div>}>
      <Switch>
        <Route exact path="/" component={Home}/>
        <Route path="/about" component={About}/>
      </Switch>
    </Suspense>
  </Router>
);
```

#### Именованный экспорт

`React.lazy` в настоящее время поддерживает только экспорт по умолчанию. Если модуль, который требуется импортировать, использует именованный экспорт, можно создать промежуточный модуль, который повторно экспортирует его как модуль по умолчанию. Это гарантирует работоспособность *tree shaking* — механизма устранения неиспользуемого кода.

**ManyComponents.js**:

```js
export const MyComponent = /* ... */;
export const MyUnusedComponent = /* ... */;
```

**MyComponent.js**:

```js
export { MyComponent as default } from './ManyComponents.js';
```

**MyApp.js**:

```js
import React, { lazy } from 'react';
const MyComponent = lazy(() => import('./MyComponent.js'));
```