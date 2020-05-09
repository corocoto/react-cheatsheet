## useEffect

[EN]

`useEffect` allows us to running side effects at functional component:

>**Note:** 
>If you know about class lifecycle methods, so `useEffect` hook present combine of `componentDidMount` and `componentDidUpdate` methods.
>So we can tell, that `useEffect` will running after render.

For more understandable, let look an example of class-based component and functional component, that will doing same things. Also we trying compare it, and finding differences between.

### Effects without reset

**Example 1:**

* **class-based component**:

```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  componentDidUpdate() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  render() {
    return (
      <div>
        <p>Вы нажали {this.state.count} раз</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Нажми на меня
        </button>
      </div>
    );
  }
}
```

>**Note:** We can see, that code are doubling (looks on code `componentDidMount` and `componentDidUpdate` methods). It's not good. But we have alternative.

* **functional component**:

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Вы нажали ${count} раз`;
  });

  return (
    <div>
      <p>Вы нажали {count} раз</p>
      <button onClick={() => setCount(count + 1)}>
        Нажми на меня
      </button>
    </div>
  );
}
```


It's looks like better. 
>**So what `useEffect` doing?**
>You're talking to React, that it's doing something after render, using this hook. 
>React is remember function (i.e. "effect"), that you send and run it after making all changes to the DOM.


### Effects with reset

We are looking side effects, that don't take reset early. However, there are cases, when reset is necessary. As example, we are may to need listener on something external data source. In this case, it's very important to run reset, so that there is no memory leaks.

Let's looks examples, that realised it:

* **class-based component**:

```jsx
class FriendStatus extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isOnline: null };
    this.handleStatusChange = this.handleStatusChange.bind(this);
  }

  componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  handleStatusChange(status) {
    this.setState({
      isOnline: status.isOnline
    });
  }

  render() {
    if (this.state.isOnline === null) {
      return 'Загрузка...';
    }
    return this.state.isOnline ? 'В сети' : 'Не в сети';
  }
}
```

>At React class, usually, set listener at `componentDidMount` and reset it at `componentWillUnmount`.

* **functional component**

Let's looks, how this component be view, if it will be writes using hooks.

```jsx
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Указываем, как сбросить этот эффект:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Загрузка...';
  }
  return isOnline ? 'В сети' : 'Не в сети';
}
```

>**Note:** If your effect is return a function, so React run it only, when the time comes to reset the effect.

### Advice: performance optimization by skipping effects

In some cases a reset or running effect by every render may to call a problem with performance. At class-based components, we can resolve it to using additional compare `prevProps` or `prevState` inside `componentDidUpdate`:

```jsx
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `Вы нажали ${this.state.count} раз`;
  }
}
```

But it'll be running inside of class-based component, but not functional component.
But functional component has same thing. It contains inside of `useEffect` hook. 
You can do so, that React missed call effect, if certain values ​​remain unchanged between subsequent renders.

For doing it, pass the array to `useEffect` as second optional argument.

```jsx
useEffect(() => {
  document.title = `Вы нажали ${count} раз`;
}, [count]); // Перезапускать эффект только если count поменялся
```

>**Note**: In this example, we pass `[count]` as second argument. 
>
>What is it mean? 
>It's mean, that if `count` will equal `5` and our component re-rendered with same value (`count` = `5`). React will compare `[5]` from previous render and `[5]` from next render. As, all array elements remain without changing, so React misses this effect. It's an optimization of this process.
>
>When our variable `count` updates to `6` on the next render, React compare the array elements `[5]` from previous render and the array elements `[6]` from next render. In this case, React runs  our effect, because `5 !== 6`.
>
>If you have some elements in array, React will running pur effect, on the time, when one of the elements will be change.

It's also work for effect with reset step:

```jsx
useEffect(() => {
  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
  return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
  };
}, [props.friend.id]); // Повторно подписаться, только если props.friend.id изменился
```

[RU]

`useEffect` позволяет нам запускать побочные эффекты в функциональном компоненте:

>**Примечание:** 
>Если вы знакомы с классовыми методами жизненного цикла, тогда хук `useEffect` представляет комбинацию методов `componentDidMount` и `componentDidUpdate`.
>Так мы можем сказать, что `useEffect` будет запускаться после отрисовки.

Для большего понимания, давайте рассмотрим пример классового и функционального компонентов, которые будут выполять то же самое. Также мы попытаемся сравнить их и найти отличия.

### Эффекты без сброса

**Пример 1:**

* **Классовый компонент**:

```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  componentDidUpdate() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  render() {
    return (
      <div>
        <p>Вы нажали {this.state.count} раз</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Нажми на меня
        </button>
      </div>
    );
  }
}
```

>**Примечание:** Мы можем видеть, что код дублируется (посмотрите на код в методах `componentDidMount` и `componentDidUpdate`). Это не хорошо. Но у нас есть альтернатива.

* **Функциональный компонент**:

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Вы нажали ${count} раз`;
  });

  return (
    <div>
      <p>Вы нажали {count} раз</p>
      <button onClick={() => setCount(count + 1)}>
        Нажми на меня
      </button>
    </div>
  );
}
```

Этот пример выглядит лучше.

>**Так что же делает `useEffect`?**
>Вы говорите React'у, что он будет делать что-то после отрисовки, используя этот хук. 
>React запоминает функцию (т.е. "эффект"), который вы отправили и запускает его после всех соврешенных изменений в DOM.


### Эффекты со сбросом

Ранее мы рассмотрели подочные эффекты, которые не требуют сброса. Однако, есть случаи, когда сброс необходим. Например, у нас может быть потребность в налчиии слушателя на какой-то внешний источник данных. В этом случае очень важно запустить сброс, чтобы не было утечек памяти.

Давайте рассмотрим примеры, в которых это реализовано:

* **Классовый компонент**:

```jsx
class FriendStatus extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isOnline: null };
    this.handleStatusChange = this.handleStatusChange.bind(this);
  }

  componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  handleStatusChange(status) {
    this.setState({
      isOnline: status.isOnline
    });
  }

  render() {
    if (this.state.isOnline === null) {
      return 'Загрузка...';
    }
    return this.state.isOnline ? 'В сети' : 'Не в сети';
  }
}
```

>В React классе, обычно, устнавливается слушатель в методе `componentDidMount`, а сбрасывается в `componentWillUnmount`.

* **Функциональный компонент**

Давайте посмотрим, как этот компонент выглядит, если он будет написан с использованием хуков.

```jsx
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Указываем, как сбросить этот эффект:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Загрузка...';
  }
  return isOnline ? 'В сети' : 'Не в сети';
}
```

>**Примечание:** Если ваш эффект возвращает функцию, тогда React запустит только её, когда придет время сброса того самого эффекта.

### Совет: оптимизация производительности за счет пропуска эффектов

В некоторых случаях сброс или запуск эффекта при каждой отрисовке может вызвать проблемы с производительностью. В классовых компонентах, мы можем решить их, используя дополнительное сравнение `prevProps` или `prevState` внутри метода `componentDidUpdate`:

```jsx
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `Вы нажали ${this.state.count} раз`;
  }
}
```

Но это будет запускаться внутри классового компонента, но никак не в функциональном.
Но функциональный компонент обладает схожей вещью. Она содержится внутри хука `useEffect`. 
Вы можете сделать так, что React пропустит вызов эффекта, если некоторые значения остались нетронутыми между последующими отрисовками.

Для того, чтобы сделать это, передайте массив в `useEffect` в качестве второго необязательного аргумента.

```jsx
useEffect(() => {
  document.title = `Вы нажали ${count} раз`;
}, [count]); // Перезапускать эффект только если count поменялся
```

>**Примечание**: В этом примере мы передаем `[count]` в качестве второго аргумента. 
>
>Что это значит? 
>Это значит, что если `count` будет равен `5` и у нашего компонента до этого произошла перерисовка с тем же значением (`count` = `5`). React будет сравнивать значение `[5]` из предыдущей отрисовки и значение`[5]` из следующей. Так как все элементы массива остались без изменений, React пропустит этот эффект. Это является оптимизацией данного процесса.
>
>Когда наша переменная `count` обновится до `6` при следующей отрисовке, React сравнит элементы массива `[5]` из предыдущей отрисовки и `[6]` из следующей. В данном случае, React запустит наш эффект, потому что `5 !== 6`.
>
>Если у вас есть некоторые элементы в массиве, React будет запускать pur-эффект в то время, когда один из элементов будет изменен.

Это также работает для эффекта с шагом сброса:

```jsx
useEffect(() => {
  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
  return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
  };
}, [props.friend.id]); // Повторно подписаться, только если props.friend.id изменился
```