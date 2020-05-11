## React.Component vs React.PureComponent

[EN]

#### Introduction

We have `PureComponent` and `Component` on React. Let's take a look on both of them.

We can extends from `PureComponent` as like simple `Component`. And it has same methods and rules.

But `PureComponent` allows us to improve performance of component work.

Let's take a look why it's work so. We are need to move at `shouldComponentUpdate` lifecycle hook for that.

### Component

When you're work with simple component (`React.Component`), you're changing the state, and  re-render running, using `setState` function, accordingly.
In this case, re-render are running anyway.
You can using `shouldComponentUpdate`(and writing your own logic handling for new `state` and `props`) for controlling it.

On `React.Component` this method always returns `true`, if you don't write necessary checking only.
Because of this, any call the `setState`, or getting new `props`, will trigger a re-render.

This greatly affects on performance.

### PureComponent

Another situation, when you're working with `React.PureComponent`. It runs "non-deep" checking inside of `shouldComponentUpdate` (it's already implemented "out of the box"), and if data has been changed, so then update running.

This checking looks like this:
```jsx
shouldComponentUpdate(nextProps, nextState) {
    return !shallowEqual(nextProps, this.props) || 
           !shallowEqual(nextState, this.state);
}
```

[RU]

#### Введение

В React у нас есть `PureComponent ` и  `Component`.Давайте раасмотрим их оба.

Мы можем унаследоваться от `PureComponent` также просто, как от `Component`. И он имеет те же методы и правила.

Но `PureComponent` позволяет нам улучшить производительность работы компонента.

Давайте посмотрим почему же он так работает. Для этого нам нужно переместиться в метод жизненного цикла `shouldComponentUpdate`.

### Component

Когда вы работаете с простым компонентом (`React.Component`), вы меняете состояние и запускаете переотрисовку, используя функцию `setState`, соответственно.
В данном случае, переотрисовка запускается в любом случае.
Вы можете использовать `shouldComponentUpdate` (и писать вашу собственную догическую обработкудля новых `state` и `props`) для его контроля.

В `React.Component` этот метод всегда возвращает `true`, если только вы не пишите необходимую проверку.
Так как в этом случае, любой вызов `setState`, или получение новых `props`, будет вызвыать перерисовку.

Это прекрасное влияние на производительность.

### PureComponent

Другая ситуация, когда вы работаете с `React.PureComponent`. Он запускает "не глубокую" проверку внутри `shouldComponentUpdate` (он готов к выолнению прямо "из коробки"), и если данные были изменены, тогда запустится обновление.

Эта проверка выглядит как:

```jsx
shouldComponentUpdate(nextProps, nextState) {
    return !shallowEqual(nextProps, this.props) || 
           !shallowEqual(nextState, this.state);
}
```