## Updating Lifecycle Methods (Обновляющие методы жизненного цикла)

[EN]

The first time that a component instance renders, it does not update. A component updates every time that it renders, starting with the second render.

There are five updating lifecycle methods:

* [`static getDerivedStateFromProps`](../mounting/getDerivedStateFromProps.md)
* [`shouldComponentUpdate`](shouldComponentUpdate.md)
* [`render`](../mounting/render.md)
* [`getSnapshotBeforeUpdate`](getSnapshotBeforeUpdate.md)
* [`componentDidUpdate`](componentDidUpdate.md)

Whenever a component instance updates, it automatically calls all of these methods, in order.

[RU]

В момент первой отрисовки экземпляра компонента обновления не произойдет. Компонент обновляется каждый раз, как он отрисовывается, начиная со второй отрисовки.


Здесь находятся пять обновляющих методов жизненного цикла:

* [`static getDerivedStateFromProps`](../mounting/getDerivedStateFromProps.md)
* [`shouldComponentUpdate`](shouldComponentUpdate.md)
* [`render`](../mounting/render.md)
* [`getSnapshotBeforeUpdate`](getSnapshotBeforeUpdate.md)
* [`componentDidUpdate`](componentDidUpdate.md)

Всякий раз, когда экземпляр компонента обновляется, он автоматически вызывает все эти методы по порядку.
