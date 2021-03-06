## `render()`

[EN]

`render` is one mandatory method on the class-based component.

Function `render()` must be *clear*. It means that it doesn't change a component's state, always return same result, doesn't interact directly with the browser.

`render` belongs to two categories: 
* mounting lifecycle methods;
* updating lifecycle methods. 

>**Note:** `render()` doesn't call, if `shouldComponentUpdate()` return `false`.

[RU]

`render` - это единственный обязательный метод в классовом компоненте.

Функция `render()` должна быть *чистой*. Это подразумевает, что она не должна изменять состояние компонента, всегда возвращать тот же результат, не взаимодействовать напрямую с браузером.

`render` принадлежит двум категориям: 
* монтирующие методы жизненного цикла;
* обновляющие методы жизненного цикла.

>**Примечание:** `render()` не вызывается, если `shouldComponentUpdate()` возвращает `false`.