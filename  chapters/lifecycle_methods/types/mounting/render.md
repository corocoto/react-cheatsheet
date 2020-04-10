## `render`

`render` is one mandatory method on the class-based component.

Function `render()` must be *clear*. It means that it doesn't change a component's state, always return same result, doesn't interact directly with the browser.

`render` belongs to two categories: 
* mounting lifecycle methods
* updating lifecycle methods. 

>**Note:** `render()` doesn't call, if `shouldComponentUpdate()` return `false`.