## `static getDerivedStateFromProps(props, state)`

[EN]

It calls before calling `render` method as starter mounting as next updates. It must return an object for state updates or `null` for updates nothing.

This method is exist for rare cases when state depending on props changing.

[RU]

Он вызвается перед вызовом метода `render`, в качестве начального монтирования при следующих обновлениях. Он должен возвращать объект для обновления состояния или `null` для его предотвращения.

Этот метод существует для редких случаев, когда состояние зависит от изменения пропсов.