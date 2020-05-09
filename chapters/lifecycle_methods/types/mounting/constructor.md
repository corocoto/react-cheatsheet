## `constructor()`

[EN]

React component's constructor calls before the component will be mounting. 

Needs calling `super(props)` at the constructor beginning. If it doesn't do, so `this.props` doesn't defined. It can be lead for bags.

Constructors on React using for 2 goals usually:
* Initialization initial state;
* Attaching event handlers for instance.

Don't use side effects or describes on a constructor. Use `componentDidMount` instead of this.

[RU]

Конструктор React-компонента вызывается перед тем, как компонент будет примонтирован.

Необходимо вызывать`super(props)` в начале конструктора. Если этого не сделать, `this.props` не будет определен. Это может привести к багам.

Конструкторы в React обычно используются для 2-ух целей:
* Инициализация начального состояния;
* Прикрепление обработчиков событий экземпляру.

Не используйте побочные эффекты или описания в конструкторе. Вместо этого используйте метод  `componentDidMount`.

