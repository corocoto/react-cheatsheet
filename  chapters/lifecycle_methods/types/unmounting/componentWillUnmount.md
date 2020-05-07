##`componentWillUnmount`

[EN]

`componentWillUnmount` gets called right before a component is removed from the DOM. If a component initiates any methods that require cleanup, then `componentWillUnmount` is place where you should put that cleanup.

> **Note:** Don't using `setState()` on the `componentWillUnmount()`, because component never been render again. After component's instance will be unmounting, it never been mounting again.

[RU]

`componentWillUnmount` будет вызван прямо перед удалением компонента из DOM. Если компонент инициирует какие-либо методы, требующие очистки, тогда `componentWillUnmount` - это место, куда вы должны полжить их.

> **Примечание:** Не используйте `setState()` в `componentWillUnmount()`, так как компонент никогда не рендерится повторно. После того, как экземпляр компонента будет размонтирован, он никогда не будет примонтирован снова.