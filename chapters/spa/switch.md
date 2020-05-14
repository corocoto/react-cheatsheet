## Switch

[EN]

**Route** component can be on any place on the router, but sometimes it needs to define what to render in the same place.
On this case, you're need using **Route** components grouping - it's `<Switch />`.

`<Switch />` is going via child components interactivity and only first to render, that match for `location.pathname`

Example:

```jsx
<Switch>
  <Route exact path='/' component={Home}/>
  {/* Оба /roster и /roster/:number начинаются с /roster */}
  <Route path='/roster' component={Roster}/>
  <Route path='/schedule' component={Schedule}/>
</Switch>
```


[RU]

Компонент **Route** может быть в любом месте в роутере, но иногда нужно определять, что рендерить в одно и тоже место. 
В таком случае следует использовать компонент группирования **Route**'ов — `<Switch/>`. 
`<Switch/>` итеративно проходит по дочерним компонентам и рендерит только первый, который подходит под `location.pathname`.

Пример: 

```jsx
<Switch>
  <Route exact path='/' component={Home}/>
  {/* Оба /roster и /roster/:number начинаются с /roster */}
  <Route path='/roster' component={Roster}/>
  <Route path='/schedule' component={Schedule}/>
</Switch>
```