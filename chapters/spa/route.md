## Route

[EN]

### Description

`<Route/>` component is main **React Router**'s building block. In that case if you're need to render an element 
depending from URLs `pathname`, you're need to using it exactly. 

### `path`

`<Route />` gets `path` as prop that describe some path and match with `location.pathname`.

```jsx
<Route path='/roster'/>
```

On example above, `<Route />` matches `location.pathname` that begins from `/roster`. When current `location.pathname` positively match with `path` prop, so component'll be render. And if we don't match it, so **Route** doesn't render anything.

```jsx
<Route path='/roster'/>
// when `location.pathname` is '/', prop `path` doesn't match
// When `location.pathname` is '/roster' or '/roster/2', prop `path` is match
// If `exact` prop set. Strong compare with '/roster' only be match, but not '/roster/2'
<Route exact path='/roster'/>
```

>**Note**: When we talk about path, **React Router** thinks about path only without domain. 
>
>It means that at address: `http://www.example.com/my-projects/one?extra=false`
>React Router will be see `/my-projects/one` only

#### Path mapping

When paths are mapping,`match` object creates. It contains next properties:

* `url` — matching part of the current  `location.pathname`;
* `path` — path at the **Route** component;
* `isExact` — `path` at the **Route** that equal `location.pathname`;
* `params` — object contains values from `path`.

#### What Route component's render are doing?

**Route** component has 3 `props` that describe how to render by matching `path` prop with `location.pathname`, and only one of props must be show at the **Route**:

* `component` — React component. When route is matching satisfy on the `path`, so it returns given component.
* `render` — function that must be return React element. It'll be call when matching satisfies on the `path`. `render` is so similar with `component`, but it using for inline-render and necessary `props` for element setting.
* `children` — `props` `children`'ll always be display whatever `path` matches or not,unlike previous two types.

```jsx
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>
```

You're need to use `component` or `render` on typical situations. `children` prop maybe used, but if `path` doesn't match with `location.pathname`, so do nothing is better way on this case.

Element that was be rendered by **Route** will pass some `props`. 
* `match` — matching object `path` with `location.pathname`;
* `location` 
* `history` - object that created route.

[RU]

### Описание

`<Route/>` компонент - это главный строительный блок **React Router**'а. В том случае, если вам нужно рендерить элемент в зависимости от `pathname` **URL**'ов, то следует использовать именно его.

### `path`

`<Route />` принимает `path` в виде prop, который описывает определенный путь и сопоставляется с `location.pathname`. 

```jsx
<Route path='/roster'/>
```

В примере выше, `<Route/>` сопоставляет `location.pathname`, который начинается с `/roster`. Когда текущий `location.pathname` сопоставляется положительно с prop `path`, то компонент будет отрендерен, а если мы не можем их сопоставить, то **Route** ничего не рендерит.

```jsx
<Route path='/roster'/>
// Когда location.pathname это '/', prop path не совпадает
// Когда location.pathname это '/roster' или '/roster/2', prop path совпадает
// Если установлен exact prop. Совпадает только строгое сравнение '/roster', но не
// '/roster/2'
<Route exact path='/roster'/>
```

>**Заметка**: Когда речь идет о пути, **React Router** думает только о пути без домена. 
>
>Это значит, что в адресе: `http://www.example.com/my-projects/one?extra=false`
>React Router будет видеть только `/my-projects/one`

#### Сопоставление пути

Когда пути сопоставляются, создается объект `match` который содержит свойства:

* `url` — сопоставляемая часть текущего `location.pathname`;
* `path` — путь в компоненте **Route**;
* `isExact` — `path` в **Route** === `location.pathname`;
* `params` — объект содержит значения из path.

#### Что делает рендер компонента Route?

У **Route** есть 3 `props`'a, которые описывают каким образом выполнить рендер, сопоставляя prop `path` с `location.pathname`, и только один из prop должен быть представлен в **Route**:

* `component` — React компонент. Когда роут удовлетворяется сопоставлению в `path`, то он возвращает переданный компонент.
* `render` — функция которая должна вернуть React элемент. Будет вызвана, когда удовлетворится сопоставление в `path`. `render` довольно похож на `component`, но используется для inline рендеринга и подстановки необходимых для элемента `props`.
* `children` — в отличие от предыдущих двух, `props` `children` будет всегда отображаться независимо от того сопоставляется ли `path` или нет.

```jsx
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>
```

В типичных ситуациях следует использовать `component` или `render`. `children` prop может быть использован, но лучше ничего не делать если `path` не совпадает с `location.pathname`.

Элементу, отрендеренному **Route**, будет передано несколько `props`. 
* `match` — объект сопоставления `path` с `location.pathname`;
* `location` 
* `history` -  объект, созданный самим роутом.